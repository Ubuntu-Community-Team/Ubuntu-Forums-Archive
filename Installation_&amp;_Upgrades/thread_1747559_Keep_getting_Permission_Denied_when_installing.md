---
title: "Keep getting Permission Denied when installing"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by Whitecolour on 2011-05-02
I made an my iso CD pop it into my laptop and install it

Half way into the installation it goes premission denied

c:/windows/users/ME/apptemp/local/temp/wubi11.04rev197

What am I doing wrong??

---

### Post by Dart00 on 2011-05-02
Maybe you could try booting of the CD and doing a duelboot and following the easy installer and not bother with wubi?

---

### Post by stargazer418 on 2011-05-02
If you're on Windows Vista or 7, make sure you're running the Wubi installer as an administrator.

---

### Post by bcbc on 2011-05-03
> **Whitecolour said:**
> I made an my iso CD pop it into my laptop and install it

Half way into the installation it goes premission denied

c:/windows/users/ME/apptemp/local/temp/wubi11.04rev197

What am I doing wrong??

It's telling you to look in the log file. Open windows explorer, enter **%temp%** in the address bar, and then open the file wubi-11.04-rev211.log. 

If it's not clear what the problem is, post it here between [CODE[SIZE="1"] [/SIZE]][/CODE] tags (# symbol above)

---

