# Ứng Dụng Của PCA, Monte Carlo Và Naive Bayes Vào Các Bài Toán Thực Tế
## Thành viên thực hiện

### **Giảng viên hướng dẫn**
- **TS. Dương Ngọc Hảo**

### **Nhóm sinh viên thực hiện**
- **Trần Thái Hoà**
- **Võ Hoàng An**
- **Nguyễn Thị Huyền Trang**

### **Môn học**
- DS101.N11 - Thống kê và xác suất chuyên sâu
## Giới thiệu

Dự án này nghiên cứu và áp dụng **ba phương pháp thống kê và học máy quan trọng** vào các bài toán thực tế:

- **Monte Carlo Simulation**: Dự đoán tổng số tiền hoa hồng phải trả cho nhân viên trong năm tiếp theo.
- **Gaussian Naive Bayes**: Phân loại khách hàng tiềm năng dựa trên độ tuổi và mức lương.
- **Principal Component Analysis (PCA)**: Xác định các yếu tố ảnh hưởng đến tỷ lệ khách hàng rời đi trong doanh nghiệp.

Mỗi phương pháp đều được thử nghiệm với **bộ dữ liệu thực tế**, thực hiện tiền xử lý, xây dựng mô hình và đánh giá kết quả.

---

## Mục tiêu của dự án

- **Monte Carlo Simulation**: 
  - Dự đoán tổng số tiền hoa hồng cần chi trả trong năm tiếp theo bằng cách tạo ra một bộ dữ liệu mới từ dữ liệu bán hàng năm trước.
  - Áp dụng mô hình mô phỏng Monte Carlo để đánh giá rủi ro và tính toán dự báo.

- **Gaussian Naive Bayes**: 
  - Xây dựng mô hình phân loại khách hàng có khả năng mua hàng dựa trên độ tuổi và mức lương.
  - Đánh giá hiệu suất mô hình trên tập dữ liệu thực tế.

- **PCA - Principal Component Analysis**: 
  - Xác định các yếu tố chính ảnh hưởng đến tỷ lệ khách hàng rời đi.
  - Giảm số chiều dữ liệu trước khi xây dựng mô hình hồi quy logistic.

---

## Bộ dữ liệu

1️⃣ **Monte Carlo Simulation**
- **Nguồn dữ liệu**: Bộ dữ liệu bán hàng năm trước.
- **Các thuộc tính chính**:
  - `Sales Rep`: Nhân viên bán hàng.
  - `Sales Target`: Doanh số kỳ vọng.
  - `Actual Sales`: Doanh số thực tế.
  - `Commision Rate`: Tỷ lệ hoa hồng.
  - `Commision Amount`: Tổng hoa hồng.

📌 **Kết quả dự báo**: Tổng tiền hoa hồng trung bình **2.85 triệu USD**, độ lệch chuẩn **103K USD**.

2️⃣ **Gaussian Naive Bayes**
- **Nguồn dữ liệu**: [Social_Network_Ads](https://www.kaggle.com/datasets/rakeshrau/social-network-ads)
- **Số lượng dữ liệu**: **400 bản ghi**.
- **Các thuộc tính chính**:
  - `Age`: Tuổi khách hàng.
  - `EstimatedSalary`: Mức lương ước tính.
  - `Purchased`: 1 - Mua, 0 - Không mua.

📌 **Hiệu suất mô hình**:
| Độ đo  | Giá trị |
|--------|--------|
| Accuracy | **91.25%** |
| F1-score | **88.87%** |

3️⃣ **PCA - Principal Component Analysis**
- **Nguồn dữ liệu**: [BankChurners Dataset](https://www.kaggle.com/datasets/sakshigoyal7/credit-card-customers)
- **Số lượng dữ liệu**: **10,000 bản ghi**.
- **Các thuộc tính chính**:
  - `Customer_Age`, `Gender`, `Total_Trans_Amt`, `Total_Trans_Ct`, `Avg_Utilization_Ratio`, ...

📌 **Kết quả**:
| Số lượng PCs | Accuracy | F1-score |
|-------------|----------|---------|
| Không dùng PCA | 89% | 0.94 |
| 2 PCs | 84% | 0.91 |
| 3 PCs | **88%** | **0.93** |

🔹 **Kết luận**: **2 - 3 PCs đủ để mô hình hoạt động hiệu quả, giúp giảm số chiều dữ liệu và tăng hiệu suất tính toán.**

---

## Phương pháp thực hiện

### 🔹 **Monte Carlo Simulation**
1. **Định luật giới hạn trung tâm (Central Limit Theorem)**: Xác định giá trị trung bình và độ lệch chuẩn của dữ liệu gốc.
2. **Mô phỏng Monte Carlo**:
   - Thiết lập mô hình dự đoán.
   - Xác định phân phối xác suất của các biến độc lập.
   - Chạy mô phỏng 1000 lần với 500 nhân viên bán hàng.
3. **Dự báo tổng số tiền hoa hồng cho năm tiếp theo**.

### 🔹 **Gaussian Naive Bayes**
1. **Tiền xử lý dữ liệu**:
   - Chia dữ liệu thành tập **train (80%)** và **test (20%)**.
   - Chuẩn hóa dữ liệu.
2. **Huấn luyện mô hình**:
   - Sử dụng thuật toán **Naive Bayes** để dự đoán khả năng mua hàng.
3. **Đánh giá mô hình**:
   - **Confusion Matrix**, **Accuracy**, **F1-score**.

### 🔹 **Principal Component Analysis (PCA)**
1. **Áp dụng PCA**:
   - Giảm số chiều dữ liệu xuống **2 - 3 PCs**.
2. **Hồi quy Logistic**:
   - Dự đoán tỷ lệ khách hàng rời đi dựa trên các PCs.
3. **Đánh giá mô hình**:
   - So sánh độ chính xác khi dùng PCA và không dùng PCA.

---

## Kết quả và đánh giá mô hình

- **Monte Carlo Simulation**:
  - Dự báo chính xác tổng số tiền hoa hồng cho doanh nghiệp.
  - Phân tích rủi ro dựa trên các biến ngẫu nhiên.

- **Gaussian Naive Bayes**:
  - **Mô hình đạt độ chính xác 91.25%** → phù hợp để phân loại khách hàng tiềm năng.
  - Nhược điểm: Giả định các thuộc tính đầu vào độc lập, có thể không thực tế.

- **PCA**:
  - Giảm số chiều dữ liệu **mà không mất nhiều thông tin**.
  - **Dùng 2 - 3 PCs vẫn giữ được accuracy > 84%.**

📌 **Mô hình hiệu quả nhất**: **Xử lý dữ liệu bằng PCA trước khi hồi quy logistic giúp giảm độ phức tạp của mô hình mà vẫn giữ được độ chính xác cao.**

---

## Hướng phát triển trong tương lai

- **Monte Carlo**:
  - Tăng số lần mô phỏng để có kết quả chính xác hơn.
  - Áp dụng vào các bài toán tài chính khác như dự báo doanh thu.

- **Naive Bayes**:
  - Kết hợp với các thuật toán khác như Random Forest để cải thiện kết quả.
  - Thử nghiệm với nhiều tập dữ liệu lớn hơn.

- **PCA**:
  - Sử dụng các phương pháp tối ưu hơn như **Varimax Rotation** để tăng khả năng diễn giải dữ liệu.
  - Áp dụng vào bài toán giảm chiều dữ liệu lớn hơn.
