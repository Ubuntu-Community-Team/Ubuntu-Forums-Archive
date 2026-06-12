---
title: "Dual boot 14.04 and Windows 10"
date: 2015-08-19
forum: Installation &amp; Upgrades
---

### Post by Bjrnar_Lingjerde on 2015-08-19
Hi
I installed W10 first on one SSD, then Ubuntu 14.04 on another SSD while the windows 10 SSD was attached to the mainboard.
Both systems boot just fine when the other SSD is unplugged, but I only get one alternative in the GRUB menu conserning windows and that is the "windows recovery environment". It does not boot W10, it only hangs.
The Boot Repair tool does not work. What do I do to make sure GRUB boots W10 corretly? Any ideas? Thanks a lot!

---

### Post by grahammechanical on 2015-08-19
How can "both systems boot just fine" when one of the SSDs with an OS on it is unplugged? Unless ...

Both Ubuntu and Windows are on the same SSD. Or, Windows boots just fine if the Ubuntu SSD is unplugged and Ubuntu boots just fine if the Windows SSD is unplugged. 

My advice? Load Ubuntu by selecting its SSD in the BIOS/UEFI boot system and when loaded into Ubuntu run this command.

```
sudo update-grub
```

See if the update to the Grub configuration files detects detects Windows. 

Regards.

---

### Post by oldfred on 2015-08-19
What issue are you having with Boot-Repair?
It would be a lot more helpful to have the Summary Report link posted.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Bjrnar_Lingjerde on 2015-08-20
> **grahammechanical said:**
> Windows boots just fine if the Ubuntu SSD is unplugged and Ubuntu boots just fine if the Windows SSD is unplugged. 

My advice? Load Ubuntu by selecting its SSD in the BIOS/UEFI boot system and when loaded into Ubuntu run this command.

```
sudo update-grub
```

See if the update to the Grub configuration files detects detects Windows. 

Regards.

As suggested above is correct. The system boots fine as the respective disc is selected.
Updateing Grub as you suggest still only finds the "Windows Recovery Environment" which doesnt load windows

Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-30-generic
Found initrd image: /boot/initrd.img-3.16.0-30-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Recovery Environment (loader) on /dev/sdc1
done

I have no issues with running the boot repair, it runs just fine but does not add the correct windows loader to the list only the recovery loader. Please have a look at the boot repair log: [http://paste.ubuntu.com/12133432/](http://paste.ubuntu.com/12133432/)
I have three disks:
sda is a data storage disc allthough it says win 8 in the log.
sdb is ubuntu
sdc is windows 10

---

### Post by oldfred on 2015-08-20
It is saying sda1 is hibernated, but not sdc1? Or Windows fast startup?
You must have fast startup/hibernation off to work with dual booting.

When you installed Windows to sdc1, was sda or sdb set as default for BIOS boot? If so Windows boot files were in those drives, either in sda's hibernated partition or erased when you installed Ubuntu. 

Windows creates a 100MB boot partition in drive set as boot in BIOS. Most install to sda so boot is in sda. But installs to other drives may not install Boot partition to same drive.

---

### Post by Bjrnar_Lingjerde on 2015-08-20
I changes the SAT_A cables so that the w10 disc became sda1 and ubuntu disc sdb1. Now dual boot works. Hovewer, the 2TB ntfs storage disc is gone. I put it on the last sata port. The two SSDs are on Intel 6GB SATA ports and the 2TB disc is on a Marvel 6GB port. Either Marvel ports requeres some extra settings in bios to enable??

---

### Post by oldfred on 2015-08-20
Your sdc was shown before, not sure why now.

I have seen issues with asmedia ports and need to only use Intel SATA ports.
Some motherboards have settings to enable/disable drives.
Drive should be in AHCI mode, not IDE nor RAID.
Not sure of any issues with Marvel?

---

