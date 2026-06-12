---
title: "no permissions to make or changes files folders -please help-"
date: 2006-09-03
forum: Installation &amp; Upgrades
---

### Post by bubi1980 on 2006-09-03
hi,

I would like to create a skin folder for BMP. What I do is: open file system/usr/include/bmp/ and try to create a skin folder but dont have the permission to make or change folders files.
I have the same problem in "file system/usr/share/backgrounds (to change wallpapers).
I have a password and username, am I not the root?
please help me out

---

### Post by ayoli on 2006-09-03
the user you are is not root, to gain root rights use sudo, you will be prompted for your _user_ password.
use sudo in a terminal like this:
```
[11:52:11@ayoli.zone]:~ >$ sudo mkdir /usr/lib/bmp/example
Password:
```

---

### Post by whizbaby on 2006-09-03
**bubi1980 is multithreading the forum**

---

