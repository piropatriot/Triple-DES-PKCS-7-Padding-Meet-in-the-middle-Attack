
# 1.Triple DES
## Sơ lược
### AES
- DES(Data Encryption Standard)  là thuật toán mã hóa theo khối, nó xử lý từng khối thông tin của bản rõ có độ dài xác định là 64 bit. Trước khi đi vào 16 chu trình chính, khối dữ liệu cần bảo mật sẽ được tách ra thành từng khối 64 bit, và từng khối 64 bit này sẽ lần lượt được đưa vào 16 vòng mã hóa DES để thực hiện. Tiền thân của nó là Lucifer, một thuật toán do IBM phát triển. Cuối năm 1976, DES được chọn làm chuẩn mã hóa dữ liệu của nước Mỹ, sau đó được sử dụng rộng rãi trên toàn thế giới. DES cùng với mã hóa bất đối xứng đã mở ra một thời kỳ mới trong ngành mã hóa thông tin. Trước DES, viện nghiên cứu và sử dụng mã hóa dữ liệu chỉ giới hạn trong chính phủ và quân đội.
- ![](https://hackmd.io/_uploads/HkZHKZiYn.png)
- Cách thức hoạt động:
  - Key mật mã: DES sử dụng phương pháp mật mã khối, điều này có nghĩa là mỗi khối dữ liệu sẽ được áp dụng bởi một key mật mã và thuật toán. DES sẽ nhóm plain text (văn bản thuần túy) thành các khối 64 bit. Bằng cách kết hợp và hoán vị các khối của plain text sẽ được chuyển đổi thành Ciphertext (văn bản đã mã hóa).
  - Key mật mã: DES sử dụng phương pháp mật mã khối, điều này có nghĩa là mỗi khối dữ liệu sẽ được áp dụng bởi một key mật mã và thuật toán. DES sẽ nhóm plain text (văn bản thuần túy) thành các khối 64 bit. Bằng cách kết hợp và hoán vị các khối của plain text sẽ được chuyển đổi thành Ciphertext (văn bản đã mã hóa).
  - Phím 64 bit: Thực tế cho thấy mặc dù DES sử dụng key 64 bit nhưng có 8 bit trong số đó đã được dùng để kiểm tra chẵn lẻ. Vì lẽ đó là key hiệu dụng chỉ có 56 bit.
  - Thay thế và hoán vị: Đây là hai quy trình mà Ciphertext phải trải qua trong quá trình mã hóa.
  - Khả năng tương thích ngược (tương thích với phiên bản cũ): Trong một số trường hợp DES cũng cung cấp khả năng này.
- Với sự phát triển của khoa hoạc kỹ thuật, DES không được xem là an toàn do độ dài 56 bít của khóa là quá nhỏ, nhiều kết quả nghiên cứu, phân tích cho thấy việc mã hóa có thể bị phá khóa, thuật toán 3DES  có tính an toàn cao hơn và được sử dụng trong thực tế nhiều hơn. Năm 2002 tiêu chuẩn mã hóa tiên tiến AES (Advanced Encryption Standard) được đề xuất thay thế cho tiêu chuẩn DES và 3DES, song vẫn có nhiều lĩnh vực áp dụng sử dụng DES, 3DES sau này.
- Có nhiều khóa được xem là khóa yếu trong thuật toán DES, đó là các khóa dễ có khả năng bị đối tượng phá khóa do một số bits của khóa lặp lại và dễ dự đoán trước. Việc sử dụng khóa yếu có thể làm giảm tính bảo mật của DES, do đó tránh sử dụng các khóa yếu này. Cụ thể là:
  - 01010101 01010101
  - FEFEFEFE FEFEFEFE
  - E0E0E0E0 F1F1F1F1
  - 1F1F1F1F 0E0E0E0E
### 3DES
- Tiêu chuẩn mã hóa dữ liệu Triple DES là một tiêu chuẩn mật mã dựa trên mật mã khối đối xứng sử dụng các khóa có độ dài cố định với ba lần truyền thuật toán DES. Là một sơ đồ mật mã đối xứng, việc triển khai DES dựa trên cùng một khóa bí mật được chia sẻ giữa người gửi và người nhận.
- Thuật toán 3DES sử dụng một nhóm khóa bao gồm 03 khóa DES là K1, K2 và K3, mỗi khóa có giá trị 56 bít.
- ![](https://hackmd.io/_uploads/rJtDXZsF3.png)
- Mã hóa: ``Ciphertext = Ek3(Dk2(Ek1(Plaintext))) `` Trước tiên, thực hiện mã hóa DES với khóa K1, tiếp tục giải mã DES với khóa K2 và cuối cùng mã hóa DES với khóa K3
- Giải mã: ``Plaintext = Dk1(Ek2(Dk3(Ciphertext)))`` Giải mã bằng khóa K1; mã hóa bằng khóa K2 và giải mã kết quả bằng K3.
- 3DES mã hóa một khối dữ liệu có giá trị 64 bít (bản rõ) thành một khối dữ liệu mới có giá trị 64 bít (bản mã). Các tiêu chuẩn chỉ ra phương thức lựa chọn nhóm khóa (K1, K2, K3) như sau:
  - K1, K2, K3 là các khóa độc lập : phương thức mã hóa mạnh nhất với 168 bit khóa độc lập (168=3x56)
  - K1, K2 là hai khóa độc lập và  K3 = K1 : ít bảo mật hơn với 112 bít khóa ( 2x56=112 bit)
  - K1=K2=K3 : tương đương với việc mã hóa DES 1 lần với 56 bít khóa.
- Mỗi khóa DES thông thường được lưu trữ và truyền đi trong 8 byte, vì vậy một nhóm khóa yêu cầu 8 hoặc 16, 24 byte cho việc lưu trữ khóa.
# 2.PKCS#7 Padding
## Sơ lược
- PKCS#7 Padding (Public-Key Cryptography Standards #7 Padding) là một thuật toán đệm (padding) được sử dụng trong quá trình mã hóa đối xứng, như block cipher, để đảm bảo rằng dữ liệu đầu vào có độ dài tương thích với kích thước khối (block size) của thuật toán mã hóa
- PKCS#7 Padding hoạt động bằng cách thêm vào cuối dữ liệu một số byte để đạt được độ dài mong muốn. Giá trị của các byte được thêm vào sẽ là số byte cần thêm. Ví dụ, nếu block size của thuật toán là 8 byte và dữ liệu cần được mã hóa chỉ có 5 byte, thì 3 byte có giá trị là 03 sẽ được thêm vào cuối.
- PKCS#7 Padding được sử dụng rộng rãi trong nhiều giao thức và tiêu chuẩn bảo mật, chẳng hạn như SSL/TLS, CMS (Cryptographic Message Syntax), và PKCS#5/PKCS#12 (Password-Based Encryption Standard). Nó giúp đảm bảo rằng dữ liệu được mã hóa luôn có độ dài bằng một bội số của kích thước khối, đồng thời cung cấp tính toàn vẹn và khả năng phục hồi đúng dữ liệu gốc sau khi giải mã.
```python=
def pkcs7(a, b):
    pad_size = b - len(a) % b
    pad = bytes([pad_size] * pad_size)
    pad_a = a + pad
    return pad_a
text = b"PKSC#7 Pad"
size = 8     
cc = pkcs7(text, size)
print(cc)

#if pad_size là 6 thì pad sẽ là b'\x06\x06\x06\x06\x06\x06'
#out b'PKSC#7 Pad\x06\x06\x06\x06\x06\x06'
```

# 3.Meet in the middle Attack
## Sơ lược
- Tấn công Meet-in-the-Middle (MITM) là một loại tấn công phân tích mật mã trong đó kẻ tấn công cần một số loại đánh đổi không gian hoặc thời gian để hỗ trợ cuộc tấn công. Nỗ lực MITM có thể làm giảm mức độ khó khăn cần thiết để thực hiện cuộc tấn công ở trạng thái ban đầu.
- Double DES sử dụng hai ví dụ về mật mã DES để mã hóa và hai đơn vị mật mã DES ngược để giải mã. Mỗi đơn vị mật mã DES cần nhiều khóa để mã hóa giúp tăng cường kích thước của khóa (112 bit) giúp khóa an toàn hơn. Nhưng trong DES kép có thể bị phá hủy bởi cuộc tấn công văn bản rõ ràng được gọi là tấn công meet-in-the-Middle.
- Cho một văn bản thuần P và hai khóa mã hóa K1 và K2, bản mã C được tạo ra dưới dạng ``  C = E1(k1, E2(k2, P))`` giải mã cần thiết rằng các khóa được sử dụng theo thứ tự ngược lại ``P = D2(k2, D1(k1, C))``
- Cuộc tấn công trung gian sử dụng một cách tiếp cận hiệu quả hơn. Bằng cách giải mã C với k2, người ta có được sự tương đương sau:
-`` C = Ek2(Ek1,P) 
Dk2 = Dk2(Ek2(Ek1,P))
Dk2 = Ek1, P
``
- Kẻ tấn công có thể tính (Ek1, P) cho tất cả các giá trị của k 1 và (Dk2, C) cho tất cả các giá trị có thể có của k2, với tổng số 2|k1| + 2|k2| (hoặc 2|k1|+1, nếu k1 và k2 có cùng kích thước hoạt động. Nếu kết quả từ bất kỳ hoạt động (Ek1, P) nào khớp với kết quả từ các phép toán (Dk2, C), cặp k1 và k2 có thể là khóa chính xác. Khóa có khả năng chính xác này được gọi là khóa ứng viên. Kẻ tấn công có thể xác định khóa ứng cử viên nào là chính xác bằng cách kiểm tra nó bằng bộ kiểm tra thứ hai của bản rõ và bản mã.
- ![](https://hackmd.io/_uploads/S1fyM6jtn.png)
- ![](https://hackmd.io/_uploads/Sy81STiYh.png)

- Meet-in-the-Middle với 2DES
  - Subcipher1 = Ef1(kf1,P) và lưu từng Subcipher cùng với từng kf1 trong tập hợp A
  - Subcipher2 = Db2(kb2, C) và lưu từng Subcipher2 cùng với tương ứng kb2 trong tập hợp B.
  - Đối với mỗi dự đoán có thể có về một trạng thái trung gian s giữa Subcipher1 và Subcipher2
    - Subcipher1 = Db1(kb1, s) và cho mỗi trận đấu giữa điều này Subcipher1 và cho bộ A, lưu kb1 và kf1 trong một bộ mới T
    - Subcipher2 = Ef2(kf2, s) và cho mỗi trận đấu giữa điều này Subcipher2 và bộ B, kiểm tra có khớp với T , nếu kết quả khớp với dữ liệu đã biết, ta đã tìm thấy khóa gốc và khóa mã hóa.
- Phương pháp "meet-in-the-middle" tận dụng tính chất của hàm băm ngược để giảm số lượng khóa cần thử. Với 2 DES, quá trình này yêu cầu tính toán khoảng 2^(56+56) = 2^112 lượt thử, một con số khá lớn và khó khăn để thực hiện trong thực tế. Như vậy meet in the middle attack đã làm cho 2DES không còn đáng tin cậy để áp dụng cho bảo mật thông tin. Thay vào đó là 3DES hay AES,...
> Nguồn tham khảo
- https://en.wikipedia.org/wiki/Triple_DES
- https://en.wikipedia.org/wiki/PKCS_7
- https://en.wikipedia.org/wiki/Meet-in-the-middle_attack
___
