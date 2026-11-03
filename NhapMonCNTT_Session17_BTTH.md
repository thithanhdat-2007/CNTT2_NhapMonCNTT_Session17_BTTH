# BÀI TẬP TỔNG HỢP SESSION 16: TRÌNH DUYỆT – CÔNG CỤ LÀM VIỆC CỦA DEVELOPER

## PHẦN A – THIẾT LẬP PROFILE VÀ BOOKMARK CHUẨN DEV

### Câu 1: Điều gì xảy ra khi đăng nhập song song GitHub cá nhân và GitHub công ty trên cùng 1 Profile?
Trong cùng một **Browser Profile**, tất cả các tab đều dùng chung một vùng lưu trữ dữ liệu cục bộ, bao gồm **Cookies**, **Session** và **Local Storage**. Trang web `github.com` nhận diện người dùng đang đăng nhập thông qua Cookie phiên làm việc (`session`) gắn với tên miền đó.

Nếu em tiếp tục dùng chung 1 Profile duy nhất để đăng nhập cả hai tài khoản:
1. **Xung đột phiên đăng nhập (Session Overwrite):** Khi đang mở GitHub cá nhân ở Tab 1 mà mở Tab 2 để đăng nhập vào GitHub công ty (hoặc buộc phải đăng xuất tài khoản cá nhân để vào tài khoản công ty), Cookie xác thực mới sẽ ghi đè lên Cookie cũ. Khi quay lại Tab 1 và tải lại trang, Tab 1 cũng sẽ tự động chuyển thành tài khoản GitHub công ty.
2. **Rủi ro thao tác nhầm quyền truy cập:** Việc phải đăng nhập – đăng xuất liên tục hoặc bị đổi phiên ngầm giữa các tab rất dễ khiến em bình luận, tạo Issue, mở Pull Request dự án nội bộ bằng tài khoản cá nhân, hoặc lưu nhầm mật khẩu công ty vào kho mật khẩu cá nhân.

### Câu 2: Áp dụng Mô hình 3 Profile chuẩn Developer vào bối cảnh công ty

| Profile | Tên đặt | Mục đích sử dụng |
| :--- | :--- | :--- |
| **1** | `Personal` | Phục vụ nhu cầu cá nhân: duy trì đăng nhập GitHub cá nhân, mạng xã hội, email riêng, giải trí và ngân hàng. Tách biệt hoàn toàn dữ liệu riêng tư khỏi công việc công ty. |
| **2** | `Company_Work` | Môi trường làm việc chính thức tại công ty: đăng nhập cố định GitHub công ty, email công ty, công cụ quản lý dự án (Jira, Slack/Teams), lưu trữ hệ thống Bookmark tài liệu kỹ thuật và cài đặt các Extension thuộc nhóm Dev Suite / Productivity Suite. |
| **3** | `Sandbox/Test` | Môi trường kiểm thử độc lập: chuyên dùng để truy cập trang nội bộ `test.internal-tool.com`, đăng nhập các tài khoản test nhiều phân quyền, thoải mái xóa Cache/Cookies và thực hành debug trên DevTools mà không làm văng phiên đăng nhập ở `Company_Work`. |

### Câu 3: Thiết kế cấu trúc Bookmark gồm 3 thư mục chuẩn phân loại
Trên thanh dấu trang (Bookmark Bar) của Profile `Company_Work`, em thiết kế 3 thư mục theo đúng nhóm chức năng:

1. **Thư mục 1: `01_Company_Project` (Dự án & Quản lý công việc nội bộ)**
   - Trang 1: Kho mã nguồn GitHub công ty (`https://github.com/company-org/internal-tool`).
   - Trang 2: Trang môi trường kiểm thử nội bộ (`https://test.internal-tool.com`) hoặc bảng quản lý tác vụ Jira/Trello của nhóm.

2. **Thư mục 2: `02_Tech_Docs` (Tài liệu kỹ thuật & Tra cứu chuẩn)**
   - Trang 1: MDN Web Docs (`https://developer.mozilla.org`) – Tra cứu tài liệu chuẩn về HTML, CSS, JavaScript và các mã trạng thái HTTP.
   - Trang 2: Trang tài liệu đặc tả API nội bộ của công ty (Swagger / Postman API Docs) để đối chiếu cấu trúc dữ liệu.

