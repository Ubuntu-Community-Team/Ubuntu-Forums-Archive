---
title: "How to restore grub after Windows overwrite it? major crisis..."
date: 2014-05-20
forum: Installation &amp; Upgrades
---

### Post by goghvv on 2014-05-20
Hi.
I used to run both Windows and Ubuntu in a dual boot mode, where I get to choose which OS I want to load whenever the computer boots up.
I recently had to reinstall my Windows 7, but unfortunately, the Windows installation overwrote the MBR, and now I can't access my Ubuntu through grub.
So I loaded Ubuntu thorugh a flash drive ('Live CD mode'), to try to reinstall grub, and restore the MBR to what it used to be.
Problem is, when I run:
```
sudo apt-get install grub
```
through the terminal, it says:
```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
```
So I tried to run:
```
sudo apt-get update
```
Which used to help me in the past when came across these weird errors, but this time running ```
sudo apt-get update
``` never finishes (it gets stuck, and just "waiting for headers"), I suspect it has something to do with the fact that I only have 4 free MB left on my disc (I got this warning when Ubuntu was launched, for some reason).
Is there a way to restore the MBR through Windows?
Please, I am really desperate here and don't know what to do, I have REALLY important files on Ubuntu... :(

---

### Post by Bucky Ball on 2014-05-20
Have a look at Boot Repair. 

Follow instructions here booting from a LiveCD:

[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

More info:

Get Boot Repair:
[http://sourceforge.net/projects/boot-repair/?source=directory](http://sourceforge.net/projects/boot-repair/?source=directory)

Use BR:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

---

### Post by oldfred on 2014-05-20
From Live installer you cannot run updates as it is not updateable.

to manually reinstall grub you need to mount partition with Ubuntu (and /boot if separate partition) and install grub using that.

       #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub


 #More info here
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB 2

---

### Post by tgalati4 on 2014-05-20
Windows wiping your MBR is a common problem.  Fortunately there are tools to fix it:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Did you try to run the suggested fix?  

```
sudo dpkg --configure -a
```

Simply trying to update the apt database doesn't fix configuration problems.  If you have a package that is only partially configured, apt will have problems and let you know about it.

---

### Post by goghvv on 2014-05-20
OK, Now I cannot launch Ubuntu from the flash drive (after choosing "Try Ubuntu" all I get is black screen).
Can I repair it from Windows 7?

---

### Post by goghvv on 2014-05-20
YESSSSS!
I remounted the Ubuntu image disc to the flash drive, launched the live-cd again, and used the manual suggested by Bucky Ball's, and my baby is back!!!
Thank you so much!

---

### Post by Bucky Ball on 2014-05-22
Excellent news! ;)

Please mark the thread as solved to help future travelers.

---

