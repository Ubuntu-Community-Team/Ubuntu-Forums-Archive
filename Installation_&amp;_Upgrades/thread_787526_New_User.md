---
title: "New User"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by Danattaway on 2008-05-09
Today I loaded my first Linux machine, I loaded Ubuntu.  I did this on a Virtualbox.  When I tried to load VBox Additions I could not because I was not administrator. Whats up with this, I created this machine but I do not have admin privalages, this is ridiculas. What am I doing wrong? How do I give myself admin rights on this machine that I just built. Any help will be appreciated. I have a lot of experiance in DOS and Windows but none in Linux so please type slow.

Thanks,
Dan

---

### Post by TryMe on 2008-05-09
"sudo" will allow you to execute commands as root. It's like the runas command in windows except better.

more info here: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by ilrudie on 2008-05-09
The Short Answer: sudo is correct.  

The Long Explanation:  It will allow you to perform the command that follows it as if you were root (In Linux and more generally Unix/Posix root is the ultimate user and can do absolutely anything on the box... like an administrator in Windows).   It is not recommended that you actually run as root for normal day to day use (Ubuntu prevents this by disabling the root account preventing users from logging in as root).  This is because many exploits happen at a user level, allowing arbitrary code execution as the user who was exploited.  If root is exploited the entire system can be over run because there are no boundaries for root.  If a standard user is exploited that user may be hosed but the whole system is not lost.  It seems a little annoying to have that extra step every time you want to make a system wide change at first but hopefully now that you have a little background and know about the extra security you are getting typing sudo won't bother you so much.

Happy Ubuntuing

---