3. **Thư mục 3: `03_Dev_Utilities` (Công cụ tiện ích hỗ trợ lập trình)**
   - Trang 1: Công cụ kiểm tra biểu thức chính quy và dữ liệu (`https://regex101.com`).
   - Trang 2: Công cụ kiểm tra độ tương thích CSS/HTML trên các trình duyệt (`https://caniuse.com`).

### Câu 4: Cho đồng nghiệp mượn máy 5 phút để tra cứu nhanh
- **Chế độ/Profile lựa chọn:** Mở **Guest Mode (Chế độ Khách)** trên trình duyệt Chrome (hoặc sử dụng **Incognito Mode – Chế độ Ẩn danh** nếu chỉ cần tra cứu một liên kết nhanh).
- **Giải thích ngắn gọn:** **Guest Mode** tạo ra một cửa sổ trình duyệt trống hoàn toàn, không chỉ cách ly toàn bộ Cookies/Session đang đăng nhập mà còn ẩn sạch thanh Bookmark, lịch sử tìm kiếm, gợi ý tự động điền (Autofill) và mật khẩu đã lưu của cả 3 Profile trên máy. Ngay khi đồng nghiệp đóng cửa sổ Guest, mọi dấu vết tra cứu trong 5 phút đó cũng tự động được xóa sạch.

## PHẦN B – CHỌN ĐÚNG EXTENSION HỖ TRỢ

### Câu 1: Lựa chọn nhóm Extension và tên tiện ích xử lý API JSON thô
- **Nhóm Extension cần chọn:** Nhóm **Dev Suite** (Bộ tiện ích chuyên dụng hỗ trợ kỹ thuật cho Developer).
- **Tên tiện ích cụ thể:** **JSON Viewer** (hoặc **JSON Formatter**). Tiện ích này tự động phân tích chuỗi JSON thô khó đọc thành cấu trúc cây phân cấp có thụt lề rõ ràng, tô màu cú pháp (syntax highlighting) theo kiểu dữ liệu và cho phép thu gọn hoặc mở rộng từng nhánh đối tượng.
- **Giải thích vì sao 2 nhóm còn lại không phù hợp:**
  1. **Productivity Suite (Nhóm quản lý & tăng năng suất):** Tập trung vào việc ghi chú, quản lý thời gian, dịch thuật hoặc gom nhóm tab (ví dụ: Notion Web Clipper, Todoist, OneTab). Các tiện ích này không có chức năng phân tích cú pháp (parse) và định dạng dữ liệu kỹ thuật trả về từ API.
  2. **Security Suite (Nhóm bảo mật & quyền riêng tư):** Tập trung vào việc chặn quảng cáo/script độc hại và quản lý mật khẩu (ví dụ: uBlock Origin, Bitwarden). Nhóm này phục vụ bảo vệ an toàn thông tin chứ không hỗ trợ hiển thị hay đọc cấu trúc JSON.

### Câu 2: Cấu hình quyền Site Access sau khi cài đặt
- **Lựa chọn cấu hình:** Chọn **`On click`** (Chỉ kích hoạt khi người dùng nhấp chuột vào biểu tượng Extension) hoặc chỉ cấp quyền trên tên miền API cụ thể (`On specific sites`), tuyệt đối không để mặc định `On all sites`.
- **Giải thích theo quy tắc quản trị Extensions:**
  1. **Đảm bảo an toàn bảo mật (Nguyên tắc đặc quyền tối thiểu):** Nếu để `On all sites`, tiện ích có quyền đọc và chỉnh sửa dữ liệu trên mọi trang web em truy cập (kể cả trang email nội bộ, GitHub công ty hay tài khoản ngân hàng). Chuyển sang `On click` giúp giới hạn phạm vi hoạt động của tiện ích đúng vào thời điểm em mở tab chứa link JSON.
  2. **Tối ưu hiệu suất trình duyệt (Tiết kiệm RAM và CPU):** Tiện ích đặt ở chế độ `On all sites` sẽ luôn chạy ngầm và kiểm tra cấu trúc nội dung trên tất cả các tab đang mở. Đặt `On click` giúp trình duyệt nhẹ hơn, không tiêu tốn tài nguyên máy cho những trang web thông thường.

## PHẦN C – PHÂN TÍCH LUỒNG HTTP REQUEST

