# K85KTP-BAITAPMOT
# TRUONG VAN QUYEN K225480106083
## BÀI TẬP MÔN: An toàn và bảo mật thông tin
## BÀI TẬP 1:
## TÌM HIỂU CÁC PHƯƠNG PHÁP MÃ HOÁ CỔ ĐIỂN
1. Caesar
2. Affine
3. Hoán vị
4. Vigenère
5. Playfair
## Với mỗi phương pháp, hãy tìm hiểu:

1. Tên gọi
2. Thuật toán mã hoá, thuật toán giải mã
3. Không gian khóa
4. Cách phá mã (mà không cần khoá)
5. Cài đặt thuật toán mã hoá và giải mã bằng code C++ và bằng html+css+javascript
# Cách làm
# 1. Mã Caesar
1.  Mã Caesar (Caesar Cipher)
- Tên gọi: Caesar Cipher
- Nguyên lý: Dịch chuyển các chữ cái trong bảng chữ cái đi một số vị trí nhất định.
2. Công thức: Thuật toán
 - Mã hóa: C = (P + k) mod 26 Giải mã: P = (C - k) mod 26
3. Không gian khóa: 26 khả năng (k = 0..25). (k = 0 cho bản rõ)
4. Cách phá mã (không cần khóa)
-  Brute force thử 26 khả năng.
-  Phân tích tần suất chữ cái (văn bản dài -> dịch sao cho chữ phổ biến nhất khớp 'E').
5.  C++ (mã hoá + giải mã
## ẢNH.
1.  ảnh python
<img width="1920" height="1020" alt="Screenshot 2025-09-27 173839" src="https://github.com/user-attachments/assets/28ad7419-5caa-40d4-9abd-d35a404af28c" />
<img width="1920" height="1020" alt="Screenshot 2025-09-27 175113" src="https://github.com/user-attachments/assets/2ffffafe-3c45-4685-8c97-2cf1e2caa78e" />
<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/af67814b-246e-4be6-8891-bbe10783ed09" />
2.  ảnh C++
<img width="1920" height="1020" alt="image" src="https://github.com/user-attachments/assets/5f0087f9-7e8e-4ba1-9bd7-8d21bf5413b9" />

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6d79edb9-5818-4486-a1f1-dc4be49d6838" />


# 2. Affine cipher (Mã Affine)
1. Tên gọi
-  Affine cipher (mã tuyến tính modulo).
2.  Thuật toán
-  Khoá: cặp (a, b) với 0 ≤ b ≤ 25 và a sao cho gcd(a,26)=1 (tức a nghịch đảo modulo 26).
-  Mã hoá: C = (a * p + b) mod 26.
-  Giải mã: tìm a^{-1} (nghịch đảo modulo 26), p = a^{-1} * (C - b) mod 26.
3. Không gian khoá
-  Số a có gcd(a,26)=1 có 12 giá trị (1,3,5,7,9,11,15,17,19,21,23,25). b có 26 giá trị. Tổng 12*26 = 312 khả năng.
4.  Cách phá
-  Brute-force: thử 312 khả năng.
-  Phân tích tần suất / known-plaintext: do là ánh xạ affine, nếu biết hai cặp plaintext–cipher tương ứng có thể giải hệ để ra a,b. Cặp letter nhất định dễ suy.
Kỹ thuật tận dụng tần suất.
5.  C++ (console)
   1.  ảnh c++
  <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/bd24c8f8-0e94-45d3-9d8b-17fdacacfbc5" />
   2.  ảnh python

   <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/6d79edb9-5818-4486-a1f1-dc4be49d6838" />
# 3. Columnar transposition (Hoán vị / Chuyển vị cột)
1.  "Hoán vị" có thể là nhiều dạng; mình trình bày columnar transposition (mã chuyển vị cột) — phổ biến và dễ hiểu.
-  Tên gọi
-  Columnar Transposition (Chuyển vị theo cột) — sắp xếp cột theo khoá (chuỗi chữ cái) rồi đọc theo cột.
2.  Thuật toán
-  Khoá: một chuỗi không trùng ký tự (hoặc ta dùng thứ tự các chữ số) xác định thứ tự cột, ví dụ ZEBRA → thứ tự các chữ cái theo thứ tự bảng: A(5), B(3), E(2), R(4), Z(1) => dùng thứ tự số (1..n).
-  Mã hoá:
-  Viết plaintext (bỏ ký tự không phải chữ nếu muốn) vào ma trận hàng theo n cột (n = độ dài key), điền thêm ký tự đệm nếu cần.
-  Đọc cột theo thứ tự tăng dần của chữ cái khoá, nối lại thành cipher.
3.  Giải mã:
-  Sắp xếp các cột về vị trí ban đầu và đọc theo hàng.
-  Không gian khoá
-  Với khoá độ dài n, không gian là n! (hoán vị).
4.  Cách phá
-  Brute-force: thử các hoán vị của cột (n!); với n nhỏ (<=8) có thể thử.
-  Phân tích cấu trúc: dùng độ dài khối, bigram/trigram tần suất để đánh giá bản giải.
-  Kỹ thuật hill-climbing / simulated annealing cho ma trận hoán vị lớn.
5.  C++ (columnar) — ví dụ đơn giản
 1.  ảnh c++
 <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/846ba880-b2b9-45a1-9710-1465015eefd8" />
2.  python
 <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e28e3ac7-0bd7-43c4-a6c2-4c7903b595d5" />

# 4. Vigenère cipher
1.  Tên gọi
-  Vigenère cipher (mã thay thế polyalphabetic với khoá chữ).
2.  Thuật toán
-  Khoá: chuỗi ký tự K = k0 k1 ... k_{m-1}.
-  Mã hoá: với plaintext P = p0 p1 ..., mỗi ký tự pi bị dịch bởi ki = K[i mod m]: Ci = (pi + ki) mod 26 (với ki là số 0..25).
3.  Giải mã: pi = (Ci - ki) mod 26.
-  Không gian khoá
-  Với khoá độ dài m, không gian 26^m. Nếu khoá biến đổi theo từ/dãy thực tế thì lớn.
4.  Cách phá (không cần khoá)
-  Kasiski examination: tìm các khoảng cách giữa các cụm lặp (repeated sequences) để ước lượng độ dài khoá m.
-  Friedman test (index of coincidence): ước lượng m.
-  Khi biết m, tách cipher thành m dãy và thực hiện phân tích tần suất (như Caesar) cho từng dãy để xác định dịch tương ứng => suy khoá.
-  Brute-force nếu m nhỏ.
5.  C++ (ví dụ)
    1.   ảnh c++
 <img width="1920" height="1080" alt="Screenshot 2025-09-27 220343" src="https://github.com/user-attachments/assets/724212d6-869e-40eb-a9db-7cabe6f327a8" />
    2. python
 <img width="1390" height="959" alt="image" src="https://github.com/user-attachments/assets/4cf76ff1-4ce0-4f72-aebb-61578f6241d9" />

        
# 5. Playfair cipher
1.  Tên gọi
-  Playfair cipher (mã thay thế theo cặp, dùng bảng 5×5).
2.  Nguyên tắc chính
-  Sử dụng bảng 5×5 chứa 25 chữ cái (thường ghép I và J hoặc loại Q tùy chuẩn).
-  Mã hoá theo digraphs (cặp chữ): chia plaintext thành cặp (AA→AXA hoặc chèn X giữa giống chữ lặp), nếu còn lẻ thì thêm X.
-  Với mỗi cặp (A,B) tìm vị trí trong bảng:
3.  Nếu cùng hàng: thay bằng chữ bên phải (vòng vòng) — hàng giữ nguyên.
-  Nếu cùng cột: thay bằng chữ phía dưới (vòng).
-  Nếu khác hàng và cột: thay bằng hai chữ ở góc của hình chữ nhật (giữ hàng, đổi cột).
-  Giải mã đảo ngược các quy tắc (bên trái / phía trên thay vì phải/dưới).
-  Không gian khoá
-  Khóa là sắp xếp 25 chữ cái (không kể chữ bị ghép), tức khoảng 25! khả năng lý thuyết (rất lớn). Nếu khoá là một từ khóa ngắn dùng để điền bảng thì không gian nhỏ hơn nhưng vẫn lớn.
4.  Cách phá
-  Phân tích digraph: phân tích tần suất digram, kiểm tra các đặc trưng (ví dụ chữ trùng, X chèn)
-  Brute-force rất khó; thực tế sử dụng heuristics / hill-climbing trên không gian hoán vị bảng.
-  Known-plaintext có thể làm lộ bảng.
5.  C++ (ví dụ chuẩn: I/J ghép)
    1.   ảnh c++
 <img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/0157c171-cb4b-4bf5-b615-7918ae426505" />
    2.   python
   <img width="1604" height="1016" alt="image" src="https://github.com/user-attachments/assets/4a783d06-e109-4ea6-9d57-a59110a380b9" />
