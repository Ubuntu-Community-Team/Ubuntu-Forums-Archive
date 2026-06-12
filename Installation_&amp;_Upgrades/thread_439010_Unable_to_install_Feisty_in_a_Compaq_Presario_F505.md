---
title: "Unable to install Feisty in a Compaq Presario F505"
date: 2007-05-10
forum: Installation &amp; Upgrades
---

### Post by rodrigouroz on 2007-05-10
Hi, I'm not being able to install this beatiful distribution (that's why I want to insist) in a Compaq Presario F505. It seems like there's some kind of problem with the video driver. This is what I've done so far. 

I booted with the Live CD (Ubuntu Feisty) and when it should started loading, it freezed (I couldn't access any terminal, couldn't do a soft reset, anything). So, hard reset and another try.

Before booting from Live CD y set VGA 1024x800 16 bits and it started!!. I installed it without any problem, but when I rebooted to start Ubuntu from the newly partition... guess what... freeze.

So, I started it in recovery mode. Then I saw an error loading the Broadcom wireless card. As I want to use Ndiswrapper I just removed that module from the kernel (and send it to the blacklist). Reboot. Nothing. Freeze. Again in recovery mode. Nothing, no errors. But X doesn't start.

The last thing I tried was starting again in recovery mode, and did a dpkg-reconfigure xserver-xorg. I chose Vesa (nv was before) in 1024x800 in 16 bits. Nothing, when I use startx, it freezes. I have to do a hard reset. I can't even access a terminal nor kill the X server with CTRL+ALT+BACKSPACE.

I was told to try with an alternative CD, and install in text mode and then download the official nvidia drivers. I was also told to use Suse instead, but I love Ubuntu. My last chance is using Debian, but I want to try something more before.

Does anyone know what else I can try?

---

