# Bài 9: Truyền dữ liệu trực tiếp vào bộ nhớ (DMA)

## Yêu cầu
- Hiểu cơ chế **DMA** và cách DMA giải phóng CPU khỏi các tác vụ truyền dữ liệu.
- Cấu hình **DMA** để truyền dữ liệu từ **ADC** vào bộ nhớ **RAM**.
- Khi quá trình truyền hoàn tất:
  - Một ngắt (interrupt) được kích hoạt để xử lý dữ liệu.
- Hiển thị dữ liệu đã được truyền thành công lên **terminal (UART)**.

## Gợi ý triển khai
1. Khởi tạo và cấu hình **ADC** để liên tục lấy mẫu.
2. Cấu hình **DMA**:
   - Chọn kênh DMA phù hợp với ADC1.
   - Địa chỉ nguồn: thanh ghi dữ liệu ADC.
   - Địa chỉ đích: mảng lưu dữ liệu trong RAM.
   - Kích thước, chế độ circular (nếu cần).
3. Kích hoạt ngắt DMA Transfer Complete (TC).
4. Trong hàm xử lý ngắt DMA:
   - Đọc dữ liệu từ buffer RAM.
   - Gửi kết quả qua UART hiển thị lên terminal.

---

📌 Bài này giúp luyện tập kết hợp **ADC + DMA + Interrupt + UART** để làm việc hiệu quả hơn mà không cần CPU copy dữ liệu thủ công.
