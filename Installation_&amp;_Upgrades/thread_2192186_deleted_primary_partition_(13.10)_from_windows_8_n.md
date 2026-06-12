---
title: "deleted primary partition (13.10) from windows 8 now stuck in grub rescue"
date: 2013-12-06
forum: Installation &amp; Upgrades
---

### Post by tausch86 on 2013-12-06
Hello

I was having issues with Ubuntu 13.10 so I decided to delete the partition through windows 8 and now I am in some hot water. I can't seem to get out of grub rescue. I have Ubuntu 12.04 boot disc and windows 8 install disc. If I reboot my computer with either disc inside nothing happens. 

So my question to you guys is can I install Ubuntu in this now unallocated partition or is there anyway j can make windows 8 the primary partition through grub rescue?

---

### Post by fantab on 2013-12-06
The deleted 13.10 partition had files required by Grub to boot. So naturally the boot problem is expected.
Never manage Linux partitions from Windows or Windows partitions from Linux.

Yes you can Install Ubuntu again.
You can also fix your Windows Boot.
Tell us what exactly do you want to do?

When you insert any install DVD/USB you have make the DVD/USB boot a top priority in the UEFI/BIOS. Have you done that?
Do you have UEFI boot? Did you install Win8 or was it pre-installed?

---

### Post by tausch86 on 2013-12-06
Hi fantab. Thanks for your response. Never again will I manage Linux partitions from Windows. I would like to install ubuntu as the primary partition again. 

I have not done that but I will do that. I installed windows 8, it did not come pre-installed. I have BIOS. My computer came installed with Windows 7.

---

### Post by fantab on 2013-12-06
To install ubuntu to the same primary partition...
During installation of Ubuntu choose "Something Else" option. At next dialog select your ubuntu partition and hit 'Change'.
Use the following parameters to setup the partition for Ubuntu install:
Use as: Ext4 journaling system
Mountpoint : /
Format: check the box

Continue with installation.

---