### Câu 1: Thứ tự 4 giai đoạn xử lý trong luồng HTTP Request Flow khi truy cập `test.internal-tool.com`
Khi gõ `test.internal-tool.com` vào thanh địa chỉ và nhấn Enter, trình duyệt thực hiện tuần tự 4 giai đoạn sau:
1. **Giai đoạn 1 – Phân giải tên miền (DNS Lookup):** Trình duyệt truy vấn máy chủ DNS để chuyển đổi tên miền dễ nhớ `test.internal-tool.com` thành địa chỉ IP xác định của máy chủ (ví dụ `192.168.1.50` hoặc IP Server nội bộ).
2. **Giai đoạn 2 – Gửi yêu cầu HTTP (Send HTTP Request):** Sau khi kết nối tới địa chỉ IP của Server, trình duyệt đóng gói và gửi bản tin **HTTP Request** lên Server (bao gồm phương thức `GET`, đường dẫn trang, Request Headers và Cookies phiên làm việc).
3. **Giai đoạn 3 – Xử lý tại Server và trả về phản hồi (Server Processing & HTTP Response):** Server tiếp nhận yêu cầu, thực thi logic kiểm tra/truy vấn dữ liệu, sau đó gửi trả về cho trình duyệt bản tin **HTTP Response** chứa **HTTP Status Code** (như `200 OK`, `404`, `500`), Response Headers và dữ liệu nguồn (HTML, CSS, JS, JSON).
4. **Giai đoạn 4 – Trình duyệt dựng và hiển thị trang (Browser Rendering):** Trình duyệt phân tích mã HTML để dựng cây DOM, kết hợp với CSS (CSSOM), thực thi JavaScript, tải các tài nguyên đi kèm và hiển thị giao diện hoàn chỉnh lên màn hình.

### Câu 2: Bảng so sánh 2 mã trạng thái HTTP và hướng debug ban đầu

| Mã trạng thái | Ý nghĩa | Lỗi nằm ở đâu? | Hướng debug ban đầu |
| :--- | :--- | :--- | :--- |
| **404 Not Found** | Máy chủ vẫn phản hồi nhưng không tìm thấy tài nguyên hoặc đường dẫn (URL/Endpoint) mà trình duyệt yêu cầu. | Thường nằm ở phía **Client (Frontend)** gọi sai đường dẫn URL, sai tên endpoint, hoặc tài nguyên đã bị di chuyển/xóa trên Server. | Mở tab **Network**, kiểm tra kỹ **Request URL** và **Request Method** (`GET`/`POST`) xem có bị gõ sai chính tả đường dẫn API, thiếu tiền tố đường dẫn hoặc truyền sai ID tài nguyên so với tài liệu API không. |
| **500 Internal Server Error** | Máy chủ gặp sự cố hoặc lỗi ngoại lệ nội bộ trong lúc xử lý yêu cầu nên không thể trả về kết quả hợp lệ. | Nằm ở phía **Server (Backend / Database)** (ví dụ: lỗi logic code trên Server, lỗi kết nối cơ sở dữ liệu, hoặc Server chưa bắt ngoại lệ khi dữ liệu gửi lên bất thường). | Mở tab **Network**, kiểm tra mục **Payload** (xem dữ liệu Frontend gửi lên có bị rỗng hoặc sai kiểu dữ liệu không) và đọc mục **Response / Preview** để lấy thông báo lỗi chi tiết, sau đó gửi thông tin request này cho Dev Backend kiểm tra Server Log. |

### Câu 3: Lựa chọn Tab trong 4 Tab DevTools để xem mã trạng thái HTTP
- **Tab cần mở:** Mở tab **Network**. Trong bảng danh sách các yêu cầu mạng, cột **Status** hiển thị trực tiếp mã trạng thái HTTP (`200`, `304`, `404`, `500`...) của trang chính cũng như từng file CSS, ảnh và API.
- **Lý do không chọn 3 Tab còn lại:**
  1. **Tab Elements:** Chỉ dùng để quan sát và chỉnh sửa trực tiếp cấu trúc cây HTML (DOM) cùng các thuộc tính định dạng CSS (Styles, Box Model), không lưu thông tin giao tiếp mạng.
  2. **Tab Console:** Dùng để theo dõi nhật ký chương trình (`console.log`), bắt lỗi cú pháp/thực thi JavaScript và gõ lệnh JS tương tác; không cung cấp bảng thống kê đầy đủ mã trạng thái HTTP và Headers của mọi gói tin.
  3. **Tab Application:** Dùng để quản lý các kho lưu trữ dữ liệu phía trình duyệt (Cookies, Local Storage, Session Storage, Cache), không theo dõi luồng gửi – nhận HTTP Request/Response.

