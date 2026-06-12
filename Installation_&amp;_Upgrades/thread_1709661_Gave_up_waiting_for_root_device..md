---
title: "Gave up waiting for root device."
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by Celswolf on 2011-03-18
In the part of the installation the problem is that it does not recognize any hard drive. That problem was solved by pressing F6 in the menu of the CD and add the line pci = nomsi.
I installed the OS apparently.

Now restart the system, I get the white logo of ubuntu, the screen goes black, and hope but nothing happens. Until I touch a key and I get the following error:
> 
Gave up waiting for root device. Common problems: 
-Boot args (cat/proc/cmdline) 
-Check rootdelay = (did the system wait long enough?) 
-Check root = (did the system wait for the right device?) 
-Missing modules (cat/proc/modules; ls/dev) 
ALERT! /dev/disk/by-uuid/XXXXXXXXXXXXXXX does not exist. Dropping to a shell! 

BussyBox v1,13,3 (Ubuntu 1:1.13.3-1 ubunut 11) built-in shell (ash)


This is my computer:
> 
_CPU_ AMD Athlon 64, 2200 MHz (11 x 200) 3500+
_Motherboard_ Asus A8V-X (3 PCI, 2 PCI-E x1, 1 AGP, 4 DDR DIMM, Audio, LAN)
_Chipset_  VIA K8T800Pro, AMD Hammer
_Memory_ 1024 MB (PC2100 DDR SDRAM)
_Video Card_ NVIDIA GeForce2 MX/MX 400 (Microsoft Corporation) (64 MB)
_Hard Drive_ HDT722516DLA380 (160 GB, 7200 RPM, SATA-II)


Extra Info:
1] The bios only recognizes the hard drive if it is set to SATA
2] I'm installing from a disk completely formatted.
3] I go with the LiveCD to see the grub and it is empty, there is nothing written.

Original post (spanish)
[http://ubuntuforums.org/showthread.php?t=1709653](http://ubuntuforums.org/showthread.php?t=1709653)

---

### Post by Hakunka-Matata on 2011-03-18
He leido su Thread original.  I would recommend installing Release 10.04 or 10.10.  
> In the part of the installation the problem is that it does not  recognize any hard drive. That problem was solved by pressing F6 in the  menu of the CD and add the line pci = nomsi.
I installed the OS apparently.apparently?  Me siento confudido leyendo esa frasa.  Did you go through the whole installation procedure?, username, password, language, all that stuff?

---

### Post by cbowman57 on 2011-03-18
What filesystem is root on?

---

