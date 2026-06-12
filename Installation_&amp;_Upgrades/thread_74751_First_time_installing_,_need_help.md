---
title: "First time installing , need help"
date: 2005-10-12
forum: Installation &amp; Upgrades
---

### Post by saadghauri on 2005-10-12
Hi , i have 2 operating systems installed on my pc (winxp and 2000). I want to install ubuntu over winxp. What i want to ask is will it mess up win200 in anyway ? thanks

---

### Post by aysiu on 2005-10-12
Know your partitions well and which one you want to erase. During a certain part of the installation process you'll be asked if you want to wipe out the entire hard drive or manually edit the partition tables. Pick the latter option and select the Windows XP partition to be reformatted as ext3 and mounted as /

---

### Post by skirkpatrick on 2005-10-12
It shouldn't but what may make things the easiest is to go into W2k and use it to delete your XP partition so that there's just a nice, unused chunk of hard drive available for Ubuntu.

---

### Post by saadghauri on 2005-10-12
Thanks a lot , i am going to install right now , hope nothing goes wrong , coz if the whole hard disk is formatted , I am in BIG trouble :???:

---

### Post by aysiu on 2005-10-12
[QUOTE=saadghauri]Thanks a lot , i am going to install right now , hope nothing goes wrong , coz if the whole hard disk is formatted , I am in BIG trouble :???:[/QUOTE] Just read the instructions very carefully. Do not say "yes" to just anything.

---

### Post by saadghauri on 2005-10-12
Any other place in the installation i might need help ??

---

### Post by aysiu on 2005-10-12
[QUOTE=saadghauri]Any other place in the installation i might need help ??[/QUOTE] If you're planning to dual boot, make sure you install Grub to the MBR.

---

### Post by skirkpatrick on 2005-10-12
It should be fairly painless.  I've setup a couple of systems, dual-booting from one disc and dual-booting with two discs.

---

### Post by saadghauri on 2005-10-12
[QUOTE=aysiu]If you're planning to dual boot, make sure you install Grub to the MBR.[/QUOTE]

Umm .. what ?? whats grub ? whats MBR :(

---

### Post by skirkpatrick on 2005-10-13
GRUB is the mechanism that allows you to select which OS you're going to boot.  MBR is the Master Boot Record.  It's what gets modified to use GRUB.  Basically, when you want to dual or triple-boot, install your Windows partitions first then install Linux.

---

### Post by saadghauri on 2005-10-13
Man ... i messed up .. grub installation failed so i selected lilo .. lilo didnt do anything about win2000 and my pc is going into linux directly .. i NEED to get win2000 back no matter what it takes ... win2000 is still on my pc .. just not showing on my boot .. pleeeeeez help me

---

### Post by skirkpatrick on 2005-10-13
See if this helps install grub for you: [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=reinstall+grub)

---

