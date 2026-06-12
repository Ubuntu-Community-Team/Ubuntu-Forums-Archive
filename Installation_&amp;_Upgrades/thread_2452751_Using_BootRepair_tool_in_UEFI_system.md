---
title: "Using BootRepair tool in UEFI system"
date: 2020-10-27
forum: Installation &amp; Upgrades
---

### Post by helen314 on 2020-10-27
After running BootRepair  I no longer have /etc/default/grub file.
How do I configure my grub - for UEFI?
Any help recovering from this would be greatly appreciated.

---

### Post by oldfred on 2020-10-27
Post link from Summary Report that Boot-Repair gives you.
Boot-Repair does change an entry or two in /etc/default/grub, but would not delete it.

---

### Post by helen314 on 2020-10-27
```

http://paste.ubuntu.com/p/BYGhXjSs8x



```

---

### Post by oldfred on 2020-10-27
Do not run Boot-Repair's auto fix.
Generally anyone with multiple drives should not run auto fix in BIOS mode as it just installs one grub from first install it sees to every drive.
Most should not have one grub, but perhaps different boot loaders in different drives.

You also booted live installer/Boot-Repair in BIOS mode, but have UEFI installs. And an UEFI system.


Line 446 shows you have 7 systems installs, most 16.04 versons.

I do not know RAID, but it looks like you have RAIDed partitions on the same drive???
My understanding it this or different drives:
**RAID** stands for Redundant Array of Inexpensive Disks.
Someone who knows & understands RAID, need to review your configuration.
Most that I have seen, seen to prefer a smaller boot drive, now often SSD, and then multiple RAID drives for data.
But RAID is for uptime, not backup.



You also have a 2.7TB (3TB) drive in MBR(msdos) mode, sda. That effectively converts it to 2TB as the now 40 year old MBR only supports 2TB.
Back in early '80s when MBR was created MB was large, GP not even heard of, and TB so large as no one would ever use it with MBR, so they set 2TB as the max that would be supported. 
If you want the full 2.7TB you have to convert to gpt, but with all your partitions that is a major change.

You have grub in MBR of sda for BIOS boot.
And you have grub installed to PBR - partition boot sector of sda18. Generally grub should not be installed to PBR. You cannot directly boot grub in a PBR.

You show three ESP - efi system partitions.
sda17, sdb1 & sdc1
UEFI is booting ubuntu from partitin with GUID 4f929080-5b02-4d52-a717-efffff17ed13 which is sdc1
And the grub.cfg refers to full grub in 6f8013d4-0561-4f13-a5d8-6b97257cdf63 your sdc2 as default boot.

You do seem to be missing /etc/default/grub in sdc2, but shows grub in sda18, sdb2, sdc5, sdc6.

You show a full grub.cfg in sdc2, so can you boot?
If so I would do a total reinstall of grub in UEFI boot mode. You can do it manually if you can boot, or use Boot-Repair in live installer, or live installer & chroot into install on sdc2.
sudo dpkg-reconfigure grub-efi-amd64
and/or
sudo apt purge grub-efi-amd64  grub-efi-amd64-signed
after above you will not be able to reboot, unless you run next command &  it works. If not then you need live installer & Boot-Repair.
sudo apt install grub-efi-amd64-signed



It looks like you have an old copy of Windows XP in sdb12, a gpt partitioned drive. Windows XP only boots from primary NTFS partition with boot flag on MBR drives. It will never be bootable.

---

### Post by helen314 on 2020-10-28
```

  	 	 	 	   [INDENT]UEFI is booting ubuntu from partitin with GUID 4f929080-5b02-4d52-a717-efffff17ed13 which is sdc1
And the grub.cfg refers to full grub in 6f8013d4-0561-4f13-a5d8-6b97257cdf63 your sdc2 as default boot.

You do seem to be missing /etc/default/grub in sdc2, but shows grub in sda18, sdb2, sdc5, sdc6.
[/INDENT]
```
         Thanks for analysis and confirmation.

        The KEY current "clean" hardware  is indeed sdc. Everything else is superfluous, md  Windows etc. 
         I will tackle all the garbage AFTER "missing /etc/default/grub" is resolved.

        I just installed THREE Ubuntu OS from ISO USB file, all in sdc. 
         It is only hardware I can safely add OS to . 
        The "grub" AKA "ubuntu" EFI defaults to sdc2 because it as the LAST OS install. 
        I am not having much luck selecting the other OS's  on sdc drive.

        Yes, there is NO /etc/default/grub AFTER  this default boot to sdc2. 

```

e@e-SATA:~$ cat /etc/default/grub
cat: /etc/default/grub: No such file or directory
e@e-SATA:~$ 

```


       That stops me from continuing to resolve the other issues.

---

### Post by oldfred on 2020-10-28
Full reinstall of grub will totally restore grub to defaults and add any missing files.

If you somehow manually deleted it and it is the only thing missing, you probably can just copy any one of the other grub from your other installs.
If this shows errors, then you also have other grub issues.
sudo update-grub

---

### Post by helen314 on 2020-10-28
In an attempt to unclutter the output I have removed both USB drives ( 2 TB and 3 TB)

```

  	 	 	 	   [h=1]http://paste.ubuntu.com/p/dHWrRdfD2m/[/h]  

```

I still have no /ect/default/grub , BUT I have NOT done any repair as suggested 

I have noticed** this **


```

  	 	 	 	   Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would purge (in order to fix packages) and **reinstall the grub-efi-amd64-signed** of
sda2,
using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s  use-standard-efi-file    

Final advice in case of suggested repair: ______________________________________

**I do not get why boot-repair suggest this - I am already booting to "OS in use" **efibootmgr confirms that. 
Please do not forget to make your UEFI firmware boot on the The OS now in use - 
Ubuntu 16.04.7 LTS CurrentSession entry (sda1/efi/****/shim****.efi (**** will be updated in the final message) file) !
```

---

### Post by oldfred on 2020-10-28
It is just confirming what it is doing & what you need to boot.
Many have multiple installs & may not have the fixed system as default.
I suggest running the UEFI fix, now you are booted in UEFI mode.

---

