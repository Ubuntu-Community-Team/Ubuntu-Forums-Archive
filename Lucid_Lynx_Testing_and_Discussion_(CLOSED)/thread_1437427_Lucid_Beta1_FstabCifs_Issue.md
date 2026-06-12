---
title: "Lucid Beta1: Fstab/Cifs Issue"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hybridr6 on 2010-03-23
Every time Ubuntu gets updated I run into more fstab/cifs problems...

Ok so when using "sudo mount -a" everything works fine and dandy. Just booting up normally though, the shares are mounted with nothing in them. I'm guessing there is some option needed? Please Help!

Here's the line from my fstab.

```
//10.10.10.2/ash  /home/ash/Documents  cifs  username=ftp,password=,noperm,uid=1000,iocharset=utf8  0  0
```

---

### Post by dcstar on 2010-03-23
> **hybridr6 said:**
> Every time Ubuntu gets updated I run into more fstab/cifs problems...

Ok so when using "sudo mount -a" everything works fine and dandy. Just booting up normally though, the shares are mounted with nothing in them. I'm guessing there is some option needed? Please Help!

Here's the line from my fstab.

```
//10.10.10.2/ash  /home/ash/Documents  cifs  username=ftp,password=,noperm,uid=1000,iocharset=utf8  0  0
```

Ask all pre-release questions in the Development forum.

10.04 is a testing release, not a production release.

---

### Post by hybridr6 on 2010-03-24
> **dcstar said:**
> Ask all pre-release questions in the Development forum.

10.04 is a testing release, not a production release.

[http://ubuntuforums.org/showthread.php?t=1437447](http://ubuntuforums.org/showthread.php?t=1437447)

---

