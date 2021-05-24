# Công cụ hỗ trợ phân tích, truy tìm nguyên nhân gốc

## Hiện trạng

- Hệ thống của VTNet nói chung đang được giám sát rời rạc, tách ra làm nhiều cụm có chung tính chất để phân tải giám sát
- Chưa có một địa chỉ cụ thể để kiểm tra giám sát, đã có Prom-Manager đưa ra được thông tin tổng hợp của tất cả các cụm Prometheus đang giám sát.
Tuy nhiên, để tra cứu đến việc giám sát từng service trong cùng 1 instance thì chưa đưa ra được thông tin.
- Trên DCIM hiện tại có chăng chỉ đưa ra được thông tin là đã được giám sát hay chưa, chưa có thông tin để cross-check
- Chưa có công cụ để tổng hợp các thông tin về giám sát, logging, alert có liên quan khi có sự cố xảy ra

## Ý tưởng giải pháp

- DCIM/Prom-Manager hỗ trợ thêm việc quản lí thông tin về Logging, giám sát, alertmanager (có thể trace từ Prometheus nhưng mất thêm cost nhất định)
- Việc đưa thông tin quản lí này phải được đáp ứng đầy đủ khi bàn giao VHKT
- Xây dựng công cụ tổng hợp, phân tích dựa trên module DCIM-topology có sẵn

## Tính ứng dụng

- Để đảm bảo các hệ thống phải có giám sát, việc chỉ khai báo đã giám sát trên DCIM là chưa đủ
- Việc khai báo thông tin cụm giám sát sẽ hỗ trợ cho việc cross-check khi nhận bàn giao VHKT, BO không phải ghi nhớ từng instance thuộc cụm giám sát nào
- Hỗ trợ việc sử lý sự cố, có 1 view về metrics, logging và các cảnh bảo liên quan, để đưa ra quyết định dựa vào các thông tin đó
- Đưa ra được model về lịch sử tập cảnh báo => đưa ra dự đoán trước nếu việc tương tự xảy ra trong tương lai
