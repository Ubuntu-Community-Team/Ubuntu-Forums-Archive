---
title: "install bootable live USB for Ubuntu 13.04 with linux"
date: 2013-04-29
forum: Installation &amp; Upgrades
---

### Post by raxman on 2013-04-29
I installed Ubuntu 13.04 on my USB stick using Universal USB Installer in Windows.  This worked fine and I was able to boot.  However, I destroyed my Windows installation (trying to install Ubuntu) and I don't have a working windows system at home currently.  I have tried using Unetbootin to install "ubuntu-13.04-desktop-amd64.iso", however, it does not boot.  I can seem the files are there.  I download a new image in case it was corrupt but that made no difference.  I can install "linuxmint-14.1-mate-dvd-64bit.iso" with Unetbootin (and Manjaro) and it boots fine.  Is there something special about Ubuntu 13.04?  I have also tried the dd command but that never gives a booting USB.

---

### Post by raxman on 2013-04-30
Strange, kubuntu-13.04-desktop-amd64.iso installs and boots just fine on my USB.  I tried ubuntu-13.04-desktop-amd64.iso again just to make sure and it still fails to boot.

---

### Post by nuffa on 2013-05-01
I'm having the same problem. I've been using unetbootin for a long time  with no problems. But with 13.04 iso, when I boot from usb it says  "Operating system wasn't found". :(

---

### Post by raxman on 2013-05-01
It works fine with Universal USB Installer in Windows though.  Also Kubuntu 13.04 install to USB and boots fine with unetbootin.  It's a bit ironic that I need to use Windows to install Ubuntu 13.04 on the USB but I don't have windows anymore because Ubuntu 13.04 turned my system into a blinking pointer...two more days of effort and still no luck.

---

### Post by sudodus on 2013-05-01
Please describe your computer: as much as possible, but at least desktop/laptop/netbook/, cpu, ram, graphics chip/card. This make it easier to give good advice.

What BIOS/UEFI system is it, and what Windows version?

I have been able to make USB boot drives with Unetbootin as well as with dd and usb-creator-kde during the testing period of Raring (13.04).

---

### Post by raxman on 2013-05-01
All the details of my system can be found in this post
[http://ubuntuforums.org/showthread.php?t=1927626](http://ubuntuforums.org/showthread.php?t=1927626)

OCZ 120 GB Vertex 3 SATA III 6.0 Gb-s 2.5-Inch Solid State Drive 
EVGA GeForce GTX 590 Classified 3072 MB PCI Express 2.0 
ASUS LPCIe 3.0 and UEFI BIOS P8Z68-V PRO/GEN3
Samsung Blu-Ray Combo Internal 12XReadable and DVD-Writable Drive with Lightscribe SH-B123L/BSBP
Intel Core i7-2600K 3.4 GHz 8 MB Cache Socket LGA1155 Processor
Corsair Vengeance Blue 16 GB PC3-12800 1600mHz DDR3 240-Pin SDRAM Dual Channel

Why does Kubuntu 13.04 install and not ubuntu 13.04 on the USB with unetbootin?

---

### Post by sudodus on 2013-05-01
That's new hardware, and it should certainly be able to run any flavour of Ubuntu. The only reason Unetbootin would work with Kubuntu but not Ubuntu, is some minor bug in Ubuntu or Unetbootin, or that one of the softwares is not up to date. But if you clone the iso file to the USB drive with dd, it should definitely work, if the iso file is good. I've done it a lot of times. Did you check with md5sum, that the download was successful?

Furthermore, are you using up-to-date iso files, the released version, or old alpha or beta testing versions from February?

- Is Windows 7 installed with UEFI?
- Is 'secure boot' on?

I suggest that you follow the suggestion by YannBuntu in the other thead, and report the result.

---

### Post by raxman on 2013-05-01
Thank you for your reply.  
I did md5sum ubuntu-13.04-desktop-amd64.iso and it reported a hash value that is not on the webpage
[https://help.ubuntu.com/community/UbuntuHashes#A13.04](https://help.ubuntu.com/community/UbuntuHashes#A13.04)

I downloaded the iso again and checked the hash and it matches the one on the webpage.  Now it boots.  Another problem solved!  Thank you!  Lucky, it's May 1st and I have the day off.  I might get this all working by the end of the day.

---

### Post by sudodus on 2013-05-01
I glad that I could help you :-)

---

### Post by nuffa on 2013-05-01
> **raxman said:**
> It works fine with Universal USB Installer in Windows though.  Also Kubuntu 13.04 install to USB and boots fine with unetbootin.  It's a bit ironic that I need to use Windows to install Ubuntu 13.04 on the USB but I don't have windows anymore because Ubuntu 13.04 turned my system into a blinking pointer...two more days of effort and still no luck.

I was also able to get it working using Universal USB Installer [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) :)
I've actually been trying to do it on Windows. So going for an alternative of unetbootin was going to be the solution and it worked.

---

