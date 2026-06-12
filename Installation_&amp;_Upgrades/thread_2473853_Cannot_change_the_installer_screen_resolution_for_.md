---
title: "Cannot change the installer screen resolution for Ubuntu Server 20.04 LTS"
date: 2022-04-16
forum: Installation &amp; Upgrades
---

### Post by codrut-popescu on 2022-04-16
I am trying to install Ubuntu Server 20.04.4 LTS (No X Server, no GUI) on my Intel NUC. My HDMI output is redirected to a video capture card (if that matters) which supports 4k display which feeds video into my laptop.
The problem is that when I start the installer it looks like this:
[https://i.stack.imgur.com/lRsXk.png](https://i.stack.imgur.com/lRsXk.png)
Basically it's just too small for my eyes.
I need to install Ubuntu Server with HWE kernel as this is supporting my wifi card and by pressing 'e' and I'm presenting with this screen:
[https://i.stack.imgur.com/4r4Cr.png](https://i.stack.imgur.com/4r4Cr.png)
I tried here changing:

set gfxpayload=1024x768x32

and the pressing F10 to boot but it didn't had any effect.
What can I do to lower the screen resolution?

videoinfo output

Adapter 'EFI GOP driver':
* 0x000 3840 x 2160 x 32 (15360) Direct color, mask: 8/8/8/8 pos: 16/8/0/24
    0x001  640 x  480 x 32 (2560) Direct color, mask: 8/8/8/8 pos: 16/8/0/24
    0x002  800 x  600 × 32 (3200) Direct color, mask: 8/8/8/8 pos: 16/8/0/24
    0x003 1024 x  768 x 32 (4096) Direct color, mask: 8/8/8/8 pos: 16/8/0/24
    0×004 1280 × 1024 x 32 (5120) Direct color, mask: 8/8/8/8 pos: 16/8/0/24
    0x005 1600 x 1200 x 32 (6400) Direct color, mask: 8/8/8/8 pos: 16/8/0/24
    0x006 1920 x 1440 x 32 (7680) Direct color, mask: 8/8/8/8 pos: 16/8/0/24
    EDID version: 1.3
        Preferred mode: 3840x2160

---

### Post by ActionParsnip on 2022-04-16
Did you try without the "x32" on the end?

---

### Post by codrut-popescu on 2022-04-16
It doesn’t make any difference

---

### Post by codrut-popescu on 2022-04-16
With Ubuntu installed I can see in the dmesg -T output that it's switching to efifb
I don't know how to see the log file for the installer. Anyway, if anyone can solve this mystery, please help! How can I control the resolution for both the Ubuntu Server installer and the OS itself after being installed?


Here is the dmesg output:
[https://paste.ubuntu.com/p/ypmmwz2PKn/](https://paste.ubuntu.com/p/ypmmwz2PKn/)

What's interesting is this:

[Sat Apr 16 13:20:21 2022] efifb: probing for efifb
[Sat Apr 16 13:20:21 2022] efifb: framebuffer at 0x4000000000, using 32400k, total 32400k
[Sat Apr 16 13:20:21 2022] efifb: mode is 3840x2160x32, linelength=15360, pages=1
[Sat Apr 16 13:20:21 2022] efifb: scrolling: redraw
[Sat Apr 16 13:20:21 2022] efifb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[Sat Apr 16 13:20:21 2022] Console: switching to colour frame buffer device 240x67
[Sat Apr 16 13:20:21 2022] fb0: EFI VGA frame buffer device
[Sat Apr 16 13:20:21 2022] Monitor-Mwait will be used to enter C-1 state
[Sat Apr 16 13:20:21 2022] Monitor-Mwait will be used to enter C-2 state
[Sat Apr 16 13:20:21 2022] Monitor-Mwait will be used to enter C-3 state

Maybe someone knows how to control the resolution of the efifb in both the Ubuntu Server installer and the OS after being installed

---

### Post by codrut-popescu on 2022-04-16
The solution was found, apparently, in some Raspberry Pi forums. After all the Intel NUC is just a more powerful RPi.
I have added:
> video=HDMI-A-1:1920x1080M@60
as a parameter to the kernel as seen in the picture:
[https://imgur.com/a/YvI1pNl](https://imgur.com/a/YvI1pNl)
and the screen resolution is now much better:
[https://imgur.com/a/Q5VIuGp](https://imgur.com/a/Q5VIuGp)

Now, I don't know what exactly:
> video=HDMI-A-1:1920x1080M@60
means. Why HDMI-A-1 and what is M in 1080M. But it works.

---

