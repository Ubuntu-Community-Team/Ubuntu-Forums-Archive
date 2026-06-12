---
title: "Unable to boot Ubuntu after installing Windows 11"
date: 2023-11-29
forum: Installation &amp; Upgrades
---

### Post by sohrabp72 on 2023-11-29
I got 2 SSD storage, first one shown as /dev/sda has ubuntu installed on, second /dev/sdb.
first of all, Ubuntu has been installed on /dev/sda1 then I tried to install Windows on /dev/sdb3. after installing Windows, now I can boot Windows but Ubuntu.
here are some useful outputs:
```

Disk /dev/sda: 223.57 GiB, 240057409536 bytes, 468862128 sectors
Disk model: WD Green 2.5 240
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 7D5AA989-7C99-48C9-9823-9640E31C972D

Device     Start       End   Sectors   Size Type
/dev/sda1   2048 468860927 468858880 223.6G Linux filesystem


Disk /dev/sdb: 476.94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: Samsung SSD 850 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 57A176F6-B6BA-4959-8253-4B589E0DA61E

Device         Start        End   Sectors   Size Type
/dev/sdb1       2048     206847    204800   100M EFI System
/dev/sdb2     206848     239615     32768    16M Microsoft reserved
/dev/sdb3     239616  313020415 312780800 149.1G Microsoft basic data
/dev/sdb4  313020416  314570751   1550336   757M Windows recovery environment
/dev/sdb5  314572800 1000212479 685639680 326.9G Microsoft basic data

```
also:
```

ubuntu@ubuntu:/mnt/boot/efi$ efibootmgr -v
BootCurrent: 0003
Timeout: 1 seconds
BootOrder: 0001,0000,0003,0002,0004
Boot0000* Windows Boot Manager    HD(1,GPT,cfb3dedb-79e4-4ab7-8b94-ccb20f493c27,0x800,0x32000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...e................
Boot0001* WD Green 2.5 240GB    BBS(HD,,0x0)..BO
Boot0002* Samsung SSD 850 PRO 512GB    BBS(HD,,0x0)..BO
Boot0003* UEFI:  USB DISK 2.0 PMAP, Partition 1    PciRoot(0x0)/Pci(0x14,0x0)/USB(4,0)/HD(1,GPT,08610777-a98b-4c93-b0ae-c0caf2ad7a47,0x800,0x39d17df)..BO
Boot0004*  USB DISK 2.0 PMAP    BBS(HD,,0x0)..BO

```
I can use an Ubuntu live system to install needed boot loader files also the above output came out from the live system.
I'm confused about Efi Uefi Grub and boot-loader systems and can't clear them of each other.
Thanks in advance.

---

### Post by Rubi1200 on 2023-11-29
To avoid issues like this it is usually recommended to install Windows and then Ubuntu.

From a liveUSB please run the boot info script in my signature.

Do not try and repair, just post the link to the pastebin with the summary results so we can see where everything is now.

Thanks.

---

### Post by sohrabp72 on 2023-11-29
Thanks for replying.
here is the [link]("https://paste.ubuntu.com/p/wpSPPKgHPM/")

---

### Post by tea for one on 2023-11-29
As you installed Ubuntu 22.04 originally, it looks like you installed it in Legacy mode.
Then, subsequently, Windows 11 will automatically install in UEFI mode.
Disk sda does not have an ESP.
Windows 11 on sdb has an ESP.

First, I would remove (isolate or de-activate) sdb and see if Ubuntu boots?

Ubuntu and Windows on separate disks is ideal.
However, both systems should be in UEFI mode with an ESP on each disk, then you can boot independently via the PC UEFI boot menu.

---

### Post by sohrabp72 on 2023-11-29
How can I have ESP on sda for booting Ubuntu?

---

### Post by tea for one on 2023-11-29
```
                        Avail Use% Mounted on
/dev/sda1              195.9G   5% /mnt
```
As you only have 5% used space on sda1, I would suggest that you backup your Ubuntu personal data and re-install Ubuntu in UEFI mode.
Less than 1 hour downtime and an ESP will be created automatically.

Remove your Windows drive so that only the target drive is visible for the UEFI Ubuntu installation.

---

### Post by yancek on 2023-11-29
I would not expect that you would be able boot Ubuntu with your current configuration as it is on a GPT drive and installed in Legacy mode.  To do that, you would need to have a 1MB undormatted partition on which the core.img file would be installed.  You don't have that.

I'd agree with the suggestion above to simply re-install Ubuntu in UEFI mode.  Disable any Legacy/CSM option in the BIOS before booting to re-install.

  > How can I have ESP on sda for booting Ubuntu? 		  

That has actually been the default with the Ubuntu ubiquity installer but you need to boot and install EFI.  If you want windows and Ubuntu totally separate, you can create an EFI partition on sda during the install.  This will work much better if you disconnect or disable the windows drive before installing, if you can.

With EFI systems, it doesn't matter if you install a Linux or windows system first as separate directories are created for each with boot files on the EFI partition and boot code is not overwritten in the MBR as on Legacy systems.

---

### Post by oldfred on 2023-11-29
Not sure how you installed Ubuntu.
With a gpt partitioned drive, you have to have either a bios_grub partition or an ESP - efi system partition for grub install.
But your sda only shows the ext4 partition.
Ubuntu installer normally defaults to first drive for ESP if UEFI or bios_grub if old BIOS install.
Did you have Ubuntu's ESP on what is now Windows drive, so Ubuntu boot got erased?
You do not show Ubuntu entry in UEFI, so install was probably old BIOS, but then not sure why you do not have bios_grub.
Best to then reinstall in UEFI boot mode to gpt partitioned drive & restore from your backup.
If possible I might disconnect Windows drive, or in UEFI settings turn off/disable drive, so not seen when installing Ubuntu.

How you boot install media UEFI or old BIOS, is then how it installs or repairs. Best with UEFI hardware to always boot in UEFI boot mode.

---