## PHẦN D – CHẨN ĐOÁN CACHE VÀ COOKIES

### Câu 1: Chẩn đoán và khắc phục hiện tượng sửa CSS nhưng nhấn F5 vẫn thấy giao diện cũ
- **Chẩn đoán nguyên nhân:** Hiện tượng này xảy ra do cơ chế **Browser Cache (Bộ nhớ đệm trình duyệt)**. Ở những lần truy cập trước, trình duyệt đã tải file CSS cũ của trang `test.internal-tool.com` và lưu vào bộ nhớ đệm trên máy để tối ưu tốc độ tải trang. Khi chỉ nhấn F5 thông thường, trình duyệt lấy lại file CSS cũ từ trong Cache ra hiển thị chứ chưa tải bản CSS mới nhất từ Server về.
- **Thao tác khắc phục chính xác:**
  1. Thực hiện **Hard Reload (Tải lại cứng bỏ qua bộ nhớ đệm)** bằng tổ hợp phím **`Ctrl + Shift + R`** (hoặc **`Ctrl + F5`** trên Windows, **`Cmd + Shift + R`** trên macOS).
  2. Hoặc mở DevTools (**F12**), vào tab **Network**, tích chọn ô **`Disable cache`**, hoặc nhấp chuột phải vào nút **Reload** trên thanh địa chỉ trình duyệt và chọn **`Empty Cache and Hard Reload`**.

### Câu 2: Rủi ro bảo mật khi Cookie `session_id` không bật cờ `HttpOnly`
- **Rủi ro bảo mật cụ thể:** Cờ `HttpOnly` có nhiệm vụ cấm các đoạn mã JavaScript chạy trên trang web can thiệp vào Cookie. Khi cột `HttpOnly` của `session_id` bị bỏ trống (không có dấu tích), bất kỳ đoạn mã JavaScript nào chạy trên trang cũng có thể đọc và lấy được giá trị `session_id` thông qua thuộc tính `document.cookie`.
- **Tên loại tấn công có thể xảy ra:** Tấn công **XSS (Cross-Site Scripting)** kết hợp **Session Hijacking (Chiếm đoạt phiên đăng nhập)**. Nếu trang web có lỗ hổng cho phép kẻ tấn công chèn mã JavaScript độc hại, đoạn mã đó sẽ âm thầm đọc `session_id` của người dùng và gửi về máy chủ của tin tặc, giúp tin tặc chiếm quyền điều khiển tài khoản mà không cần mật khẩu.

### Câu 3: Thao tác chỉ đăng xuất (xóa phiên đăng nhập) nhưng vẫn giữ nguyên Cache ảnh/CSS
Thay vì dùng chức năng *Clear Browsing Data* (làm xóa sạch cả bộ nhớ đệm khiến trang tải lại rất chậm), em thực hiện thao tác xóa chọn lọc trong DevTools như sau:
1. Mở trang `test.internal-tool.com` và nhấn **F12** để bật DevTools, sau đó chọn tab **Application**.
2. Ở cột danh mục bên trái (phần **Storage**), mở mục **Cookies** và nhấp vào đúng tên miền `https://test.internal-tool.com`.
3. Tại bảng danh sách bên phải, nhấp chuột phải vào dòng Cookie lưu phiên đăng nhập (như `session_id` hoặc `auth_token`) rồi chọn **Delete** (hoặc nhấn biểu tượng **Clear All Cookies** để xóa riêng Cookies của trang này), sau đó nhấn **F5**.
4. Khi đó, phiên đăng nhập bị hủy ngay lập tức (tài khoản được đăng xuất), nhưng toàn bộ bộ nhớ đệm **Cache** chứa hình ảnh và file CSS vẫn được giữ nguyên.

## PHẦN E – DEBUG BẰNG INSPECT ELEMENT VÀ NETWORK TAB

