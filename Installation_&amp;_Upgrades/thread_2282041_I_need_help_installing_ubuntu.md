---
title: "I need help installing ubuntu"
date: 2015-06-11
forum: Installation &amp; Upgrades
---

### Post by ramon.nordo on 2015-06-11
First I want to say that I never had linux on any of my PCs before but i was trying to install it on a laptop i had lying around.

The Laptop is currently running Windows 8.1 and everytime i try to install ubuntu (15.04) with my bootable usb stick (used this method [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) ) I'll get the purple loading screen with "ubuntu" written on it but after that just this [http://i.imgur.com/caNJKnJ.jpg](http://i.imgur.com/caNJKnJ.jpg)

What am i supposed to do?

---

### Post by QIII on 2015-06-11
Hello!

Could you describe exactly what you are doing, step by step, in the process of trying to install?

---

### Post by oldfred on 2015-06-11
While it should boot in BIOS mode, if Windows is UEFI and all Windows 8 systems are UEFI, you need to boot flash drive in UEFI mode not CSM/BIOS/Legacy or whatever your system calls it.
       
Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Did you check that download was correct? It seems to have issues booting flash drive.
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

How to create a bootable Ubuntu USB Flash Drive - unetbootin
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

   Usb installer from Windows - pendrive may not work with UEFI
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

---

