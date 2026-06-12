---
title: "/casper/vmlinuz file not found"
date: 2013-02-24
forum: Installation &amp; Upgrades
---

### Post by Lithdk on 2013-02-24
Hello all :)

I am trying to install "ubuntu-12.04.2-desktop-amd64" from a USB created with "Universal-USB-Installer-1.9.2.5". When I click anything in the boot menu (livecd, install, etc) it just says /casper/vmlinuz file not found. There is a "vmlinuz.efi" in the casper folder on the USB stick. I tried installing 12.10 which installs just fine, but I would like to have 12.04. From what I understand I need to change some files in the  /boot/grub part of the USB but I have no idea how that works.

From my research a lot of people have this problem and have gotten it solved, but the answers they've gotten is very encrypted when my knowledge of stuff like that is next to none.(e.g.: They say they cant install, post a ton of code, someone post a ton of code back and they say "thx, works". ) Also, in my research I have found this problem to be only for .04 LTS versions. Some other guys have problem with other versions, but not the "/casper/vmlinuz file not found" problem.

It does install correctly with wubi, but from what I can understand wubi isn't a "real" installation per se.

My regards, and thanks in advance
Lithdk
(Sorry for my english, not my first language.)

---

### Post by gordintoronto on 2013-02-24
Try using unetbootin to create the USB.

---

### Post by Lithdk on 2013-02-24
Already tried unetbottin and LiLi. And atleast 5 times with each usb creator.

But now I went with Linux Mint 14 cinnamon and it actually fills my needs 100% and I figure - since I read its 99% ubuntu - I can still get help from the ubuntu community in my startup period in linux :-) Already followed a few ubuntu guides in mint and so far it works perfectly.

---

### Post by omid2s on 2013-02-24
[FONT=Comic Sans MS][COLOR=DarkRed][SIZE=3]hello my dear friends
[/SIZE][/COLOR][/FONT]
I also had this problem.
but this problem isnt from unetbottin and LiLi
Maybe this problem from your usb memory
this problem 100% for transfer rate is slow
I disconnect usb and connect Again
and boot computer....and solved it

---

### Post by Lithdk on 2013-02-25
> **omid2s said:**
> [FONT=Comic Sans MS][COLOR=DarkRed][SIZE=3]hello my dear friends
[/SIZE][/COLOR][/FONT]
I also had this problem.
but this problem isnt from unetbottin and LiLi
Maybe this problem from your usb memory
this problem 100% for transfer rate is slow
I disconnect usb and connect Again
and boot computer....and solved it

Yeah I also tried that, but Im fairly certain it's a problem with the 12.04.2-desktop-amd64 install.

---

### Post by siguie on 2013-03-01
I think I might know thos one ... I don't know what the actual ubuntu problem is BUT I do know that when I set my BIOS to "Legacy OS" I have the same problem. However, when I set the BIOS to **UEFI** everything works fine.

Incidentally this problem isn't just with the installation or use of the Live USB, once installed if you set the BIOS back or mess up with Boot Repair {kinda why I know this} you will have the same issue.

On the plus side if your computer is relatively knew and has UEFI as an option it works great :guitar:

---

### Post by omid2s on 2013-03-01
hello my friends
I downloaded ubuntu 12.04 lts DVD 32bit and
64amd(ubuntu 12.04 64bit DVD) hasnt problem to load.
and create Live usb with pendrive.
frist this error shown.
but I restart computer and unplug usb memory
and quichly plug usb memory and run ubuntu 12.04.

---

### Post by eminemix on 2013-03-03
I have the same issue using "Universal-USB-Installer-1.9.2.5" trying to install 13.04.

Never had this. I guess that iso is broken.

Check [this](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1077388) out!

---

### Post by wordimx on 2013-03-04
> **eminemix said:**
> I have the same issue using "Universal-USB-Installer-1.9.2.5" trying to install 13.04.

Never had this. I guess that iso is broken.

Check [this](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1077388) out!

Hi there,

I'm a Linux newbee too, but in seems that the file /caspar/vmlinuz has the file extension .efi in the 64bit 12.04 edubuntu version.

I removed the extension and the installation seems to work now. I got an error during the installation but I think that might be because of my harddrive.
The MD5 checksum is ok for the image, so I guess the issue is with the ISO.

:)

---

### Post by newjorkcity on 2013-04-04
> **Lithdk said:**
> Hello all :)

I am trying to install "ubuntu-12.04.2-desktop-amd64" from a USB created with "Universal-USB-Installer-1.9.2.5". When I click anything in the boot menu (livecd, install, etc) it just says /casper/vmlinuz file not found. There is a "vmlinuz.efi" in the casper folder on the USB stick. I tried installing 12.10 which installs just fine, but I would like to have 12.04. From what I understand I need to change some files in the  /boot/grub part of the USB but I have no idea how that works.

From my research a lot of people have this problem and have gotten it solved, but the answers they've gotten is very encrypted when my knowledge of stuff like that is next to none.(e.g.: They say they cant install, post a ton of code, someone post a ton of code back and they say "thx, works". ) Also, in my research I have found this problem to be only for .04 LTS versions. Some other guys have problem with other versions, but not the "/casper/vmlinuz file not found" problem.

It does install correctly with wubi, but from what I can understand wubi isn't a "real" installation per se.

My regards, and thanks in advance
Lithdk
(Sorry for my english, not my first language.)


I also had this problem exept I put the file I downloaded into an ISO converter and it said it was like version 13.0.0. It was indeed weird:confused:

---