### Câu 1: Thao tác thử sửa màu nút "Đăng nhập" trực tiếp trên trình duyệt
Để kiểm chứng mã màu đúng thiết kế ngay trên trình duyệt mà không can thiệp vào file mã nguồn gốc của dự án, em thực hiện:
1. Nhấp chuột phải trực tiếp vào nút **"Đăng nhập"** trên trang `test.internal-tool.com` và chọn **Inspect (Kiểm tra)** để mở tab **Elements** nhảy thẳng tới thẻ HTML của nút đó.
2. Quan sát khung **Styles** bên phải, tìm thuộc tính quy định màu sắc của nút (thường là `background-color` cho màu nền hoặc `color` cho màu chữ).
3. Nhấp chuột vào ô vuông màu nhỏ bên cạnh mã màu hiện tại để mở bảng chọn màu (**Color Picker**) hoặc nhấp đúp vào giá trị mã màu cũ và gõ mã màu chuẩn theo bản thiết kế (ví dụ `#2563eb`).
4. Quan sát sự thay đổi màu sắc tức thời của nút "Đăng nhập" trên màn hình. Khi xác nhận màu đã khớp hoàn toàn với thiết kế, em ghi lại đúng tên class/selector và mã màu CSS đó để báo cho Dev cập nhật vào file nguồn.

### Câu 2: Áp dụng Quy trình 4 Bước Debugging cho request API bị lỗi màu đỏ trên tab Network
Khi phát hiện một dòng request API hiện màu đỏ trong tab **Network**, em thực hiện tuần tự 4 bước sau:
1. **Bước 1 – Xác định request lỗi và mã trạng thái (Identify):** Quan sát dòng màu đỏ trên bảng **Network**, xem cột **Name** để biết chính xác tên endpoint API đang bị lỗi và xem cột **Status** để xác định nhóm mã lỗi HTTP (lỗi phía Client `4xx` như `400`, `401`, `403`, `404` hay lỗi phía Server `5xx` như `500`, `502`).
2. **Bước 2 – Kiểm tra dữ liệu gửi đi từ Client (Inspect Request):** Nhấp vào dòng request màu đỏ đó, mở tab con **Headers** để kiểm tra `Request URL`, `Request Method` (`GET`, `POST`, `PUT`...) và token xác thực; tiếp tục mở tab con **Payload** để kiểm tra các tham số hoặc dữ liệu JSON gửi lên có đúng tên trường và kiểu dữ liệu hay không.
3. **Bước 3 – Phân tích phản hồi lỗi từ Server (Inspect Response):** Chuyển sang tab con **Preview** hoặc **Response** để đọc nội dung JSON/thông báo lỗi chi tiết (`message`, `error_code`, `details`) mà Server trả về nhằm xác định nguyên nhân gốc rễ.
4. **Bước 4 – Đối chiếu, kiểm chứng và phối hợp xử lý (Verify & Resolve):** Đối chiếu nguyên nhân vừa đọc được với tài liệu API mentor cung cấp (và kiểm tra thêm tab **Console** xem giao diện có bị văng lỗi JavaScript khi nhận dữ liệu lỗi không), sau đó tổng hợp đầy đủ bằng chứng (URL, Status Code, Payload, Response) báo cáo lại cho mentor/Dev để xử lý.

### Câu 3: Hai thao tác cần bật trên tab Network để chỉ xem API và luôn lấy dữ liệu mới nhất
1. **Thao tác 1 – Lọc chỉ hiển thị lời gọi API:** Trên thanh phân loại bộ lọc của tab **Network**, nhấp chọn mục **`Fetch/XHR`**. Thao tác này giúp ẩn toàn bộ các tài nguyên tĩnh như hình ảnh (`Img`), bảng định dạng (`CSS`), phông chữ (`Font`) và chỉ giữ lại các lời gọi API trao đổi dữ liệu.
2. **Thao tác 2 – Ngăn trình duyệt dùng dữ liệu cũ từ bộ nhớ đệm:** Tích chọn vào ô **`Disable cache`** nằm trên thanh công cụ phía trên của tab **Network**. Khi ô này được bật (trong lúc mở DevTools), mọi request gửi đi đều buộc trình duyệt phải lấy dữ liệu mới nhất trực tiếp từ Server thay vì đọc từ Cache.
