---
title: "[SOLVED] Kubuntu won't boot"
date: 2005-09-04
forum: Installation &amp; Upgrades
---

### Post by Stolea on 2005-09-04
Hi all,
My rig has 
2.8g Prescot processor
2g ram
ATI 256 9600 Raedon Graphics Card
Pioneer DVD rom
Liteon DVD burner
1 x IDE 200g master (logical) 1 partition NTFS (Data only)
1 x SATA (1) 200g 2 partitions
Primary, active, (WIN XP Pro) 20g NTFS
logical (data) 180g NTFS
1 x SATA (2) 200g 2 partitions
primary, active, Kubuntu 504 188g EXT3
logical (swapspace 2) 2.6g

The bios boot sequence is set for 
1.)  sata 1 (WinXP)
2.)  sata 2 (Kubuntu)
3.)  ide drive

I installed Kubuntu without any hitches. At the end it asked if I wanted to install the boot manager (GRUB), which I said yes to (Default). It had recognized that WinXP was present.
After the installation completed it rebooted straight back into Windoze. No bootmanager.
I changed the bootsequenze in the bios and was greeted with a black screen with a cursor blinking at me.
So now I have a perfectly functional WinXP but no Kubuntu.
Any brilliant ideas whats gone haywire?
Cheers

---

### Post by tonym on 2005-09-04
Where did you specify grub should be installed?

---

### Post by Stolea on 2005-09-04
[QUOTE=tonym]Where did you specify grub should be installed?[/QUOTE]
 Didn't see where it asked??? When does that happen?
Just went through the install again with exactly the same result again. At no time was there an option where grub should be instaled, only if it was to be installed or not. 
Grub instal found 2 instances of winXP. 1 being the real one and one being a hidden backup incase things go pearshaped (which they frequently do)
Any more ideas ](*,)

---

### Post by mlomker on 2005-09-04
You'll need to boot into linux from a CD--Knoppix or whatever you have.  Once you are at a command line, this should work:

grub
grub> root (hd1,0)
grub> setup (hd0)
grub> quit

[Instructions](http://www.ubuntuforums.org/showthread.php?t=24113) (look at post #2) but your entries will be as above, from what you've described.

Hopefully it'll detect Windows for you and add it to the boot menu.  If not then you'll have to look at your /boot/grub/menu.lst file and add a few lines for the Windows selection.  It'll be something like:

Title Windows XP
rootnoverify (hd0,0)
chainloader +

---

