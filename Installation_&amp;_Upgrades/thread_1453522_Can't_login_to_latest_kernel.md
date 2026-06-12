---
title: "Can't login to latest kernel"
date: 2010-04-13
forum: Installation &amp; Upgrades
---

### Post by dcroxton on 2010-04-13
Hi, I'm running 9.10.  I had a strange issue after the latest kernel upgrade (I believe to 2.6.31) -- I can't login.  It just keeps returning me to the login screen.  This happens in normal and safe mode; the vm "works" as far as logging in goes, but it hangs and I get nothing but wallpaper on the screen.

I was worried I might have to do a password reset at first, but it turns out I can log in to the previous kernel with no problem.  Any idea what's up with this?

Sincerely,
Derek

---

### Post by bumanie on 2010-04-13
That login loop seems to be a bug that appears now and again - just use the previous kernel, but you should also place a bug report with launchpad so that developers can look at it and hopefully fix it. It has happened to quite a few testers of 10.04.

---

