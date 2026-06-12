---
title: "Installation of 12.04 32-bit on USB; want 64-bit on another HDD"
date: 2013-06-08
forum: Installation &amp; Upgrades
---

### Post by patrickbp on 2013-06-08
Here's my situation:

I installed 12.04 LTS on a 64GB USB drive, which installed fine. The drive runs a bit slow, but I like Ubuntu. (I used Red Hat maybe 15-20 years ago). Anyway, I decided to use my second hard drive, a 320GB, and since I have an Intel Duo Core 2 processor, decided to put 12.04 64-bit on it. So, I made a separate USB boot stick with the 64-bit version. It tells me "Boot manager is missing" (even though I created it with Pendrive). I tried 13.04 64-bit (on the USB drive),with the same message. I then burned a DVD with 12.04 x64. It gives me a graphics error, or if it makes it to the desktop, it prompts me for a User name/password. It does not load the "Try Ubuntu | Install Ubuntu". So, I got a regular CD, tried it again. Now I get a prompt asking me for the boot type with either "1" or "2" (with no explanation of what the boot types mean). Then it's very erratic booting, with either "Grub rescue", black screen, or a Ubuntu desktop with no "Try Ubuntu | Install Ubuntu". 

I don't know what to do about it, and wonder if other users are having a similar issue. Any suggestions?

Added note: If I boot into my existing 12.04 32-bit on USB, if I put the CD in, it does not ask me if I want to upgrade or install; it asks me instead if I want to use package manager to view the packages.

---

### Post by oldfred on 2013-06-09
CD's are not large enough for newest version, so I do not think a CD will work at all. I use flash drives just to avoid burning lots of CD/DVDs as I did in the past. And with an install I just use grub2's loop mount to directly boot the ISO. 

Some just have issues with certain flash drives or certain flash drive creators. 
       Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

      
 [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)


 Also instructions for DVD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by patrickbp on 2013-06-09
I managed to successfully install 12.04 64-bit! I was using a USB drive created in Windows with Pendrive, which didn't work at all, strangely. So, I then created a USB startup disk using Startup Disk Creator, putting the .iso image on it. Booted up and installed with nary a problem. Go figure!

---

