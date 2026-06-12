---
title: "Internal HDD (Windows) will not boot without External HDD (Ubuntu) plugged in"
date: 2015-11-22
forum: Installation &amp; Upgrades
---

### Post by shomeir on 2015-11-22
I installed Ubuntu 15.10 on an external drive plugged into my HP Laptop.  I changed the boot order to boot the CD/DVD first, the External HDD second, and the Internal HDD third.  I installed Ubuntu on the external HDD.  It showed the external HDD as sda and the internal HDD as sdb.  I was hoping that when I unplugged the external HDD that it would boot into Windows 10, but there is a grub error.  How do I fix this?

---

### Post by yancek on 2015-11-22
It seems as though you installed Ubuntu to the external hard drive but left the default of /dev/sda as the location for Bootloader Installation.  That would explain the problem.  So what do you want to do.  Boot the external from the BIOS when you want Ubuntu and windows from it's HDD when you want it?  Probably the thing to do is to run the boot repair script and select the option to Create Bootinfo Summary and post the link here to get more details to verify the problem.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Bashing-om on 2015-11-22
shomeir; Hello;

Agreed with yancek's assessment .
To know the truth of what is, one can run terminal commands:
```

sudo blkid
sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
sudo grub-probe -t fs_uuid /boot/grub
sudo lshw -C Disk -short 

```
Expecting to find that grub is installed on the external hard drive.
I do expect the fix to be to install Windows' boot code on the internal drive - presently identified as sdb;
install ubuntu's grub ( GRand Unified Bootloader ) to the external drive - and with - which we expect already is installed :
```

sudo update-grub

```
when booted into ubuntu ... chainloading Windows to this boot code.

Thus, with the external drive connected, you have the option to boot whichever system of choice as the boot order is currently set in bios.
When the external drive is not present, the booting will then default to the internal drive - No bootable CD present either - and find the Windows' boot code .

[INDENT][INDENT]my 2 pounds worth
[/INDENT][/INDENT]

---

### Post by shomeir on 2015-11-23
Here are the results of the terminal commands:


$ sudo blkid
[sudo] password for shomeir: 
/dev/sda1: UUID="d148c6f5-941c-4e97-92bc-70566066d555" TYPE="ext4"
/dev/sda3: UUID="df86e953-4754-4904-9e4a-a66c26a340fe" TYPE="swap"
/dev/sdb1: LABEL="WINRE" UUID="444A46D84A46C680" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="2fd78090-3b17-4662-8758-c8187ebe4ab8"
/dev/sdb2: UUID="622B-5A11" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="6d24605b-35cd-4cc8-b932-1a70e3fa02e8"
/dev/sdb3: PARTLABEL="Microsoft reserved partition" PARTUUID="4596d365-b2c8-409a-9a3b-89b2c92ebc7f"
/dev/sdb4: LABEL="Windows" UUID="7AE2BA2BE2B9EC0F" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="2b3221fc-cf5d-4c5d-8cc9-10d53899ae90"
/dev/sdb5: UUID="C4F6F466F6F45A5E" TYPE="ntfs" PARTUUID="9fc633cc-1fd0-4928-8327-91ad787992c5"
/dev/sdb6: LABEL="RECOVERY" UUID="9E9E23E39E23B2A7" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="00258b46-4665-4448-9e7c-c69176f2ef04"
/dev/mapper/cryptswap1: UUID="69354da1-0af1-4490-af5e-bce7697db14e" TYPE="swap"




$ sudo debconf-show grub-pc
  grub2/linux_cmdline_default: quiet splash
  grub-pc/install_devices_empty: false
  grub-pc/install_devices_failed: false
  grub-pc/mixed_legacy_and_grub2: true
  grub-pc/partition_description:
  grub2/linux_cmdline:
  grub2/device_map_regenerated:
  grub-pc/install_devices_failed_upgrade: true
  grub-pc/kopt_extracted: false
  grub-pc/disk_description:
  grub-pc/timeout: 10
  grub-pc/install_devices_disks_changed:
  grub-pc/hidden_timeout: true
  grub-pc/install_devices:
  grub2/kfreebsd_cmdline_default: quiet splash
  grub2/kfreebsd_cmdline:
  grub2/force_efi_extra_removable: false
  grub-pc/chainload_from_menu.lst: true
  grub-pc/postrm_purge_boot_grub: false




