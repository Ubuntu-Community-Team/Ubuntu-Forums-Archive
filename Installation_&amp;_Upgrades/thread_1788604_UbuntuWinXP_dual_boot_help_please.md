---
title: "Ubuntu/WinXP dual boot help please"
date: 2011-06-22
forum: Installation &amp; Upgrades
---

### Post by quinne on 2011-06-22
Hi everyone -- If one is going to dual boot Ubuntu and Win XP, I believe  I've read it's preferable to install XP first, then Ubuntu.  I wiped  Win 7 off of this laptop (couldn't stand it) and then installed Ubuntu.   I've now decided I want to dual boot with XP.  Is there a wiki  somewhere on how to accomplish this so as to not destroy my grub  bootloader?

Thanks for any hints, tips, etc you can provide.

---

### Post by oldfred on 2011-06-23
Windows will overwrite grub's bootloader in the MBR. You just have to reinstall it. Make sure you have a good liveCD of the same version of Ubuntu as you have installed.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

Windows will only install to a primary NTFS partition with the boot flag or to a blank drive where it can create a primary NTFS primary partition and make it active(boot flag).

---

### Post by quinne on 2011-06-23
Great info, oldfred, many thanks for laying that out so succinctly.  If I have any further questions, I'll let you know.  Thanks again.

---

