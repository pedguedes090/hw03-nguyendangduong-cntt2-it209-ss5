# Bài 3 — Rebase và xử lý conflict theo từng commit

**Sinh viên:** NguyễnDăngDương
**Lớp:** CNTT2 — IT209 — Session 05

## Thiết lập hai nhánh

Nhánh `main` có cấu hình nền với `port` và `env`. Nhánh `feature-api` tạo hai commit riêng: đổi `port` thành `9000`, sau đó đổi `env` thành `production`. Trong lúc đó, `main` tạo hai commit xung đột trên cùng các trường: đổi `port` thành `8081` và `env` thành `staging`.

```bash
git switch feature-api
git rebase main
```

## Xử lý từng conflict

Conflict đầu xuất hiện khi áp commit đổi `port`. Sửa `config.json` để giữ cấu hình hợp lệ, stage file và tiếp tục:

```bash
git status
git add config.json
git rebase --continue
```

Commit feature tiếp theo xung đột trên `env`; giải quyết trường này, rồi lặp lại `git add config.json` và `git rebase --continue`. Không dùng `git merge` thay cho rebase. Nếu muốn quay lại trạng thái trước lần rebase, dùng `git rebase --abort`.

## Kiểm tra lịch sử

```bash
git status
git log --graph --oneline --all
```

Kết quả hoàn tất có lịch sử tuyến tính: hai commit main đứng trước hai commit feature đã được áp lại; không có merge commit phát sinh từ rebase. Trong mỗi lần dừng, đọc `git status` để biết commit nào đang áp và file nào cần giải quyết.
