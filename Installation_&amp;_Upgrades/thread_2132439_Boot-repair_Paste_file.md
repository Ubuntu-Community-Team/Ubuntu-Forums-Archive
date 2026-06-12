---
title: "Boot-repair Paste file"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by Bresser on 2013-04-04
Can anyone tell me what this means:
[http://paste.ubuntu.com/5672524/](http://paste.ubuntu.com/5672524/)
I ran Boot-repair and  now it deleted my os and wont let me boot from USB.

---

### Post by fantab on 2013-04-05
The gist of your boot-repair output is that Windows boot loader (MBR) is messed up... How did you manage that?

If you had installed Ubuntu in Windows with WUBI then I don't think Boot Repair will be of any help. However, we need to confirm this.
The simple solution would have been to 'repair' Windows MBR, which could have been done with Windows Install Disk or Windows Repair Disk.

Since you have deleted your OS (what OS was that?), what would you like to do now? Do you want to Dual Boot Windows and Ubuntu? Or Do you just want to install either Ubuntu or Windows? And do give more details about your machine.
Tell us what help do you expect from this forum.

---

### Post by Bresser on 2013-04-05
Ok 
Computer: HP 2000 Notebook Laptop
OS: None, used to be Win 7
Perferred OS: Doesn't matter to me as long as I am able to use my computer.
Processor: AMD E-450 APU with Radeon(tm) HD Graphics
Process. Speed: 1.65 Ghz
RAM: 4 GB
Really all I want is to be able to use my computer. I love Ubuntu and I would be fine with Ubuntu as long as I am able to get Wine because I need Itunes to sync my Ipod. If I could get back the files that I know are still on my drive that would be nice. But if i have to lose them all that is acceptable to me

Thanks,
Bresser

---

### Post by darkod on 2013-04-05
You DO NOT have ubuntu, you have wubi inside windows. On top of that, your hdd is in Dynamic mode, not Basic. Dynamic disk is Microsoft format and most linux tools can't work well with it.

Boot-repair is for proper ubuntu on its own partition, not for wubi (as far as I know).

Get your win7 install dvd or rescue cd, boot with it and try the Repair This Computer option which should help you restore your bootloader.

In general you can copy data from ntfs partition from ubuntu live mode when windows doesn't boot. But since you have Dynamic disk, I wouldn't try touching it too much with linux tools. The choice is yours.

---

### Post by Bresser on 2013-04-05
Oh they are simple partitions not dynamic. And i already put them on a USB

---

### Post by oldfred on 2013-04-05
SFS is dynamic, when you look at partitions from Windows it will not say basic.

 Microsofts offical policy is a full backup, erase dynamic partitions and create new basic partitions. There is no undo.
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You may be use a third-party tool, such as Partition Wizard MiniTool or EASEUS to convert a convert a dynamic disk to a basic disk without having to delete or format them.
I've never used any of these and so I can't be sure they will work.Be sure to have good backups as any major partition change has risks.
Dynamic also on gpt as LDM
[http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx]("http://msdn.microsoft.com/en-us/library/windows/desktop/aa365449%28v=vs.85%29.aspx")

   Used EASEUS Partition Master -  free version used to  include conversion
[http://ubuntuforums.org/showthread.php?t=1692248](http://ubuntuforums.org/showthread.php?t=1692248)
EASEUS Partition Master - The free home edition converted both dynamic partitions into basic partitions in less than 5 minutes!!
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)

---

### Post by bcbc on 2013-04-05
> **Bresser said:**
> Can anyone tell me what this means:
[http://paste.ubuntu.com/5672524/](http://paste.ubuntu.com/5672524/)
I ran Boot-repair and  now it deleted my os and wont let me boot from USB.
Boot repair shows the "before state" at the bottom, and the "after state" at the top. So you need to look lower down to see how it stopped Windows booting. And the clue is that the boot flag was on /dev/sda2 before you ran boot repair, and now it is on /dev/sda1.

So change that back. Do you know how to do this?

And then uninstall Ubuntu/Wubi (from Add/remove programs) and only install it when you've got rid of dynamic disks.

Here is the relevant info:
```
=================== fdisk -l:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x27f7617e


Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63        2047         992+  42  SFS
/dev/sda2   *        2048      409599      203776   42  SFS
/dev/sda3          409600   443033599   221312000   42  SFS
/dev/sda4       443033600   625140399    91053400   42  SFS




=================== Recommended repair
Recommended-Repair
This setting will restore the [(generic mbr)] MBR in sda, and make it boot on sda1.
Additional repair will be performed: unhide-bootmenu-10s




Will restore the MBR_TO_RESTORE : sda (generic mbr) into sda
dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
0+1 records in
0+1 records out
parted /dev/sda set 1 boot on


                                                                          
Error: Partition(s) 1, 2, 3, 4, 5 on /dev/sda have been written, but we have
been unable to inform the kernel of the change, probably because it/they are in
use.  As a result, the old partition(s) will remain in use.  You should reboot
now before making further changes.



```

---

