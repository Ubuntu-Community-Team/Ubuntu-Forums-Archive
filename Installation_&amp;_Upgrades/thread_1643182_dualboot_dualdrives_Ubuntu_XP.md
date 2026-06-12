---
title: "dualboot dualdrives Ubuntu XP"
date: 2010-12-11
forum: Installation &amp; Upgrades
---

### Post by jamesisin on 2010-12-11
I would like to build a machine with dual boot (Ubuntu 10.04 and Windows XP). I have two identical hard drives in the machine in question.  One of those drives has Ubuntu installed.

I will now install Windows on the other drive.  I anticipate needing to put the Windows drive first (SATA0), but I'm sure there are other nuances which must be obeyed.

I have found this page:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

However, that page doesn't deal specifically with a two hard drive situation.

Can someone please adjust my tack so I am on the best course?

---

### Post by oldfred on 2010-12-11
Windows will not even see the Linux partitions. I would suggest to keep the system partition relatively small and make a separate data NTFS partition for any data that you may want to share with Ubuntu. I have firefox & thunderbird profiles still in my shared partition even though I only boot XP occasionally.

After you install XP run this in Ubuntu to find the windows and add it to your menu.

sudo update-grub.

After your install, besure to set the Ubuntu drive as first to Boot in BIOS.

---

### Post by jamesisin on 2010-12-11
Thanks.

Each OS drive is 160 GB and there will be a massive storage drive added later (1.5 TB probably FAT32) which will handle any necessary file sharing.  This should offer plenty of wiggle room.

It sounds as though you are recommending I use GRUB as the boot loader.  The page I linked above seems to prefer the Windows boot loader.  I am curious which is the best path?

---

### Post by wilee-nilee on 2010-12-11
> **jamesisin said:**
> Thanks.

Each OS drive is 160 GB and there will be a massive storage drive added later (1.5 TB probably FAT32) which will handle any necessary file sharing.  This should offer plenty of wiggle room.

It sounds as though you are recommending I use GRUB as the boot loader.  The page I linked above seems to prefer the Windows boot loader.  I am curious which is the best path?

If installed in separate HD the MS bootloader will be in the MBR of the XP install grub can find this and give you a choice. You can then use a per-session key-prompt to boot the XP HD.

---

### Post by jamesisin on 2010-12-11
That sounds like exactly what I'm after, wilee nilee.  Can you offer a link to instructions for setting my machine up in that manner?

---

### Post by oldfred on 2010-12-11
I like grub2 as it gives you a choice to boot other systems & is good at automatically setting then up in the menu with sudo update-grub.

If you are adding a large drive I would not use FAT32. It is not journalized and any file over 4GB is truncated (usually without warning) and is then lost. Use FAT for small devices where you have to like camera flash cards or USB keys that are not large. I understand now that xbox needs FAT, which is surprising as even Microsoft does not use it any more for systems.


NTFS and Fat info:
FAT 4GB max & no journaling 
[http://technet.microsoft.com/en-us/library/cc938932.aspx](http://technet.microsoft.com/en-us/library/cc938932.aspx)
[http://technet.microsoft.com/en-us/library/cc940351.aspx](http://technet.microsoft.com/en-us/library/cc940351.aspx)
[http://www.ntfs.com/ntfs_vs_fat.htm](http://www.ntfs.com/ntfs_vs_fat.htm)

---

### Post by wilee-nilee on 2010-12-11
> **jamesisin said:**
> That sounds like exactly what I'm after, wilee nilee.  Can you offer a link to instructions for setting my machine up in that manner?

If your building the computer and no installs have been done just install XP on one HD.Then install Ubuntu to the other making sure grub is pointed at that HD at the partitioning screen in the install.

Even if you screw up where grub goes you have the XP disc to boot to repair and run /fixmbr which puts the MS bootloader back in and then a Ubuntu disc of the distro to load that HD's MBR.

Oldfred is really good in this area and setting up separate /home partitions and a whole bunch of stuff.

---

### Post by jamesisin on 2010-12-11
I'm not too concerned about the limitations (of which I am well aware) with FAT32.  I haven't decided for certain yet, but it doesn't really matter to what we are discussing here anyway.

I installed each operating system independently without the other drive attached.  I can easily attach either drive to SATA0 if that is important.  Currently I can, by swapping which drive is attached, boot into either OS.

I have not yet attempted to boot with both drives attached, but presumably the boot loader in SATA0 will take priority (that's my guess).  I would just need to know which refinements must be made to enable this system to dual boot from this position.

---

### Post by oldfred on 2010-12-11
Both drives have internal setting that make them then they are drive 0. Ubuntu is more forgiving as it also does a search by UUID to find the correct partition to boot.

I would plug the windows drive into the lowest SATA port, plug Ubuntu into the next. Sometimes odd/even does still make a difference, not sure with your motherboard.

You should be able to boot either with your one time boot key (f12 on  my system). If both boot ok then change BIOS to boot Ubuntu drive first. After booting Ubuntu run this and it should find your windows and let you boot that also the next time.

sudo update-grub

If the Ubuntu drive has problems in the future, you still have the windows boot loader in the windows drive and can boot that.

---

### Post by jamesisin on 2010-12-16
The update grub command did the trick.  Oddly enough SATA0 is referred to as the 2nd Sata drive in the BIOS (SATA1 is called the 1st Sata drive).  Other than that not confusing at all.

Thanks to all for the assistance.

---

