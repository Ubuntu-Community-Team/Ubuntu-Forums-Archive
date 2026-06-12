---
title: "Moving Ubuntu HD from secondary to primary."
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by Mark_C on 2010-01-18
Currently I am running Ubuntu 9.10 on an older P4 system with EIDE harddrives.  My primary HD has a WinXP installation and GRUB.  Ubuntu is installed on the secondary HD.

I am happy enough running Ubuntu that I would like to remove my WinXP disk, move the disk with Ubuntu on it to be the primary boot drive, and then install a new drive as the secondary.  

However when I tried to simply move the drive with Ubuntu on it from the secondary to the primary EIDE position the system would not boot.  I assume that this is because there is no boot loader currently on that drive.

So my question is how do I put GRUB on the Ubuntu drive so that it can become the boot drive?  Or is there some other way to accomplish what I am after without having to reinstall Ubuntu?

Mark

---

### Post by oldfred on 2010-01-18
From a working Ubuntu you can install grub2 to another drive:

sudo dpkg-reconfigure grub-pc
this will also give several menus for special startup commands in the grub file, if no commands are required you can just accept each page until it asks which drive to install to.

or

reinstall to sda, change to sdb, sdc etc
sudo apt-get install --reinstall grub-pc
sudo grub-install /dev/sda 
If that returns any errors run: 
grub-install --recheck /dev/sda

or from a liveCD

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) 
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by Mark_C on 2010-01-18
> **oldfred said:**
> From a working Ubuntu you can install grub2 to another drive:

sudo dpkg-reconfigure grub-pc
this will also give several menus for special startup commands in the grub file, if no commands are required you can just accept each page until it asks which drive to install to.



That looks straight forward enough.  I assume that having GRUB installed on more than one drive in a system is not going to muck anything up, true?  

Thanks for the quick reply.  Soon as I do a backup of my Ubuntu data I'll give this a shot.

Mark

---

### Post by Mark_C on 2010-01-19
I tried the command "sudo dpkg-reconfigure grub-pc" but it came back with the message "Package 'grub-pc' is not installed and no information is available".

I checked the version of grub on my system and it is 0.97.  I think when I upgraded from Ubuntu 9.4 to 9.10 I may not have upgraded grub.  

I'm new to this stuff and don't want to zorch my Ubuntu drive.  Would it be safest to DL the live cd, swap out my HD's, boot off the live cd and install grub from there?

Thanks for any advice.

Mark

---

### Post by oldfred on 2010-01-20
Sorry, I sw 9.10 and assumed (big mistake) that it was a new install. Upgrades do have grub legacy (0.97) unless you separately upgrade that also.
Most of the instructions use a liveCD but you can do it from your working system:
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd1,6) or root (hd0,6) Look at output from #4 use (hdx,6)
6. Type setup (hd0) where hd0 is drive sda or hd1 is drive hd1.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Follow instructions for 9.04 as that is for old grub where 9.10 is grub2.

---

