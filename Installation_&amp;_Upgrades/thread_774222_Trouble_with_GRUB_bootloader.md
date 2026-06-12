---
title: "Trouble with GRUB bootloader"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by [mike@theInternet]$ on 2008-04-29
Hello fellow Ubuntuians, I have a question.  I have a machine which I partitioned for 2 installations of Ubuntu (7.10 and 8.0x) I formatted the 8.0x partition and planned on resizing the partition to expand my 7.10 install.  Long story short, apparently my GRUB is still trying to pull from the partition I just formatted.  How do I set my 7.10 partition to be the default boot partition thereby pointing it to my /boot/grub directory on my 7.10 partition.  Was that confusing?  :)  Thanks for any help.

Thanks,
Mike

PS I have some bootable CDs such as GParted live that I was going to try and resize and set bootable with tonight.

---

### Post by dstew on 2008-04-29
You need to reinstall grub, because the boot loader is "hard wired" to get its stage2 and menu from a particular partition. If you change your partitions around, the grub boot loader can't find its stage2. The solution is to re-install grub, with the proper root designation.

To reinstall grub, boot a Live CD. On a command line enter **sudo grub**. That will get you the grub command line, with the **grub>** prompt. At the grub prompt, enter```
find /boot/grub/stage2
```It should return the name of the partition that contains the stage2 file in grub-speak, maybe (hd0,0). Whatever it returns, use as the argument for the  root statement, and setup grub in the MBR of the first disk, like this:```
root (hd0,0)
setup (hd0)
quit
```Then reboot, and it should be OK.

---

### Post by [mike@theInternet]$ on 2008-04-30
That worked, many thanks!

---

