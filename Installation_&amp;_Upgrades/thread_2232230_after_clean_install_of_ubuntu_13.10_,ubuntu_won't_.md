---
title: "after clean install of ubuntu 13.10 ,ubuntu won't boot,not dual booting"
date: 2014-06-30
forum: Installation &amp; Upgrades
---

### Post by e-rootsofmt-zion on 2014-06-30
i have a hp laptop with 3.6 gb ram, amd e-300 apu with radeon hd grafics x 2 processor , it came with windows 8 ,i'm not dual booting , windows is gone for good ,  I tried to install ubuntu (32 bit i386) via usb but wont boot off usb ,  just shows me files on the usb drive , so i switched from uefi to legacy in the bios and she booted fine and install went find but after restart she wont boot, all i get is a black screen that says-  minimal BASH-like line editing is supported ....grub version ...ect. So i booted off the usb again and installed boot-repair and hit the recommened repair button and when i reboot i get gparted instead of ubuntu , i guess boot-repair mounted the live cd that comes with ubuntu 13.10 cuz when i boot off the usb and hit the try ubuntu button  i see a gparted live cd between the system settings and the trash icons on the left vertical bar , so i had her erase the install of ubuntu and did another fresh install and i get the same -minimal BASH-like editing screen , this time instead of running boot-repair recommened repairs i had boot repair create a bootinfo summary  [http://paste.ubuntu.com/7726708/](http://paste.ubuntu.com/7726708/)   i hope this helps....if you need more info or if i posted this in the wrong place please let me know...

---

### Post by yancek on 2014-06-30
Your bootinfoscript output shows that Grub is installed to the master boot record and also shows the core.img and other boot files in the correct location.  The menuentry for Ubuntu in the grub.cfg file also looks good, correct partition and UUID.  Have you disabled Secure Boot in the BIOS as well as fastboot?

FYI:  Support for 13.10 will end in a month.

---

### Post by oldfred on 2014-06-30
Looks ok to me also, but with AMD video you may need a boot option. I really only know nVidia as that is what I have.

       [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

