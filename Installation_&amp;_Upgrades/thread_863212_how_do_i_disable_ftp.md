---
title: "how do i disable ftp?"
date: 2008-07-18
forum: Installation &amp; Upgrades
---

### Post by alex5025 on 2008-07-18
ok i want to disable ftp
how do i do it?
im trying to connect my self and i think the ftp server is fzSftp
how do i disable it or remove it?

---

### Post by cpetercarter on 2008-07-18
I guess you can remove it with
```
sudo apt-get remove fzsftp 
```

---

### Post by alex5025 on 2008-07-18
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package fzsftp

---

### Post by cpetercarter on 2008-07-18
OK, I guess you have Filezilla - try
```
sudo apt-get remove filezilla
```

---

### Post by alex5025 on 2008-07-18
ty it worked! thanks

---

