---
title: "GRUB2 and large USB Drive"
date: 2019-10-30
forum: Installation &amp; Upgrades
---

### Post by kmand on 2019-10-30
I'm trying to get a live ubuntu flash drive to chainload a grub2 boot from an 8TB usb disk. The grub2 commandline sees the usb disk as (hd0) but can't read any partition info. The disk is GPT partitioned.

If I let the live ubuntu boot from the flash drive, it can perfectly well see the  8TB disk and mount its partitions. It just can't do it from grub2. 

Any ideas on how to fix this?

---

### Post by yancek on 2019-10-30
Since you are using a 'live' Ubuntu usb, the only way you could do this would be to boot the usb and hit the 'c' key to be able to enter the separate lines needed to boot the other system.  The 'live' Ubuntu is read-only so putting an entry in its grub.cfg would be pointless as the change is lost on reboot.  Is the GPT disk an EFI install?  What OS is on it that you are trying to boot?  You might try running:  sudo update-grub on the 'live' system to see if the other OS on the drive is picked up.  Of course you would need to then either print out the menuentry for it from grub.cfg on the 'live' usb or write it down somewhere to enter when you boot. 

If you have grub2 install on the 8tb drive, you should be able to also use a configfile entry.  Lots of examples of this if you do a search here or online.  This would also need to be manually entered.

---

### Post by oldfred on 2019-10-30
Grub2 has chainload, often used to boot Windows. And it has a configfile which allows one grub to boot another grub so you have full menu from second install.
I believe the version of grub in the installer is limited and only had the parts of grub that it needs to boot the install. It is not the full grub, so not everything may work.

I almost always now keep ISO on hard drive and use grub2's loopmount to boot the ISO directly. 

I used to install a full versions of grub to flash drive and use loopmount to boot several ISO on a medium size flash drive. But now with larger flash drives (over 16GB) I just do a full install. I may use it to store data on rest of drive, also have ISOs,  but often edit 40_custom to boot internal drive (even if not totally correct configuration, often easier to edit that just using grub's command line).
You can install full grub to a flash drive and create your own grub.cfg to boot anything. And that only needs an ESP if UEFI or MBR & one small partition for grub if BIOS.

What installs are on 8TB drive?

Post this:
sudo parted -l
lsblk -f

---

