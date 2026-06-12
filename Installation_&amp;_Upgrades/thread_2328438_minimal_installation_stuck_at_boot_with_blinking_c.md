---
title: "minimal installation stuck at boot with blinking cursor"
date: 2016-06-21
forum: Installation &amp; Upgrades
---

### Post by zuku on 2016-06-21
Hello,
I have problem with fresh UEFI minimal install Ubuntu 16.04 LTE, grub is showing but after Ubuntu starts booting I see that monitor is starting to blink trying to get proper resolution and at the end it stops with this error:
/dev/sda6: clean ....../...... files, ..../..... blocks
and cursor blinking.

My notebook is Thinkpad X240 with video Intel Haswell-ULT Integrated Graphics Controller, and I have tried install drivers: sudo apt-get install --reinstall xserver-xorg-video-intel xserver-xorg-core xserver-xorg
but without success.

need Your help.

---

### Post by sudodus on 2016-06-21
How did you install - did you start from the Ubuntu mini.iso?

- Which one, 32-bit or 64-bit?
- Did you install the Ubuntu desktop environment (Unity), or some other desktop environment or no desktop environment?
- Are you running in UEFI mode or BIOS mode?
- Is it Ubuntu only, dual boot or multi boot?

- Is there only Intel graphics or a hybrid system with integrated Intel plus a separate graphics card, for example nvidia?

-o-

Maybe you have better luck if you start from a compressed image file according to the following links

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[Two updated compressed image files are uploaded](http://ubuntuforums.org/showthread.php?t=2213631&page=8&p=13494760#post13494760)

You can try to install such a system to a USB pendrive and test it before deciding to install it to the internal drive.

---

### Post by zuku on 2016-06-22
Yes I have downloaded mini.iso image and converted it bo be UEFI boot capable by adding to image EFI folder.
-this is 64bit 16.04 LTS
-I have installed only based system package nothing more no any graphic environment
-I'm running UEFI mode, GRUB installed without aby problem and I have in grub Ubuntu and Windows 10 everything boots from Grub menu (but Ubuntu hangs during boot)
-multiboot with windows 10 x64 Pro UEFI

this is Thinkpad x240 here is all hardware 
[http://www.ubuntu.com/certification/hardware/201307-14019/](http://www.ubuntu.com/certification/hardware/201307-14019/)

I've made installation from scratch and installed this time Ubuntu Desktop during Setup, this time Ubuntu boot to Unity everything OK,
but I don't want any GUI and it environment only minimal boot to console.

---

### Post by sudodus on 2016-06-22
Sometimes the minimal system does not show anything, probably due to problems with the graphics driver. It can help to switch virtual screen with

*ctrl + alt + F1*
*ctrl + alt + F2*
...
*ctrl + alt + F6*

(*ctrl + alt + F7* - is reserved for a graphical desktop)

Sometimes you need to press the Enter key an extra time.

If this is the case you can try with different methods. One of them is to install the package **xserver-xorg-video-intel**, another to try different boot options, or set console mode in grub.

---

### Post by sudodus on 2016-06-22
There is one more big problem:

The Ubuntu mini.iso does not work in ***UEFI*** mode. If you want to install a text mode system in UEFI mode, you should start from the ***Ubuntu Server 64-bit iso file*** instead. Maybe what you added is enough, maybe not, for example, there seems to be something missing for the graphics.

So please try to install from the Ubuntu Server iso file. If you avoid installing any server package, you will get a result, that is very similar to what you get from the mini.iso.

---

### Post by zuku on 2016-06-24
thanks, problem solved I have installed OS using ubuntu server iso image.

---

