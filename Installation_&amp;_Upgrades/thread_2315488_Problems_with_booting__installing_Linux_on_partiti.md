---
title: "Problems with booting / installing Linux on partitions."
date: 2016-02-29
forum: Installation &amp; Upgrades
---

### Post by laisut on 2016-02-29
Hi. There is the situation:
I have an SSD drive and windows installed on it. I have HDD with few partitions (all of them contain vital data for my work). I left about 100GB free (unallocated) space for Linux installation. I boot the installer from USB flash drive, choose option "something else", then create an EXT4 partition for Linux installation and Swap partition for Linux-swap area. (Everything is done in installation menu). Then there is option - "Device for boot loader installation" here i select to install this boot loader to the same EXT4 partition where my Linux will be installed. After done installing Linux prompts a message to restart the mashine now. I press the restart button - everything froze. Couldn't click anything, just had to force shutdown by removing batery. After in BIOS i select to boot from HDD it does not boot but boots from second option - SSD where my windows is installed. What did i do wrong? What are solutions to get Linux booting and not freezing after shutdown?

---

### Post by grahammechanical on 2016-02-29
> What did i do wrong?

This

> Then there is option - "Device for boot loader installation" here i  select to install this boot loader to the same EXT4 partition where my  Linux will be installed.

You should select to install the Grub boot loader to the hard drive (not the SSD). And then use the BIOS setting utility to set the motherboard to load from the hard drive and not the SSD. You should then get a menu that will offer to load either Ubuntu or Windows.

Regards.

---

### Post by laisut on 2016-02-29
Thank you. But installing boot loader on entire HDD will not wipe out my data?

---

### Post by oldfred on 2016-02-29
No. 
Boot loader with MBR is just a tiny amount of code in the MBR which is only the very first sector of a drive. That code then loads more code to fully boot.

All BIOS systems boot from MBR, newer UEFI use an ESP - efi system partition where all systems install boot code.

You can use Boot-Repair to reinstall grub to MBR. Best to use advanced mode and fully uninstall/reinstall grub. If you just put grub in MBR, it may have a setting on original install location and use that on major update. Then later you have issues again.

You can install this into your Ubuntu live installer in live mode.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by laisut on 2016-02-29
Thank you very much! I think the easiest way will be to reinstall Linux.

---

### Post by laisut on 2016-02-29
Im getting another issue. Whenever my installation reaches the creation of ext4 partition it keeps runing forever. What im doing again wrong ?

---

### Post by oldfred on 2016-02-29
If you already have the ext4 partition, are you not just selecting it and reformatting.
Or are you using an auto install option, best to use Something Else and just select/choose existing ext4 partition for install.

---

### Post by laisut on 2016-03-01
Thank you. Just restarted the installation. How do i close / delete this topic (thread) now ? Or move to "
solved" ?

---

### Post by oldfred on 2016-03-01
To change to solved see my signature below. (last line)

---

