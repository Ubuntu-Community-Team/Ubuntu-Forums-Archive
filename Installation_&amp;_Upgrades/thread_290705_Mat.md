---
title: "Mat"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by qmatin on 2006-11-01
Hi
 I am kind of new in Ubuntu linux and I am loving it. I stumped at one problem. May be somebody could help me...thanks.

What is the exact command line to install a program from CDrom ?
Suppose the program is mat, which is in a cd. How can I install this program in my pc through Terminal window ? From cd rom to harddrive.

my e-mail address is [email]sky11@comcast.net[/email]

---

### Post by taurus on 2006-11-01
You first need to mount your CD which it would have been automatically mounted when you insert it.  Then, you need to change to wherever it has been mounted, usually /media/cdrom0.  Then, you need to run the executable file to install it to your harddrive.  If you can list the output of this command, perhaps I can spot an installer for you!!!

```
ls -la /media/cdrom0 
(assuming that it has been mounted on /media/cdrom0!!!)
```

---

