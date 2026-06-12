---
title: "[SOLVED] USB Ubuntu/KUbuntu boot problem."
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by solarwind on 2008-02-06
Hey all,

I'm trying to install Ubuntu/KUbuntu on a computer without a CD rom drive. In order to do this, I prepared a 1 GB USB memory stick on **Windows** using the guide here: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

The drive boots and I see the little Ubuntu/KUbuntu loading progress bar but after that it immediately brings me to the **ASH ram disk shell**. No graphical interface or X, just a shell. What's the problem here? I tried this same guide with both Ubuntu *and *KUbuntu. Same problem.

---

### Post by solarwind on 2008-02-06
Bump.

---

### Post by jan quark on 2008-02-06
just food for thought

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

---

### Post by Tannster on 2008-02-06
I just joined the forum to contribute as of today so I'm not a super forum user yet but I may be able to help.

Which version are you installing with?
Also dont use the alternate iso's to put on the usb drive.

I've never had the alternates work for me.

---

### Post by solarwind on 2008-02-06
I tried the latest Ubuntu and KUbuntu i386 desktop isos.

---

### Post by solarwind on 2008-02-06
> **jan quark said:**
> just food for thought

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

I looked at that before but I thought it's for a "persistant" type of install where you use your usb drive as a mini ubuntu installation and not an "install to pc from usb" type of thing.

---

### Post by Tannster on 2008-02-06
> **jan quark said:**
> just food for thought

