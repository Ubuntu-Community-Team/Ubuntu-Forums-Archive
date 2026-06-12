---
title: "Dual Boot Prep"
date: 2016-08-01
forum: Installation &amp; Upgrades
---

### Post by khublaikhan on 2016-08-01
Hi All,

Like many other posters here I am somewhat confused with the UEFI option to dual booting with WIndows 10.

Before I do this however, I have noticed that I have already like 5 partitions on my system, - one is definitely the Recovery partition 15GB that came with the laptop and the another is the system partition, there is one labelled EFI System and there is a couple marked as recovery partition. I have created a Windows 10 Recovery disk but I wish to delete as many unneeded partitions as possible before I attempt the Dual Boot.

Any suggestions how I do this please?

---

### Post by grahammechanical on 2016-08-01
Motherboards that have UEFI boot systems usually have hard drives with GPT partitioning. With GPT there is no limit to the number of primary partitions which is a big improvement on the older BIOS boot system motherboards with MBR partitioning that limited the number of primary partitions to 4. Forcing everyone to use a work-around.

UEFI boot systems have two install options. EFI mode and BIOS/legacy/CSM mode. Windows 7 cannot be installed in EFI mode. That is why there is a BIOS/legacy mode. Windows 8/10 is always preinstalled in EFI mode. Ubuntu can be installed in either mode but it must be installed in the same mode that Windows is install in. You have Windows 10 so you must boot the Ubuntu install ISO image in EFI mode so that Ubuntu will be installed in EFI mode. Then you will not have problems dual booting.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

There is other information in that wiki that you will need to follow.

What Windows partitions you delete is up to you. You take the consequences. I know nothing about Windows 10. But there is no need to delete any partitions in order to dual boot with Ubuntu. Modern hard drives are not short of space. And with GPT partitioning we do not have a 4 primary partition limit.

The EFI system partition is an efi_boot partition. It is where Microsoft puts the Windows 10 efi boot files. When Ubuntu is installed in EFI mode the Ubuntu installer will need somewhere to put the Ubuntu efi boot files. It will use the same partition as Windows 10. The two sets of efi boot files will happily co-exist.

If by chance you try installing Ubuntu in BIOS/Legacy mode the Ubuntu installer may fail to install the Grub boot loader. This is because when Ubuntu (or any OS) is installed in BIOS/Legacy mode on a hard drive with GPT partitioning the installer will need a bios_boot partition for the boot files. You do not have a bios_boot partition. So, installing Ubuntu in EFI mode is the least complicated method.

Regards

---

### Post by oldfred on 2016-08-01
With UEFI/gpt do not delete any partition.
All but perhaps a recovery partition are required. And only if you have used recovery to make a full backup of Windows would I possibly delete a recovery partition.
Many systems create a small recovery DVD or flash drive but then that is only to boot and copy the recovery partition. So you may not have a full backup of your Windows, if you delete recovery partitions.

       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by khublaikhan on 2016-08-04
So I installed Ubuntu in UEFI Mode, using the something else option I created a SWAP Space, a 10GB / partition and a 20GB /Home  Partition. I chose to install EFI boot files in the same partition listed as "EFI" on the Windows Partitions.

After installation, when I restarted the system went immediately to Windows 10. I don't understand why??

Help appreciated

---

### Post by oldfred on 2016-08-04
Those partition sizes are just ok for a start. If using separate / & /home and only 30GB, I would suggest them as one / partition with home inside. Then unused space is shared as you may nto be sure which partition fills up first. Downloading data can fill /home but updates & log files can fill / also.

Can you choose ubuntu entry (you may have two, one shim and the other grub) from UEFI boot menu. You can usually directly access UEFI boot menu with one time boot key like f10 or f12. But if fast boot in UEFI (different than fast start in Windows) is on, you may not have time to press a key. From Windows then go into UEFI and turn off fast boot. But make sure Windows fast start up is off also. Windows may on updates turn it back on.

What brand/model system. Some work directly with Ubuntu, others need work arounds to boot ubuntu entries.

Do not run any fixes until reviewed.
 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

