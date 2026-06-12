---
title: "avoiding GRUB MBR LILO issues"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by artsci2 on 2008-09-22
I've been avoiding boot loader problems in my multi OS systems by using separate hard drives for each system e.g. a windows hard drive and a second drive with Ubuntu installed. Currently I have been avoiding multiboot problems by disconnecting the Ubuntu disk when installing windows and then diconnecting the Windows drive before installing Ubuntu. Then I connect both drives and boot the computer. The bios offers a selection of boot device if I press F8 during start up.

I wish that the Ubuntu and Windows installation disks would see this two-separate-drives installation and offer the option to not install a bootloader so I could do my installations without needing to remove and replace hard drives.

BTW: I also tried partitioning the drives with a swap on the windows drive for use by Ubuntu, and a fat32 partition on the Ubuntu drive for windows to use as vitrual memory. However Ubuntu and windows dont seem to use much swap/virtual memory on 512Mb-2Gb machines so making the extra partitions is not helpful for me.

---

### Post by caljohnsmith on 2008-09-22
If you don't install a boot loader though, how are you planning on booting Ubuntu? You have to use some sort of boot loader in the Master Boot Record (MBR) to boot Ubuntu, and one of the best is Grub. If you are concerned with Grub being installed to your Windows drive when you install Ubuntu to the other drive, all you have to do is hit the "advanced" button in the final Ubuntu installation stage, and you can tell Grub to install to /dev/sda or /dev/sdb, or whichever is the Ubuntu drive. Then it won't touch the Windows drive. Is this what you are looking for maybe?

---

### Post by artsci2 on 2008-10-01
> **caljohnsmith said:**
> If you don't install a boot loader though, how are you planning on booting Ubuntu? ...?

During boot the bios give a message, "press F10 to select boot device". When you do that a list comes up and you just use the arrow keys to highlight the disk/cd/pendrive you want to boot from. Older computers dont have this feature though.

---

### Post by louieb on 2008-10-01
You have 2 boot loaders now:
the MBR of your window drive points to the windows boot loader program **ntldr**. 
the MBR of your Linux drive points to the GRUB program **stage2**.

If you want to avoid using the F10 key or whatever key brings up boot device menu, its easy enough to add a Windows entry to GRUB. It a little harder but you could add Ubuntu to your windows boot loader too. 

The problem is GRUB can't boot windows. but it can start the windows boot loader ntldr by chainloading the windows partitions boot sector.  So you have to have ntldr to boot widows.

The same can be said about ntldr. It can't boot a Linux OS but it can be tricked into starting GRUB or LILO. So you have have one of those boot loaders in order to start Linux. 

Hope this clears things up a bit.

---

