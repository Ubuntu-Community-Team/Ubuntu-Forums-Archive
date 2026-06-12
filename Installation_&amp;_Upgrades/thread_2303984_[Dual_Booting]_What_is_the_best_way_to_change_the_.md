---
title: "[Dual Booting] What is the best way to change the default from within each OS?"
date: 2015-11-23
forum: Installation &amp; Upgrades
---

### Post by yoni1 on 2015-11-23
I'm building a Windows Vista/Ubuntu system (Vista, because that's what I have an unused license for), but I'm intending to use the sytem without video/keyboard/mouse by SSH/VNC'ing into from my tablet, so I obviously need to be able to change the default boot from within each of those operating systems.

(I don't think it's an EFI system).

Currently this is what I've come up with (it's mostly tested):

1. Installed Vista to sda1 (ntfs).  Windows bootloader installed to MBR.
2. Installed Ubuntu to sda2 (ext4).  Installed grub to sda2, not sda.
3. Rebooted to Ubuntu Live CD and copied boot sector from sda2 and placed it on C:\ubuntu.bin
4. Rebooted (automatically to Vista) and added boot entry for Ubuntu pointing to ubuntu.bin
5. Rebooted (manually) to Ubuntu and copied C:\Boot\BCD to C:\Boot\BCD.vista

Now, in theory, over VNC (assuming VNC is running as a service for each OS):
Whenever I'm in Vista, I can either reboot into Vista, or boot into Ubuntu by changing the default to Ubuntu using bcdedit and rebooting
Whenever I'm booted into Ubuntu, I can either reboot into Ubuntu, or boot into Vista by copying C:\Boot\BCD.vista to C:\Boot\BCD and rebooting

---

### Post by grahammechanical on 2015-11-23
Did you by any chance install Ubuntu using wubi.exe?

---

### Post by yoni1 on 2015-11-23
No, after installing Vista, I booted from the Live CD (14.04), selected "Install Ubuntu," and installed Ubuntu to sda2 (sda2 = /, sda3 = swap, grub installed to sda2).  I think that everything is working as I described above, I really just wanted to check if there are better alternatives to this.  I considered using grub as the main bootloader (i.e. install it to sda instead of sda2), but then the obvious problem is how to update the grub default from within Windows when I want to reboot (from remote) and get back into Ubuntu. (I did read about grub_reboot, so I could set Ubuntu as the default, and use grub_reboot to get into Vista, but that would require two boot cycles for every reboot Vista->Vista)

---

### Post by oldfred on 2015-11-23
I have installed grub directly to FAT32 & NTFS partitions. But have then created my own grub.cfg and manually maintained it.

But if you have the separate /grub NTFS or FAT32 partition you can edit it, or even have a script behind an icon to auto edit with both installs.

Since you have grub in the PBR of sda2, you can just move boot flag back & forth. The Windows boot loader just looks for the partition with the boot flag and jumps to that for more boot code. So in Windows move boot flag to sda2 and in Ubuntu move boot flag to sda1.

In Windows the command line is set active, do not know details.

       set boot flag on for sda1 (off on others)
sudo sfdisk -A1 /dev/sda
or
parted /dev/sdb set 1 boot on
Some bios refuse to boot a hard drive without a boot flag. Although grub does not need one.
More precisely: Some Bios require a boot flag on a primary partition. Or even on gpt based partitions.
So it is not important that the first partition has the boot flag, but that one of the first four partition has a boot flag.
Many Intel BIOSes, though, have a bug that requires that at least one MBR partition be marked as bootable, so you'll need to use fdisk (not gdisk, parted, or GParted) to mark the 0xEE partition as bootable/active. Note this is an Intel-specific bug; 

    
How BIOS systems boot, applies to all, but this still mentions grub legacy.
 Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

---

### Post by yoni1 on 2015-11-24
Thanks, I didn't know that about the Windows bootloader and the boot flag.  My current method seems to work (manipulating the BCD file from each OS), but the boot flag method definitely seems more straight-forward!

---

