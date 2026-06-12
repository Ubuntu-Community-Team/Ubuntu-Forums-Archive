---
title: "Will Ubuntu install on my Windows 7 Home Basic(64 bit)?"
date: 2010-09-05
forum: Installation &amp; Upgrades
---

### Post by Evil Eye on 2010-09-05
as above
i am using Windows 7 Home Basic on 64 bit machine

my query was:
will i be able to install the latest version of ubuntu inside windows i.e. without partitioning the hard drive?

thanks in advance

---

### Post by 73ckn797 on 2010-09-05
I have not performed what is called a "WUBI" installation into Windows in several years. You should be able to quite easily.

See this link for instructions: [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by andymorton on 2010-09-05
I did a Wubi install on a Windows 7 computer a while ago. I didn't have any problems at all. :)

andy

---

### Post by Evil Eye on 2010-09-06
thanks a lot for your help guys


i installed ubuntu on D: drive of my laptop which is the Data drive
now when i run ubuntu, it only shows C: and doesn't show the D: on which it is installed, is there any way in which it will show the contents of D: drive?


thanks :)

---

### Post by 73ckn797 on 2010-09-06
Run this command in a terminal and post the results:
```
sudo blkid
```

---

### Post by Evil Eye on 2010-09-07
solved, thanks!

---

