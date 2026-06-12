---
title: "Trouble Installing Ubuntu 13.10 on HP Pavilion w/ Windows 8"
date: 2013-11-19
forum: Installation &amp; Upgrades
---

### Post by fernando.ceballos on 2013-11-19
I'm first time user of Ubuntu. Thought I would add a partition of Ubuntu to my HP Pavilion machine, so I can learn the OS.

After installing from a CD Ubuntu 13.10 on my machine, after the reboot I got a terminal with the following:

[I]error: no such partition
Entering rescue mode
grub rescue>[/I]

I attempted a Boot Repair. Here's the report
[http://paste.ubuntu.com/6442488/](http://paste.ubuntu.com/6442488/)

The Recommended Boot Repair didn't work.

Any help is appreciated, so that I can either a) fix so I can choose between Windows 8 and Ubunto upon booting OR b) restoring the computer to the state it was in before all this

Thanks,
Ferny

---

### Post by fantab on 2013-11-19
If I am not wrong you've installed Ubuntu on an External HDD /dev/sdf. Ubuntu's bootloader, GRUB is installed on this disk. 
So in your BIOS 'enable' booting from USB devices and set your Ext HDD as the first boot device.

---

### Post by oldfred on 2013-11-19
Since you have two drives, you should keep a Windows boot loader on sda and only have grub on sdf. If then grub was working then when booting from sdf grub would give you a choice to boot Ubuntu or Windows. If sdf is removeable then system would default to boot sda.

Boot-Repair defaults to install grub to the MBR of every drive. Uncheck the auto fix and check the update MBR in Advanced. Then choose Windows and sda as what you want to update and it will install a Windows type boot loader to sda. Or you can use your Windows repairCD to run fixBoot or auto repair.

Is sdf a removeable drive? You told Boot-Repair no so that is why it installed grub to both drives. But it is unusual for an internal drive to be sdf and not just sdb?

You are showing boot flag on sdf5. A few BIOS are designed for Windows and only let you boot if boot flag is on a primary partition (sda1 thru sda4). Windows has to have a boot flag, grub does not use boot flag, so just move boot flag to sdf1. You can use gparted and click on sdf5 and edit flags & then sdf1 and add boot flag.

I doubt if the issue is just the boot flag. 
Some combination of BIOS, grub and USB (if external) make it that systems do not boot from large drives when boot files are far into drive.
First is BIOS set for AHCI. Windows may need driver, but I think Windows 8 has that by default. Any other setting like IDE in BIOS could be the issue.
If that does not work or already AHCI, then the only solution is to have a /boot partition totally within the first 100GB of your drive. That would required moving your Windows partition to make rooom. I hate to move partitions as any powerfailure or issue in the middle can corrupt data, so good backups always suggested. Run chkdsk from Windows after any change in size of a NTFS partition.

---

### Post by fernando.ceballos on 2013-11-19
I discovered the same thing you guys did. I found that I had  accidentally installed it on an external HD. I deleted that partition  and installed on a new partition on the desktop's drive and all is  working fine.

Appreciate your help!

-Ferny

---

### Post by fantab on 2013-11-19
Glad you've figured it out. 
Please mark the thread as 'Solved' using Thread Tools.

---

