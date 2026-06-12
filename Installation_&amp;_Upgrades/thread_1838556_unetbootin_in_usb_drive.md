---
title: "unetbootin in usb drive?"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by Matrix01 on 2011-09-03
i like to install ubuntu in usb drive, 

i connected usb drive when installing unetbootin.

Is unetbootin installed in hard drive or usb drive?


[ATTACH]201424[/ATTACH]

---

### Post by 2F4U on 2011-09-04
unetbootin is installed on your computer's hard drive and can be used to create a bootable usb drive.

---

### Post by Matrix01 on 2011-09-04
does usb drive need to be formatted in FAT 32?

---

### Post by Hakunka-Matata on 2011-09-04
Yes, format it fat32, and mark the flags, boot, lba.

partition for ubuntu Desktop install size, 1GB more than enough.

---

### Post by Matrix01 on 2011-09-04
][ATTACH]201479[/ATTACH]

I installed bootloder in usb stick which has 1 GB, this installation took hours...
and
selected language, time zone, keyboard....
installation....
usb drive is not shown here...???

how can i install ubuntu 10.04 in usb drive?
[ATTACH]201478[/ATTACH

---

### Post by Hakunka-Matata on 2011-09-04
> **Matrix01 said:**
> 

I installed bootloder in usb stick which has 1 GB, this installation took hours...
and
selected language, time zone, keyboard....
installation....
usb drive is not shown here...???

how can i install ubuntu 10.04 in usb drive?


You have booted off the usb drive, correct?
It looks like you did, and there is no empty space on your hard drive to install ubuntu to.  
Everything is working correctly.

You'll have to reboot into Windows, use window's disk management software to defragement your hard drive, two times minimum.  Then reboot back into Windows, so see it is still working.  Then shrink some partition and leave space for ubuntu.  Those details come later, are you booted from the usb drive?

---

### Post by Matrix01 on 2011-09-04
How do i know ubuntu is booted from usb drive?
usb pen drive is connected.

i like to install ubuntu in usb drive, not in hard drive.

---

### Post by Hakunka-Matata on 2011-09-04
[https://help.ubuntu.com/community/Installation/FromImgFiles#Mac_OS_X](https://help.ubuntu.com/community/Installation/FromImgFiles#Mac_OS_X)

Oh, now I get it.

[B]EDIT: NO, I DO NOT GET IT.  It looks like that link above has what you need.

BURN LiveCD/USB for MAC, while running a Linux/Ubunu OS on a PC.

but you can burn a persistence usb install stick, 'liveCD/USB", for ubuntu installation onto a PC.  I don't know how to do it for mac, "download the ubuntu install .iso for MAC, and burn it to usb using unetbootin?



[/B] You need minimum size 4GB usb stick.
you can use unetbootin, select the **persistence** button.  8GB drive is much better, or bigger still.

---

### Post by Hakunka-Matata on 2011-09-04
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

that's the one to look at!

---

### Post by Matrix01 on 2011-09-04
some people said 1 GB or larger..

[http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/](http://www.howtogeek.com/howto/linux/create-a-bootable-ubuntu-usb-flash-drive-the-easy-way/)

---

### Post by Hakunka-Matata on 2011-09-04
1GB is not enough for a **persistence **install, as I understand it.  Google it, maybe?

---

