---
title: "Help installing Lubuntu 16.04 on a laptop"
date: 2016-05-07
forum: Installation &amp; Upgrades
---

### Post by bobapplepie on 2016-05-07
I am trying to install it on an old windows-xp era computer.  The  installation works fine, but when it's done and I restart it, it hangs  on a black screen and says "/dev/sda1: clean, 121444/370208 files,  654953/1478400 blocks" and has a blinking cursor.  Does anyone know how  to fix this?

---

### Post by mörgæs on 2016-05-07
Hi, welcome to the fora.

My guess is that you have Intel graphics. We see a lot of these cases with Lubuntu: [http://ubuntuforums.org/showthread.php?t=2323514](http://ubuntuforums.org/showthread.php?t=2323514)

---

### Post by bobapplepie on 2016-05-07
Thanks for the help.  I followed the instructions on an old thread and got it working.

---

### Post by mörgæs on 2016-05-07
Good, please post the solution and mark the thread 'solved'.

---

### Post by bobapplepie on 2016-05-09
Solution: I went into the options menu in grub and added "nomodeset" after the words "quiet splash."  Then I used Synaptic to install the packages "xserver-xorg-video-intel" and "xserver-xorg-video-intel-dbg" and then rebooted the computer.

---