[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

Beat me to it.

I would suggest going through this first and see if you can actually get it to boot up, thus comfirming that it mounts and gives you a gui.

---

### Post by solarwind on 2008-02-06
> **Tannster said:**
> Beat me to it.

I would suggest going through this first and see if you can actually get it to boot up, thus comfirming that it mounts and gives you a gui.

One problem. I don't have Linux on any of my computers. I only have winbloze.

---

### Post by solarwind on 2008-02-06
Bump.

---

### Post by solarwind on 2008-02-07
Bump.

---

### Post by wanfahmi on 2008-02-07
If you followed the USB guides, It'll tell you to create/copy syslinux.cfg.
Unfortunately, they don't tell you to delete the isolinux.cfg.

Just run
cd /media/Your_USB_Drive
rm isolinux.cfg

I've had the same issue. I'm currently, using Ubuntu on USB drives. Give this a try. Backup isolinux.cfg. OK?

I'm using this guide.
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

---

### Post by solarwind on 2008-02-07
> **wanfahmi said:**
> If you followed the USB guides, It'll tell you to create/copy syslinux.cfg.
Unfortunately, they don't tell you to delete the isolinux.cfg.

Just run
cd /media/Your_USB_Drive
rm isolinux.cfg

I've had the same issue. I'm currently, using Ubuntu on USB drives. Give this a try. Backup isolinux.cfg. OK?

I'm using this guide.
[http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

But I ***renamed*** isolinux.cfg to syslinux.cfg. This should work...

---

### Post by solarwind on 2008-02-07
The problem is, **I don't have a CD rom drive and I can't put one in. At all.** So I can't even boot from the livecd to do this.

---

### Post by Licurgo on 2008-02-08
Solarwind:
You wrote:
**One problem. I don't have Linux on any of my computers. I only have winbloze**

If you follow the instructions in pendrivelinux: [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

you can see that in step 3, says:

1. Grab the Ubuntu 7.10 ISO and burn it to a CD
2. Insert the CD and your USB flash drive
3. Reboot your computer into Ubuntu from the Live CD

So, this tutorial is in linux environment, you don't need windows to install ubuntu in your USB

If you don't have a cdrom, can you get one external cdrom or you can borrow it?

Good luck:lolflag:

---

### Post by solarwind on 2008-02-08
> **Licurgo said:**
> Solarwind:
You wrote:
**One problem. I don't have Linux on any of my computers. I only have winbloze**

If you follow the instructions in pendrivelinux: [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

you can see that in step 3, says:

1. Grab the Ubuntu 7.10 ISO and burn it to a CD
2. Insert the CD and your USB flash drive
3. Reboot your computer into Ubuntu from the Live CD

So, this tutorial is in linux environment, you don't need windows to install ubuntu in your USB

If you don't have a cdrom, can you get one external cdrom or you can borrow it?

Good luck:lolflag:

That is the other problem. I don't have a CD rom drive, or space for another drive on my motherboard. I also don't think that it can boot from a USB one.

---

### Post by Licurgo on 2008-02-08
Solarwind:
How many USB ports do you have?, if you have one you can just insert an external CD and your problem resolved
:)

---

### Post by solarwind on 2008-02-08
> **Licurgo said:**
> Solarwind:
How many USB ports do you have?, if you have one you can just insert an external CD and your problem resolved
:)

My computer can't boot from USB ;)

---

### Post by wanfahmi on 2008-02-10
May be you can try this

Install as per persistant. then during bootup, select Live 'CD' mode.
From there you can install from USB. the install icon would be on the desktop

---

### Post by solarwind on 2008-02-10
> **wanfahmi said:**
> May be you can try this

Install as per persistant. then during bootup, select Live 'CD' mode.
From there you can install from USB. the install icon would be on the desktop

But installing as persistent means you still need a Linux CD to make the bootable USB stick...

---

### Post by wanfahmi on 2008-02-10
After renaming isolinux.cfg to syslinux.cfg, did you edit it?

I have been thrown to ASH during boot up before. The problem was, it was booting using isolinux.cfg and not syslinux.cfg.

Anyway

I suspect 2 things.
1. syslinux.cfg is not pointing to the correct files.
2. Some files are not copied correctly, (in the wrong place)
(I think some steps you've done correctly, since you go ASH)

I'm assuming you are using Gutsy.
I'm also assuming, you've mounted/extracted Ubuntu image to a directory.
I'm assuming sysconfig.exe works since I have never used it.

1. Format the USB stick.(FAT 16)
2. run syslinux.exe (syslinux will create a hidden file ldlinux.sys)
3. Copy files into the USB stick (All these files must  be in the correct places to work
[LIST]
[*]Copy these **folder** to USB stick root: casper disctree dists install pics pool preseed .disk
[*]Copy ALL files in **isolinux folder** to USB stick root
[*]Copy initrd.gz and vmlinuz in **casper folder** to USB stick root
[*]Copy md5sum.txt README.diskdefines ubuntu.ico to USB stick root
[*]**Rename** isolinux.cfg to syslinux.cfg
[/LIST]

Open up syslinux.cfg. Delete everything in it
Copy and paste this into syslinux.cfg 

```

DEFAULT vmlinuz
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=/preseed/ubuntu.seed boot=casper initrd=initrd.gz quiet splash --
LABEL live
  menu label ^Start Ubuntu in Live mode
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper initrd=initrd.gz quiet splash --
LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper xforcevesa initrd=initrd.gz quiet splash --
LABEL driverupdates
  menu label Install with driver ^update CD
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper debian-installer/driver-update=true initrd=initrd.gz quiet splash --
LABEL oem
  menu label ^OEM install (for manufacturers)
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper oem-config/enable=true initrd=initrd.gz quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel vmlinuz
  append  boot=casper integrity-check initrd=initrd.gz quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel /install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

```

Optional:
Edit isolinux.txt. Change the word CD to USB

That's it. Try this out.

---

### Post by solarwind on 2008-02-10
> **wanfahmi said:**
> After renaming isolinux.cfg to syslinux.cfg, did you edit it?

I have been thrown to ASH during boot up before. The problem was, it was booting using isolinux.cfg and not syslinux.cfg.

Anyway

I suspect 2 things.
1. syslinux.cfg is not pointing to the correct files.
2. Some files are not copied correctly, (in the wrong place)
(I think some steps you've done correctly, since you go ASH)

I'm assuming you are using Gutsy.
I'm also assuming, you've mounted/extracted Ubuntu image to a directory.
I'm assuming sysconfig.exe works since I have never used it.

1. Format the USB stick.(FAT 16)
2. run syslinux.exe (syslinux will create a hidden file ldlinux.sys)
3. Copy files into the USB stick (All these files must  be in the correct places to work
[LIST]
[*]Copy these **folder** to USB stick root: casper disctree dists install pics pool preseed .disk
[*]Copy ALL files in **isolinux folder** to USB stick root
[*]Copy initrd.gz and vmlinuz in **casper folder** to USB stick root
[*]Copy md5sum.txt README.diskdefines ubuntu.ico to USB stick root
[*]**Rename** isolinux.cfg to syslinux.cfg
[/LIST]

Open up syslinux.cfg. Delete everything in it
Copy and paste this into syslinux.cfg 

```

DEFAULT vmlinuz
GFXBOOT bootlogo
GFXBOOT-BACKGROUND 0xB6875A
APPEND  file=/preseed/ubuntu.seed boot=casper initrd=initrd.gz quiet splash --
LABEL live
  menu label ^Start Ubuntu in Live mode
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper initrd=initrd.gz quiet splash --
LABEL xforcevesa
  menu label Start Ubuntu in safe ^graphics mode
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper xforcevesa initrd=initrd.gz quiet splash --
LABEL driverupdates
  menu label Install with driver ^update CD
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper debian-installer/driver-update=true initrd=initrd.gz quiet splash --
LABEL oem
  menu label ^OEM install (for manufacturers)
  kernel vmlinuz
  append  file=/preseed/ubuntu.seed boot=casper oem-config/enable=true initrd=initrd.gz quiet splash --
LABEL check
  menu label ^Check CD for defects
  kernel vmlinuz
  append  boot=casper integrity-check initrd=initrd.gz quiet splash --
LABEL memtest
  menu label ^Memory test
  kernel /install/mt86plus
  append -
LABEL hd
  menu label ^Boot from first hard disk
  localboot 0x80
  append -
DISPLAY isolinux.txt
TIMEOUT 300
PROMPT 1
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt

```

Optional:
Edit isolinux.txt. Change the word CD to USB

That's it. Try this out.

This worked PERFECTLY! Thank you SO MUCH! Very simple and easy to follow guide and worked VERY WELL! I was able to boot into it very quickly and easily and install faster than ever! I even managed to play a chess game with the computer while it was installing. Flawless! This needs to go into the wiki for sure!

---

### Post by wanfahmi on 2008-02-11
Glad to hear it helped. I'm a noob 1 month into Ubuntu, just giving back to the community.

---

