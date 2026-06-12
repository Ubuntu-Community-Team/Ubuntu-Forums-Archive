---
title: "Video Problem when installing ubuntu on old system"
date: 2007-08-26
forum: Installation &amp; Upgrades
---

### Post by cooldoe on 2007-08-26
I tried to install Ubuntu 7.04 to my old computer but there some problem with the video.

My spec as follow:
Intel Celeron 900mhx
256 mb Ram
Nvidia MX200 128mb

The live CD would not work as I cannot get the correct screen resolution. 
The screen become unreadable because there are several instance of the screen clash.
Just like when you tried to change to incorrect resolution in windows.

Tried installing with alternate Ubuntu CD. Ubuntu install ok with the text vesio but when loaded the same thing occur.

Can anyone help me? I'm newbie here.

---

### Post by SilentStrike on 2007-08-26
Sounds a lot like what im experiencing. Try booting Ubuntu in safe graphics mode form the LiveCD and see what happens.

---

### Post by Pumalite on 2007-08-26
256 MB RAM or less>Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/) If you want something that installs easy and run fast in your computer. With 256 MB RAM you cannot boot the Live CD.

---

### Post by cooldoe on 2007-08-27
I have tried Ubuntu Alternate it does not work.

Live CD would not work for sure. I tried the safe mode.

I will try the xubuntu alternate and let you know

---

### Post by cooldoe on 2007-08-29
XUBUNTU alternat have the sample problem as well.

Any other idea to solve this problem?

---

### Post by Pumalite on 2007-08-29
Try sudo dpkg-reconfigure xserver-xorg. Say yes to most defaults, choose 'vesa' as your driver. Then: startx

---

### Post by cooldoe on 2007-08-30
when do i type it? 

I'm complete newbie here

I type the comment during instalation or after?

If after, how do I get out of the x-windows. It autamatically load the window.

---

### Post by Pumalite on 2007-08-30
Ctrl+Alt+F1

---

