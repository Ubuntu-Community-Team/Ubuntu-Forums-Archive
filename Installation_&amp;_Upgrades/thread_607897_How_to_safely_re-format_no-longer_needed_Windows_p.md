---
title: "How to safely re-format no-longer needed Windows partition"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by tbraun on 2007-11-09
Hello!

I want to go completely Windows free (yeah!) and delete my Windows partition on my laptop. But I need some help/advice, because I don't want to screw up anything and leave the system unbootable. I would like to reformat the partition with ext3 and make it available as a data partition to Linux.

My laptop came originally installed with Windows XP. I installed Ubuntu (7.04) the usual way: Insert Live CD, click install. I now have a dual-boot system via Grub. If I would reformat the Windows partition would that impact the operation of Grub? I guess I can manually edit out the option to boot into Windows from the Grub menu. I'm just not sure exactly what Grub needs to work correctly, as far as specific partitions and flags for partitions is concerned. My concern comes from what gparted shows me. I have attached a screenshot.

The 'ntfs' partition is where Windows currently lives (/dev/sda2). As you can see, it is labelled with a 'boot' flag. No other partition is labelled that way, so I'm a bit nervous about just whacking this. What does this mean? The notification-alert in the line for that partition says that no mount-point can be found. That's also strange, because it's definitely mounted and accessible.

Any help is greatly appreciated. Thank you very much!

Tom

---

### Post by bulldog on 2007-11-09
You can safely reformat that partition.
You have to umount it first to do so.
Bare in mind Grub is counting partitions starting with 0,so if you make the partition an ext3 and don't change into two partitions your safe.
If you want to make more than one partition you'll have to edit the menu.lst.
You can remove the windows entry from the menu.lst as well if you remove windows.

---

### Post by stchman on 2007-11-09
> **tbraun said:**
> Hello!

I want to go completely Windows free (yeah!) and delete my Windows partition on my laptop. But I need some help/advice, because I don't want to screw up anything and leave the system unbootable. I would like to reformat the partition with ext3 and make it available as a data partition to Linux.

My laptop came originally installed with Windows XP. I installed Ubuntu (7.04) the usual way: Insert Live CD, click install. I now have a dual-boot system via Grub. If I would reformat the Windows partition would that impact the operation of Grub? I guess I can manually edit out the option to boot into Windows from the Grub menu. I'm just not sure exactly what Grub needs to work correctly, as far as specific partitions and flags for partitions is concerned. My concern comes from what gparted shows me. I have attached a screenshot.

The 'ntfs' partition is where Windows currently lives (/dev/sda2). As you can see, it is labelled with a 'boot' flag. No other partition is labelled that way, so I'm a bit nervous about just whacking this. What does this mean? The notification-alert in the line for that partition says that no mount-point can be found. That's also strange, because it's definitely mounted and accessible.

Any help is greatly appreciated. Thank you very much!

Tom

If you really want to be XP free just right mouse click on your Windows partition and select delete.  After that hit apply.

Delete sda1 and sda2.  If you have those volumes mounted you must unmount those volumes.

---

