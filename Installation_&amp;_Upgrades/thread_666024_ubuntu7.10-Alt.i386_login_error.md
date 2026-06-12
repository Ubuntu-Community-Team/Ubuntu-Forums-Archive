---
title: "ubuntu7.10-Alt.i386 login error"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by dzuari on 2008-01-12
i just installed ubuntu 7.10-Alternate.i386.iso onto my portable HD with a CD-R. when i boot to my harddrive and ubuntu loads up, i try to login and it goes through but before anything loads a error pops up saying iv been logged in for less than 10 sec and have an error. the error is "/.xsession-errors file". any help?

---

### Post by taurus on 2008-01-12
Press <Ctrl><Alt>F2 and log in with your username and password.  Then, have a look at your ~/.xsession-errors.

```
tail -30 ~/.xsession-errors
```
Also, check your disk space while you are at it.

```
df -h
```

---

### Post by dzuari on 2008-01-12
when i typed in the Tail code nothing came up after it, and for my disk space i installed ubuntu onto a 75G partition but it only showed that i use 100% of 2Gs on dev/fts1

---

### Post by taurus on 2008-01-13
Sounds like somehow you made / to be a little small and it's all filled up.  Try to free up some space so at least you can log in with

```
sudo apt-get clean
```
Then, get back to GUI log in screen with <Alt>F7 and log in.  Post the outputs of these commands here.

```
sudo fdisk -l
df -h
```

---

