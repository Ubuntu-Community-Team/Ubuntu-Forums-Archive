---
title: "Get rid of dual boot"
date: 2011-01-15
forum: Installation &amp; Upgrades
---

### Post by Bo0ddha on 2011-01-15
I currently have 10.10 and 10.04 installed and dual booted.  I want to remove 10.10.  Looking at the drive partitioning the 10.10 is the one with the boot flag.  I also am worried about just formatting it and loosing the bootloader.  Don't care about joing the partitions or anything just would like to remove 10.10.  Not sure about the correct way to go about removing 10.10 and not wiping grub out completely.

---

### Post by fuzzyworbles on 2011-01-15
boot up with ubuntu on a usb or live cd, run gparted and change the boot flag to the other root partition. then remove the partition you don't want and expand what's left the fill the space (if that's your plan). you'll then have to reconfigure grub2 to to point to the partition where /boot/grub resides. for that, search for "reinstall grub2" on this forum. that'll be done also with your live usb or cd. 

OR

you could reconfigure grub2 while booted into the partition you wish to keep, then boot using the live usb or cd to do change the boot flag and partition wrangling. this might be the easier option, because reconfiguring grub using a live usb/cd can sometimes be confusing.

in the end, "dual-boot" will still be present. meaning, that you'll still see the grub menu when starting. to change this, just edit /default/grub and make the timeout 0 and hidden.

---

### Post by wilee-nilee on 2011-01-15
The boot flag means nothing in Ubuntu. All you have to do is in the OS you want to keep 10.04, in the terminal run these two commands.
sudo grub-install /dev/sda
then sudo update-grub.

This will put Lucid in charge of the boot and you can remove the bootflag altogether and Maverick. If you once again after 10.10 is removed run 
sudo update-grub 
Maverick will be off the grub menu list and you will boot in without seeing the grub menu, unless you hold down the shift key when powering on.

---

### Post by Bo0ddha on 2011-01-15
ok This is what I get from sudo update-grub


Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-27-generic
Found initrd image: /boot/initrd.img-2.6.32-27-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done


Why does it find 2 images?

---

### Post by wilee-nilee on 2011-01-15
> **Bo0ddha said:**
> ok This is what I get from sudo update-grub


Generating grub.cfg ...
**Found linux image: /boot/vmlinuz-2.6.32-27-generic**
Found initrd image: /boot/initrd.img-2.6.32-27-generic
**Found linux image: /boot/vmlinuz-2.6.32-24-generic**
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
done


Why does it find 2 images?

Those are two kernel sets, generally the second one is a backup in case the first one fails.

---

### Post by drs305 on 2011-01-15
The two items are two kernels in the same release. As a newer kernel is installed, the older kernel is retained on the system and in the menu.

Many users keep a backup kernel they know works as insurance. If you really want to physically remove the kernel, and thus remove it from the menu, you can refer to this link on how to do it. Hint: Ubuntu Tweak...
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

---