$ sudo grub-probe -t device /boot/grub
/dev/sda1




$ sudo grub-probe -t fs_uuid /boot/grub
d148c6f5-941c-4e97-92bc-70566066d555


$ sudo lshw -C Disk -short
H/W path               Device      Class       Description
==========================================================
/0/100/10/0/1/0.0.0    /dev/sda    disk        1TB Expansion
/0/2/0.0.0             /dev/sdb    disk        1TB HGST HTS541010A9
/0/3/0.0.0             /dev/cdrom  disk        DVDRW  GUB0N

What I want it to do is to boot up into Ubuntu when the external drive is plugged in and into Windows when it isn't

---

### Post by oldfred on 2015-11-23
Is drive showing as sda, the external drive?

Windows is installed in UEFI boot mode. Cannot tell for sure if Ubuntu is UEFI or BIOS/CSM.

Best to see details from Summary Report from Boot-repair. Post link it provides.

---

### Post by shomeir on 2015-11-24
Yes the drive showing as sda is the external drive as I said in my original post.

---

### Post by shomeir on 2015-11-24
Boot-Repair summary: [http://paste.ubuntu.com/13496139/](http://paste.ubuntu.com/13496139/)

---

### Post by oldfred on 2015-11-24
Report shows Windows in UEFI boot mode and gpt partitioning on sda. Looks like drive order changed after a reboot.

You have Ubuntu on sdb, a MBR partitioned drive.
MBR drives really should be booting in BIOS/CSM/Legacy mode, so if you want to keep it as BIOS boot, you need to install grub to the MBR of sdb.

But because you have the ESP - efi system partition, it looks like grub2/Ubuntu is in UEFI boot mode.
Grub2/Ubuntu can boot in UEFI mode from a gpt drive, but with Ubuntu on a MBR drive. Not really recommended. Better to have gpt partitioning on your external drive. You can boot Ubuntu in UEFI or BIOS from external if desire. 

And you really want the external drive to boot on its own. As configured it can only boot the install on sdb, using the ESP on sda.

With multiple drives best to partition in advance and only use Something Else install option. Requires a bit of planning on what partitions you want or need and how to use Something Else.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/](http://linuxbsdos.com/2014/05/31/dual-boot-ubuntu-14-04-windows-7-on-a-pc-with-2-hdds-and-uefi-firmware/)
Something Else install, but prefer larger / of 20 or 25GB. Not showing Windows
[http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/](http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/)

---

### Post by shomeir on 2015-11-25
All of this is very confusing.  Is there any way to get windows to boot with the external drive unplugged?

---

### Post by oldfred on 2015-11-25
Since UEFI, you should always be able to go into UEFI and from boot tab choose the Windows entry.
You should also have a one time boot key, that shows the same UEFI boot entries directly.
I think HP uses f9, but others use f10 or f8. Check your manual.

Someone posted this before:
 1) press esc key while booting to access start up menu 2) press F9 for boot devices menu.

---

### Post by shomeir on 2015-11-26
That works for a one time boot without the external drive plugged in. Now I just need to eliminate grub from the internal drive.

---

### Post by shomeir on 2015-11-26
I tried plugging my external drive into an identical laptop and it won't boot - grub is not on the external drive -- it is on the internal drive.  This is not what I wanted.

---

### Post by oldfred on 2015-11-26
If keeping MBR on external drive, just run Boot-Repair and install grub to external drive.
Best to use Advanced mode and choose install and drive to install boot loader for that install.

---

### Post by furtom on 2015-11-27
> **shomeir said:**
> I tried plugging my external drive into an identical laptop and it won't boot - grub is not on the external drive -- it is on the internal drive.  This is not what I wanted.

Yes, this is correct. If grub were not on the internal drive, booting windows would be unaffected.

If you are not heavilly invested, I'd reinstall ubuntu and remember to put grub on the external drive when the time comes.

**But first,** you will have to repair the internal drive's boot sector, probably with the Windows installation media. Boot from that DVD if you have it. it should be easy to find the repair.

If that is not available, there are third party tools that may do it like rescatux, though I've never used it for this purpose.

---

