# Hướng dẫn sử dụng Git, GitHub !
**Người thực hiện**: [Facebook](https://facebook.com) 
[Github](https://github.com/qhaof26)

**Nguồn tham khảo Git, GitHub**: [Youtube](https://www.youtube.com/watch?v=-VmX40r5ARI&t=209s)

**Cách viết file .md**: [Youtube](https://www.youtube.com/watch?v=jJky0Ws9xKg)

---
#### Git là gì ?
> Git là thẻ nhớ cho dự án, lưu các phiên bản của dự án.
#### Các từ thường gặp
- Repository (repo) : nơi lưu trữ.
- Branch : nhánh.
- Conflict : xung đột.
- Local : những gì có ở trên máy.
- Remote : các thứ bên ngoài.
#### Cấu hình Git
> git config -g user.name qhao

> git config -g user.email qhaofdev@gmail.com

> git config -g user.name : kiểm tra cấu hình
#### Các câu lệnh
1. `git remote add origin link-repo` : đặt tên cho link gốc.

2. `git init` : khởi tạo 1 dự án thành git repository.

3. `git add .` : chuẩn bị lưu lại thời điểm hiện tai của dự án.

4. `git commit -m ‘message’` : chính thức lưu + ghi chú lần commit đó có ý nghĩa gì.

5. `git push origin master` : đẩy từ local repo → remote repo.

> **Note**: 1 pull request chỉ nên có 1 commit.

    Trường hợp: khi đã commit và push code lên, nhưng lại thiếu mất chức năng. Sau khi code thêm 1 số file thay đổi, thì dùng: 
6. `git commit —amend`: nó sẽ ghi đè lại với cái commit trước đó.

7. `git push -f origin master`: để push lại với pull trước đó. 

    `Esc + :wq` để thoát khi dùng `git commit --amend`.
> → Mục đích 6 & 7: Tránh việc dư thừa commit.

8. `git pull = git fetch + git merge`
- Example: **`git pull origin master`**
- **`git fetch`**: Lấy tất cả các thay đổi từ kho lưu trữ từ xa (remote) mà chưa có trong kho lưu trữ cục bộ (local). Điều này bao gồm các commit mới, các nhánh mới, và các thay đổi khác.
- **`git merge`**: Sau khi `fetch`, `git pull` sẽ tự động gộp (merge) những thay đổi mới từ kho lưu trữ từ xa vào nhánh hiện tại mà bạn đang làm việc. Nếu có xung đột (conflict) trong quá trình gộp, bạn sẽ cần phải giải quyết xung đột đó trước khi hoàn thành việc gộp.

9. `git rebase` (Teamwork thực tế)
- Trường hợp: có 3 branch **master**, **login**, **cart**. A code **login** xong và gộp vào nhánh **master** rồi. B code **cart** muốn sử dụng component trong **login**, nhưng lại chưa có component đó ở trong **cart** → `git rebase`: gộp code lại tương tự `git merge`. → B đã có component ở **login** để sử dụng trong **cart**.
- Example: Branch **cart**: `git rebase master`.

10. `Branch`
- `git branch` : kiểm tra branch mặc định.
- `git checkout {nameBranch}` : chuyển sang branch khác.
- `git checkout -b {nameBranch}` : tạo ra 1 branch mới với tên branch là nameBranch. 
- `git branch -d {nameBranch}` : xóa 1 branch.
- `git checkout -b {nameBranch} {id-log}` : khôi phục lại branch đã bị xóa với id cũ.

11. `remote`
- `git remote -v` : show tất cả các origin.
- `git remote rm orgin` : xóa origin.

12. `log`
- `git log --oneline` ~ `git reflog` : Hiển thị tất cả các commit với id + branch + commit,…

13. `Đang cập nhật`
- **remote → local (thường dùng hơn)**
    
    origin : https://github.com/repo.git
    
    `git clone {url repo}`
    
    git push -u {url remote repo name} {url remote repo} : đẩy 1 branch lên remote repo.
     
    Ex: `git push -u origin dev`. Chỉ cần dùng lần đầu, còn lần sau chỉ cần git push.
    
    Nếu muốn clone 1 branch trên remote repo: git checkout master → git fetch origin → git checkout -b {branch name} origin/{branch name}
    git branch : kiểm tra lại các branch.
    
    `Pull request` : gộp các branch lại trên remote repo
       → Trên local repo: muốn xem lại thay đổi → git pull
    
    `Git Ignore`: khi không muốn cho github theo dõi 1 file nào đó trong dự án.
       → Tạo file .gitignore → viết tên file vào trong .gitignore