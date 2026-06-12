---
title: "How to install ubuntu 12.10 to an external hdd"
date: 2012-11-16
forum: Installation &amp; Upgrades
---

### Post by skiabox on 2012-11-16
I want to install ubuntu 12.10 to an external hdd.
How do I do that?
Thank you.

---

### Post by Mr_JMM on 2012-11-16
1. Connect hard drive.
2. Insert Ubuntu DVD.
3. Turn on computer.
4. Boot from DVD.
5. Select "Something Else" on the partition screen.
6. Follow installation directions selecting the External drive when asked where to install.
7. [This step provided by [Arpanaut]("http://ubuntuforums.org/member.php?u=45953")]: Install grub to the external drive. For explination, see arpanaut's post below.
8. Make a cup of tea. Sorry, make two, mine's strong, milk and a sugar.

Tips:
1. Create a separate home partition if not already.
2. If carrying the external drive around with you, encrypt the /home partition (see point 6 above).

---

### Post by arpanaut on 2012-11-16
Another point to remember is to install grub on to the external drive,
because if you install grub on to your internal HDD grub will be looking for the external 
and will not boot into any OS without the external being plugged in.

---

### Post by oldfred on 2012-11-16
Some screen shots to show the good  instructions by Mr_JMM and arpanaut. I have missed the where to install grub2's boot loader combo box on the install screen and had to restore a boot loader, so review the partition screen and particularly the where to install grub. Install to MBR of external drive (often sdb) not any partitions like sdb1 or sdb2.

Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Different versions have slight difference in install screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by efflandt on 2012-11-17
Unfortunately **12.10's grub is broken for external drives** at the moment, so you may have to edit /boot/grub/grub.cfg initially before first boot after install and any time the kernel or grub updates (any time grub-update is run) until grub is fixed.  And the 1st boot after installation will have 95 updates including a kernel.

Grub used to be able to find drives by UUID regardless of where they were, but the grub in 12.10 uses hardware drive definitions that break that when the drive is in a different hd# or achi# after installing from USB memory stick, or it ends up as hd0 when BIOS boots that device instead of the hd# or achi# grub set during grub-update.

The reason I know that is because I just installed 12.10 on a USB drive,  and it it booted to a grub prompt (not grub menu) because grub was  looking for hd7 where the drive was (sdh) above the USB stick during install.  But it is hd0 when BIOS boots it.  Then during those 95 updates including a kernel, grub changed it  to hd6 because it was sdg while Ubuntu was  running (without the USB stick), but is still hd0 when BIOS boots it.

Not very user friendly.  More of nuisance for those of us who know how to correct it, but possibly aggravating to new users.

---

### Post by oldfred on 2012-11-17
@efflandt
I had a similar issue when installing from one flash to another and drive number were like yours hd5 & hd6. But that was with grub 1.98.
Once fixed, I never had issue and I assumed it was that after a gap in drives the search function which is supposed to override the set root stopped searching. But never had issue again on any of my 4 drives and sometimes my flash it sda, sdc or sde, have not checked grub's enumeration to see what it says.
All I did was edit grub menu with e and change to hd0 when I next booted flash drive.

---

### Post by Dogbytes on 2013-04-23
does anyone know if grub was updated to fix this issue? i came across this thread while planning to install 12.10 to a thumbdrive or an external HDD. But it sounds more difficult than i thought. more reading on my end is needed i reckon.

---

