---
title: "Having trouble getting my Eee PC 2G Surf to boot Eeebuntu from SD card"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by merrymoll on 2009-12-03
Evenin' all!

The OS on my little Eee PC 2G Surf recently went gaga, so I installed Eeebuntu NBR via USB.  As the hard drive only has 2G it wasn't big enough to contain the new OS, so I copied the boot to my 4G sd card, which works fine.

However - I can't seem to get the machine to boot automatically from the sd card - I have to hit 'Esc' as soon as I turn it on and manually direct it to boot from the sd card - otherwise it just tries to boot from the hard drive.

Can anyone advise me on how to change it so it automatically boots from the sd?  I'm a linux/ubuntu newbie so I'll need VERY detailed instructions, especially of what to type if I need to do anything in the terminal.

Thanking you in advance!

---

### Post by winotree on 2009-12-03
On your device does F2 open the BIOS like mine?  If so, change the boot order so your USB is priority one like so:

Press F2 at ASUS splash screen; press Boot; press or open Boot Device Priority.  Make changes using simple directions in lower right corner [assuming your device is similar to mine].  Press Esc then F10 to save and exit.  I think there's one last screen marked OK -- press enter and it'll re-boot.

It'd be a good idea to double-check by shutting down and restarting your device before claiming success.  ;)

---

### Post by mrawlings on 2009-12-03
yeyee

---

### Post by merrymoll on 2009-12-03
> **winotree said:**
> On your device does F2 open the BIOS like mine?  If so, change the boot order so your USB is priority one like so:

Press F2 at ASUS splash screen; press Boot; press or open Boot Device Priority.  Make changes using simple directions in lower right corner [assuming your device is similar to mine].  Press Esc then F10 to save and exit.  I think there's one last screen marked OK -- press enter and it'll re-boot.

It'd be a good idea to double-check by shutting down and restarting your device before claiming success.  ;)


Thanks for your advice!  Unfortunately, it's not working; I got into  BIOS (it goes there, as you said, when pressing F2 on startup), adjusted the boot device priority and rebooted - but it came up  with "Error 15".  Rebooting and pressing "Esc" to change the boot device  seems to be the only way, so far, to get the OS started.

---

### Post by sgosnell on 2009-12-03
You put the bootloader for Eeebuntu on the SSD.  Bad idea.  See [this thread](http://ubuntuforums.org/showthread.php?t=224351) for instructions for reinstalling grub on the SD card.  You'll have to boot from the USB install drive, then make sure you find the SD card, which is probably sdb, NOT sda.  Sda is the SSD.

---

### Post by winotree on 2009-12-03
Ouch!  But thanks to **sgosnell **for the quick catch!  :D  Hope to read tomorrow that you're OK.

---

### Post by merrymoll on 2010-03-08
Just a quick note to you all that I managed to install the stripped down Basic version of EEEbuntu.  It's up and running just fine.  Thanks so much to everyone for all your help and advice!  :p

I'll mark this thread as "solved"

---

