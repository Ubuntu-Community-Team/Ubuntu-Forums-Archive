---
title: "Problems with UBUNTU 8.04 live CD"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by Sutukh19 on 2008-07-11
I would like to state first that I would like to dual boot XP and Ubuntu 8.04. I have done so previously on another system. The setup I am attempting install on is an ASUS M2A-VM 690G SB600. with Seagate 350G PATA HD. 2GB DDR/667 memory. The Live CD I am attempting install with is 8.04 x86-64. While loading I get the error "Buffer I/O error on device fd0, logical block 0" numerous times until it eventually locks up. There is no floppy disk drive. However I do have a SATA CD/DVD combo drive, and my SATA setting in the BIOS is set to IDE. I have tried numerous times and different ISOs and all is the same. I have googled and tried all manner of boot up options, and still no results. I am wondering is Ubuntu compatable with the setup that I have or is there something that I am missing?
Any help in this manner will be greatly appreciated!:(

Thanks in advance!

---

### Post by Pumalite on 2008-07-11
Try placing all_generic_ide at the end of the boot line.

---

### Post by Sutukh19 on 2008-07-11
I have just tried adding the line, and I am still getting the errors. Sorry, If I did  not mention this earlier in my original post, but the drive is completely empty fresh out of the box, I was trying to see if the live CD would at least boot, but I think I may need to install windows xp first!

---

### Post by Pumalite on 2008-07-11
I hope you formatted your drive first.

---

### Post by Sutukh19 on 2008-07-11
I am formating the drive now with the XP installation CD! I think that mat have been the problem.

---

### Post by Sutukh19 on 2008-07-12
Formatted the drive, installed XP and still NO joy with that error about buffer i/o on fd0..........I guess I will have to try another distro.

---

### Post by Sutukh19 on 2008-07-15
Well I got sick of trying Ubuntu. So I tried out Linux MInt 5 Elyssa. The live CD installed and recognized everything.
I successfully installed Mint in a Dual boot configuration with XP but however when I reboot, the computer goes straight into Windows XP. 
How Can I get my Grub to load at boot to select which operating system to load?
I have a single 320G hdd spilt as follows into seperate primary partitions:

/dev/hda1 (ntfs) 48GB Windows XP
/dev/hda2 (ntfs) 218GB Stuff
/dev/hda3 (extended) Used for Mint 5
_____/dev/hda7 (ext3) 10GB /Root
_____/dev/hda5 (ext3) 20GB /home
_____/dev/hda6 (swap) 1GB
While running the command "find /boot/grub/stage1" I get the results:
(hd0,6)

What does this mean?

On a previous system I have successfully dual booted Ubuntu and XP and It worked like a charm with a similar setup with a 120GB hdd split into WInXP/Stuff/Extended Partition with Ubuntu. On a Dell XPS m1330.

Any help in the matter will be greatly appreciated.

---

