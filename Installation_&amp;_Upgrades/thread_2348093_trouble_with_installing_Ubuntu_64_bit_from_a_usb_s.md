---
title: "trouble with installing Ubuntu 64 bit from a usb stick (but 32 bit works)"
date: 2016-12-31
forum: Installation &amp; Upgrades
---

### Post by Anfanglir on 2016-12-31
Hi!
I'm having trouble with installing Ubuntu 64 bit from a usb stick. When I load the stick with an old version of Ubuntu 32 bit (14.04.1 LTS) everything works, but when I create the startup disk with a 64 bit iso (16.04 or 16.10) I get the following error message when booting:

“Missing parameter in configuration file. Keyword : path
gfxboot.c32: not a COM32R image
boot:”

I have googled this error and found the advice to press TAB and then write “live”, or alternatively write “help”. In either case the screen goes black and nothing else happen (I have waited a long time). After a while the display gives the message no signal recieved and goes into power saving mode.

I have created the startup disk with Ubuntu's utility. I have tried with different USB sticks. Also tried Unetbooting. Unetbooting loads the first menu, but when I press try out or install, the result is a black screen.

My computer runs on an ASUS P7P55D pro motherboard, Intel i5 processor, Radeon HD 6670 graphics card, 8 gb ram. I have previously been running 64 bit Ubuntu with same processor, motherboard and rams (but different graphic card and harddrive).

Thankful for any advice. / Anfanglir

---

### Post by sudodus on 2016-12-31
I think this problem is due to the tool to create the USB boot drive. Try a cloning tool, for example mkusb according to this link:

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by Anfanglir on 2016-12-31
OK, I will look into that, thanks! 

/ Anfanglir

---

### Post by bearlake on 2017-01-01
> **sudodus said:**
> I think this problem is due to the tool to create the USB boot drive. Try a cloning tool, for example mkusb according to this link:

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

^^^^^ +1

Never looked back after the first time used.

---

### Post by Anfanglir on 2017-01-02
I tried something else before testing mkusb, I made a 64 bit 12.04. startup disk (with the Ubuntu startup disk tool). That one worked. Then made an upgrade to 14.04, that also worked. After another upgrade to 16.04 I once again lost the display (everything is black). It looks like there is some problem with the drivers for my graphic card (Radeon HD 6670) in 16.04/16.10. 

I'm now in the process of installing 12.04/upgrading to 14.04 again, and will stick with 14.04 for now. Will make a note of mkusb for future use though, thanks.

/ Anfanglir

---

### Post by sudodus on 2017-01-02
When you feel that your problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

