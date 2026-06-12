---
title: "Windows 10 Upgrade on a dualboot laptop"
date: 2015-11-25
forum: Installation &amp; Upgrades
---

### Post by alpage2 on 2015-11-25
I have an elderly laptop (acer aspire 5315) (bought with Vista installed, originally, later replaced by a clean install of Win8) which now was happily running as a dualboot system with fully up-to-date versions of Windows 8.1 and Lubuntu 15.10. Having heard good things about Windows 10, I decided to accept the Win10 upgrade, during which it warned that it would do some automatic reboots. At the first automatic reboot, the usual grub menu had disappeared, and it dropped to a grub rescue prompt.

I asked for a list of partitions:
```
grub rescue> ls
(hd0) (hd0, msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1)
grub rescue>

```

but I don't know where to go from there. What I would like to do is get the windows partition booting normally so that continuing windows reboots execute smoothly and I can complete the win10 upgrade. After that it will be no problem to reinstall grub or even a full install of lubuntu. It is finishing the win10 upgrade that is my first priority.

I have the original windows 8 install system on a USB stick, so I assume I can restore the mbr from that? But I was just wondering if there was a more elegant solution that also preserves the grub menu?

Any advice or pointers would be much appreciated. I have trawled the forums, but not found a problem that was exactly the same as mine.
Thanks in anticipation
Alan

---

### Post by yancek on 2015-11-25
Did you install windows 8.1 using UEFI or the older MBR to boot?
In any case, windows will modify the boot code during this upgrade.  There are numerous posts here with people in this same situation.  The problem is that your upgrade from windows 8.1 to windows 10 failed.  You might be better off asking your question at a windows forum or the microsoft support site.  The link below has a pretty good description of how to use the grub rescue prompt to boot which you might try.

  [https://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/](https://www.linux.com/learn/tutorials/776643-how-to-rescue-a-non-booting-grub-2-on-linux/)

---

### Post by grahammechanical on 2015-11-25
> even a full install of lubuntu.

A lot of those threads about problems after upgrading Windows 8.1 to Windows 10 seem to indicate that the upgrade changed the partitions. That old Vista machine would have had MBR partitioning with its 4 primary partition limit. You might find that the Lubuntu partition has been replaced with a Windows partition.

GPT partitioning allows many more primary partitions. And we can use GPT partitioning even with a BIOS motherboard that is not UEFI capable. Gparted in a Ubuntu live session will let us set a hard disk to GPT partition table.

So, once you have recovered what data you can you may want to wipe that disk and set a GPT partition table and then re-install Windows 8.1 and upgrade to windows 10 and then re-install Lubuntu.

Regards.

---

### Post by alpage2 on 2015-11-25
Many thanks, yancek & grahammechanical - great information that I can follow up on, although it may be a day or two before I have the time - I'll post back here when I do, with the outcome.

yancek - that was a great grub tutorial, which confirmed that win8 installed with the old mbr partition table (I don't recall it offering a choice). I'll use commands from the grub 2 tutorial to try to examine the contents of the partitions, and see if linux was overwritten or not - and if not, to reinstate the grub menu. But failing that, I can fall back on grahammechanical's suggestion of cleaning up the partitions and:
> 
 set a GPT partition table and then re-install Windows 8.1 and upgrade to windows 10 and then re-install Lubuntu.


Thanks again, to both
Alan

---

### Post by oldfred on 2015-11-25
Windows only boots from gpt partitioned drive with UEFI. But if an older computer you probably do not have UEFI.
Ubuntu can boot with either BIOS or UEFI from gpt partitioned drives. I used gpt with my old system with 10.10 and BIOS boot with XP on another MBR partitioned drive.

But Windows has always had a bug where it rewrites partition tables on major updates and "forgets" to write a Linux partition that is inside an extended partition.

If you look at partitions and just have an empty space from start of extended and start of swap, Windows forgot your partition. It still is there with all its data if you do not do other things to damage it. You can use parted rescue or testdisk to add partition back.

       sudo parted /dev/sda unit s print
[http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080](http://askubuntu.com/questions/654386/windows-10-upgrade-lead-into-grub-rescue/655080#655080)
Windows 7 to Windows 10 MBR partition missing
[http://ubuntuforums.org/showthread.php?t=2288988](http://ubuntuforums.org/showthread.php?t=2288988)
[http://ubuntuforums.org/showthread.php?t=2290190](http://ubuntuforums.org/showthread.php?t=2290190)
[http://ubuntuforums.org/showthread.php?t=2292545](http://ubuntuforums.org/showthread.php?t=2292545)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)
[http://www.gnu.org/software/parted/manual/html_node/rescue.html](http://www.gnu.org/software/parted/manual/html_node/rescue.html)
[http://gparted.sourceforge.net/faq.php/#faq-22](http://gparted.sourceforge.net/faq.php/#faq-22)
Parted rescue seems easier than testdisk
[http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462](http://askubuntu.com/questions/665445/upgraded-to-windows-10-on-dual-boot-and-cant-boot-to-ubuntu-partition/665462)#

---

### Post by alpage2 on 2015-11-26
Many thanks, oldfred - lots of good information, which I'll take on board..

Thanks again
Alan

---

