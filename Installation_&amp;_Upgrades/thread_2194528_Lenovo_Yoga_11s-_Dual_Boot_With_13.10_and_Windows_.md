---
title: "Lenovo Yoga 11s- Dual Boot With 13.10 and Windows 8 Pre-Installed Black Screen"
date: 2013-12-19
forum: Installation &amp; Upgrades
---

### Post by akanksha.dlf on 2013-12-19
I am a complete newbie to ubuntu installation. I have a Lenovo Yoga 11s with the following specs

CPU- Intel i3-3229Y 1.4G
RAM-4G
SSD 128 GB
OS Win 8 Em 

I have made my Live USB using Rufus to burn a bootable USB from ubuntu-13.10-amd64.iso file

I shrunk my windows partition and created an unpartitioned space of 39 GB using disk mangement of windows 8.

I disabled fast-startup in the power options of control panel in Windows. Then in the UEFI settings I disabled Secure Boot and Fast Boot. Enabled USB Boot
The Boot Mode is UEFI (options were lagacy/UEFI)
I booted the PC with USB and got to the grub menu with options Try ubuntu without installing and Install ubuntu etc. Whenever  i select any  of these 2 i get a completely black screen where i can do nothing. I have to ultimately use the power button to switch off.

---

### Post by therealslamo on 2013-12-19
Firstly, you should look around the forums--this has been answered elsewhere. Also, you may not have wifi working out of the box... Follow this guide for wireless: [http://sudomasochism.com/post/55464266362/installing-ubuntu-linux-on-a-lenovo-yoga-11s](http://sudomasochism.com/post/55464266362/installing-ubuntu-linux-on-a-lenovo-yoga-11s)

With the screen turning black, try hitting F11 or F12 (screen brightness up and down)... if that doesn't correct the problem, Check this forum (plus there is plenty of great info in this forum--as well as many other questions you may have--there are posts geared for newbies): [http://ubuntuforums.org/showthread.php?t=1911972&](http://ubuntuforums.org/showthread.php?t=1911972&)

Good luck!

---

### Post by oldfred on 2013-12-19
@akanksha.dlf
Are you booting with UEFI or BIOS. If you have Windows and want to dual boot you need to install Ubuntu in the same boot mode.

If BIOS at tiny icons (accessiblity screen) you press any key and then f6. If booting with UEFI you get a standard grub menu and use e for edit scroll to linux line and replace quiet splash with boot option like nomodeset or acpi=vendor.

How you boot install media, UEFI or BIOS is how it installs:
 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

      
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by akanksha.dlf on 2013-12-19
Thanks for replying.i did look around the forum. I however could not find anything that answered my problem. The screen brightness keys do not help i have already tried that. There was a post on one forum that answered my problem which i cannot find again which said edit the grub options by pressing e and adding kernel nomodeset and acpi=vendor but wasnt very clear about exactly what to and where to type this.(forgive me but i am new to command line i have only used computer applicatio s and web for recreation previously(i am a freshman in a computet programming course and i really need ubuntu fr studies therefore desperate)). 

so the forum mentioned above talks about yoga 13 not 11s.  The 11s i have is the i3 version. 
People in the forum installed 12.04 version should i try that?

---

### Post by oldfred on 2013-12-19
Moved my post from other thread.

---

