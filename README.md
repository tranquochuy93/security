### Password
  - RULE:
    - hash algorithm là one-way-function
    - hash algorithms là slow-hash => giảm khả năng tính toán của  brute-force attach, dictionary attach
    - Thêm pepper và salt vào pasword: hash(pepper + salt + password)
  - hash algorithm là one-way-function, tức là không thể suy ngược trực tiếp ra password nếu có hash_value.
    => brute-force attach, dictionary attach -> điểm chung là ta cần thử và đoán password nhiều lần cho tới khi đúng cái cần tìm.
  - Thêm salt: hash(salt + password)
    - salt là random cho từng user và được lưu ở db
    => tăng thời gian tính toán ra password
  ``` html
  id |          hash_md5                |    salt         |
---------------------------------------------------------
1  | 0510210d4b370165658bdc0d0b005244 | 7nWZLcCK0vsPzIM |
  ```
  - Thêm Pepper: hash(pepper + salt + password)
    - dùng chung cho tất cả user
    - k lưu trong db, lưu pepper ở application hoặc ở một service khác
  - bcrypt 
    - slow-hash algorithm (mất 100ms để tính toán ra chuỗi hash)
