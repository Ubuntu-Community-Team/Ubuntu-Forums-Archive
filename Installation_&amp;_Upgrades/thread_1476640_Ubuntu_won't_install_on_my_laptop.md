---
title: "Ubuntu won't install on my laptop"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by Fost325 on 2010-05-08
I have a new laptop that I can install ubuntu on without hassle using a cd.

I wanted to put it on my older Toshiba laptop (2003) for my little cousin to use to get on the internet and play games.

When I boot from the CD the ubuntu logo comes up runs.
It ask me my language then goes to the screen where I can choose
"Try Ubuntu without installing it"
"Install Ubuntu Now"
etc
etc

Ive tried clicking both install and try
both launch the ubuntu logo it runs for about 4 min and then hangs on a black screen.
I know it isn't the cd because I can use it on any other computer and it works.

This Toshiba cannot boot from a jump drive though so that choice is out.

---

### Post by Catharsis on 2010-05-08
From the menu, press F6 and then Esc to edit the boot parameters. Replace "quiet splash" with "nomodeset". If that doesn't work, try replacing it with "i915.modeset=1". If that doesn't work either, try "xforcevesa noapic noapci nosplash irqpoll"

Also, do you know what graphics card you have? If you can get to a terminal, type:
```
lspci | grep VGA
```

---

### Post by nikefalcon on 2010-05-08
I get the same problem, See this thread:
[http://ubuntuforums.org/showthread.php?t=1476182](http://ubuntuforums.org/showthread.php?t=1476182)

i havn´t tried davidmohammed´s suggestion as yet-using XVESA instead of Xorg.

---

### Post by nikefalcon on 2010-05-09
Ok everyone! here's a fix!
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

