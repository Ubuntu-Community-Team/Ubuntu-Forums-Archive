---
title: "Dual-Boot Windows 7 and Ubuntu 11.10 (on 2 separate HDD's)"
date: 2012-03-31
forum: Installation &amp; Upgrades
---

### Post by p2p4m3 on 2012-03-31
I can't seem to find this answer any where. I want to dual-boot Windows 7 and Ubuntu 11.10 "side-by-side" but on 2 separate Hard Drives. Ubuntu is already installed on the first hard drive. I want Windows on the second. Can I still modify the GRUB? and How?

I may be over-complicating this but I just don't want to screw anything up.

---

### Post by 2F4U on 2012-03-31
This documentation describes how to install Windows and Ubuntu (either before or after Windows).

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/MultiOSBoot](https://help.ubuntu.com/community/MultiOSBoot)

Installing on a second hard drive is not much different than installing to a separate partition on the same hard drive.

---

### Post by darkod on 2012-03-31
I would actually prepare the win7 partition from ubuntu. Just to make sure win7 doesn't ger confused with the boot flag. Windows is very stupid about this, and it can put the boot files in a wrong location.

You can:
1. Disconnect temporarily the ubuntu disk and install win7 on the other disk. Then connect the ubuntu disk and boot ubuntu. In terminal run:
sudo update-grub
That will locate win7 and prepare the entry in the boot menu.

2. With both disks connected, from ubuntu open Gparted and prepare one ntfs partition with the size you want for win7. Maybe you want one partition on the whole disk, or a smaller partition. Then also in Gparted set the boot flag on that partition. After that boot with the win7 dvd and install on the prepared partition.

---

### Post by INKs on 2012-03-31
i need some help man...

I am new to ubuntu and and my compiz settings are not working..

Please help me someone anyone

---

### Post by darkod on 2012-03-31
> **INKs said:**
> i need some help man...

I am new to ubuntu and and my compiz settings are not working..

Please help me someone anyone

Please create your own thread instead of hijacking another thread that has nothing to do with your problem.

---

### Post by oldfred on 2012-03-31
I would suggest to follow Darko's instructions, but when plugging in drives leave the Windows drive in the lower or lowest SATA port number on motherboard. That should leave it as sda where Windows prefers to be. Ubuntu uses UUIDs so changing Ubuntu drive to sdb should not make any difference. 

In BIOS choose to boot Ubuntu drive and run this to find Windows install.

sudo update-grub

---

### Post by raen on 2012-04-30
> **oldfred said:**
> I would suggest to follow Darko's instructions, but **when plugging in drives leave the Windows drive in the lower or lowest SATA port number on motherboard. That should leave it as sda where Windows prefers to be**. Ubuntu uses UUIDs so changing Ubuntu drive to sdb should not make any difference. 

In BIOS choose to boot Ubuntu drive and run this to find Windows install.

sudo update-grub

How important is this? I don't know which drive is plugged in where on the motherboard, and I've been going in through the back panel to swap out the connectors so that only one drive is plugged in at a time. Since, while installing 12.04, it thought there was only one disk, Ubuntu (and grub boot loader) is installed to sda.

Thanks,
raen

---

### Post by oldfred on 2012-04-30
When you unplug drives and install, that drive thinks it is hd0 or sda. My system reports in sda port order on the motherboard. This system, I originally had two identical 160GB drives, one XP and the other Ubuntu. I used to have to just choose a drive to boot in BIOS and hope, but know I know or it is better identified.

XP still uses drive numbers, I think Windows 7 uses a drive ID like the UUID. Ubuntu uses UUID so drive order is not so important.

But if both drives are connected and you install to sdb, the boot files for Windows may be on sda. Likewise grub usually installs to sda. 

For the first time in ages I used a CD and let it auto install. It found some unallocated space on sdc and just installed there without any suggestion of anything. It also installed grub to sdc which surprised me, as I thought it would install to sda. And I think I have sdb as BIOS default for boot.

---

### Post by raen on 2012-04-30
So, in other words, once I'm ready to have both drives connected at the same time for a proper dual boot, I should be all right and not have to worry about what's sda and what's sdb?

Thanks,
raen

---

