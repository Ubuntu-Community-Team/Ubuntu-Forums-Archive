---
title: "Graphical issues during installation"
date: 2012-05-22
forum: Installation &amp; Upgrades
---

### Post by rlesko on 2012-05-22
Hey All,

I'm having some issues during installation.  First of all, when I boot from the cd drive to install, I am not presented with any GUI interface.  I'm given 3 choices and must use controls with the arrow keys.  "Try Ubuntu without installing", "Install Ubuntu", and some check disk option.  I arrow down to Install, and hit enter.  Then, I just get a few colored lines across the middle of the screen.  I'm not given the function key options at the bottom of the screen that I've read about using when the graphics are failing.  Any suggestions?  Thanks.

---

### Post by BlinkinCat on 2012-05-22
Hi,

Did you check your md5sum ?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by rlesko on 2012-05-22
Checksum is correct

---

### Post by darkod on 2012-05-22
So, are you actually trying to load the older style main menu?

I'm not sure it loads automatically when graphics are failing.

When it starts to boot, when you see the first purple screen, hit Esc. That should bring up the older main menu.

At the bottom you should have advanced options with the F keys. Most often used is F6 and then nomodeset parameter.

After that select Try Ubuntu first to see if it loads the desktop correctly. Don't start installing right away. Always first check in live mode. It's best even if you don't think graphics is failing.

---

### Post by rlesko on 2012-05-22
I never see a purple screen.  I will take a picture of what I see and post it

---

