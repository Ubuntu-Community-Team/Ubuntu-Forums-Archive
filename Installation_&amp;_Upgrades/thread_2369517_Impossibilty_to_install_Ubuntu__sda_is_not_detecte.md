---
title: "Impossibilty to install Ubuntu / sda is not detected"
date: 2017-08-24
forum: Installation &amp; Upgrades
---

### Post by belouga18 on 2017-08-24
Hello from France, 
I try to install Ubuntu on some computers without success... And I don't understand why.

I want to install Ubuntu (seul) on 15 computers which have Windows 10 (Old computer Windows 7 upgraded to Windows 10)
On 8 computers : All was OK, and I have install Ubuntu with success.
On 7 computers : It is impossible.

Computers are :
AMD Athlon II X2 255 Processor x2 / DD 320 Go / Mémoire 2Go

I have a USB key with Ubuntu 16.04.3
When I launch installation, I have : 
1) The welcome screen, with the language choice (of course, I take French)
2) The screen of installation preparation (update and others software)
3) The screen with the installation type ... but sda is not detected... (only sdb is detected, corresponding to USB Key LiveCD)

[https://framapic.org/ufKNlWIJLO37/3n9W6CoRPLBQ.jpeg](https://framapic.org/ufKNlWIJLO37/3n9W6CoRPLBQ.jpeg)

I try to erase completely the hard disk with Gparted, créé un table de partition GPT et créé un partition unique en ext4

This is "sudo fdisk -l"
```

Disque /dev/loop0 : 1,5 GiB, 1561751552 octets, 3050296 secteurs
Unités : sectors of 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disque /dev/sda : 298,1 GiB, 320072933376 octets, 625142448 secteurs
Unités : sectors of 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F5A4A07F-F8C5-4091-BD99-C8E4BC129DD4
Périphérique Start       Fin  Secteurs   Size Type
/dev/sda1     2048 625141759 625139712 298,1G Linux filesystem

```

This is "sudo parted -l"
```

Modèle: ATA ST3320418AS (scsi)
Disque /dev/sda : 320GB
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : gpt
Disk Flags:
Numéro  Début   Fin    Taille  Système de fichiers  Nom  Fanions
 1      1049kB  320GB  320GB   ext4
Modèle: General UDisk (scsi)
Disque /dev/sdb : 1992MB
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : msdos
Disk Flags:
Numéro  Début   Fin     Taille  Type     Système de fichiers  Fanions
 1      32,8kB  1607MB  1607MB  primary                       démarrage, caché

```

So, sda is correctly detected. So I don't understand why sda is not detected during installation. So, why installation is impossible ? have Somebody an idea about this ?
And I don't uderstand with it was OK on 8 computers and impossible on 7. I have compare BIOS on 1 impossible and 1 OK and I don't found any difference.

remark : I try to install again Windows 10 and networked perfectly :-(

Thanks in advance for your help.

---

### Post by ajgreeny on 2017-08-24
I suspect this may be a BIOS vs UEFI problem.

Did you boot the USB in BIOS or UEFI mode?  Is the problem machine using BIOS or UEFI?

See [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) and [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by belouga18 on 2017-08-24
> **ajgreeny said:**
> Did you boot the USB in BIOS or UEFI mode?  Is the problem machine using BIOS or UEFI?
The USB start in BIOS mode.
All the machine are using BIOS (as you can see in my first post, the partition table is GPT)
(But I will verify tonight directly )

---

### Post by oldfred on 2017-08-24
Having Windows convert a drive from gpt to MBR causes issues as it does not do conversion correctly.
So if any drives were gpt which Windows requires for UEFI, but then Windows installer booted in BIOS mode, Windows converts drive to MBR(msdos) but leaves the backup gpt partition table.

Linux tools see MBR & backup gpt and in effect do not know what to do, so only offer to erase drive or do nothing.
If that is issue you can use fixparts to remove backup gpt data or gdisk to correctly fully convert to gpt.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
sudo fixparts /dev/sda 

      Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)
gdisk to convert from gpt to MBR
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

If installing in UEFI boot mode, you need to boot installer in UEFI boot mode & drive should be gpt. Windows requires it to be gpt partitioned. You have to have an ESP - efi system partition.
If installing BIOS boot mode you can still use gpt if only booting Linux. Windows requires MBR for BIOS boot, but Ubuntu will boot in BIOS mode from gpt but needs a bios_grub partition.

 It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical (17.04 or later uses swap file if no swap partition) 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by belouga18 on 2017-08-25
My Windows start in Bios mode. Look hereafter.

```
PS C:\Windows\system32> bcdedit
Gestionnaire de démarrage Windows
---------------------------------
identificateur          {bootmgr}
device                  partition=\Device\HarddiskVolume1
description             Windows Boot Manager
locale                  fr-FR
inherit                 {globalsettings}
default                 {current}
resumeobject            {70390bf7-887b-11e7-be1d-b20c42c5110d}
displayorder            {current}
toolsdisplayorder       {memdiag}
timeout                 30
Chargeur de démarrage Windows
-----------------------------
identificateur          {current}
device                  partition=C:
**path                    \Windows\system32\winload.exe**
description             Windows 10
locale                  fr-FR
inherit                 {bootloadersettings}
recoverysequence        {70390bf9-887b-11e7-be1d-b20c42c5110d}
displaymessageoverride  Recovery
recoveryenabled         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \Windows
resumeobject            {70390bf7-887b-11e7-be1d-b20c42c5110d}
nx                      OptIn
bootmenupolicy          Standard

```

and fixparts don't detect MBR partition.
> PS C:\Windows> fixparts32 0:
FixParts 1.0.1
Loading MBR data from 0:
MBR command (? for help): p
** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!
** Extended partitions are not displayed, but will be generated as required.
Disk size is 488397168 sectors (232.9 GiB)
MBR disk identifier: 0x4B636A12
MBR partitions:
                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048      1026047   primary     Y        Y      0x07
   2               1026048    205826047   primary              Y      0x07
   3             205826048    488396799   primary              Y      0x83




Do I have to do Something else ?

---

### Post by oldfred on 2017-08-25
That says it is MBR(msdos), and then you should install in BIOS boot mode.

I prefer to partition in advance with gparted and use Something Else to choose the partition(s) I have created.

But with Windows 10 whether BIOS or UEFI, you must make sure fast start up is off.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by belouga18 on 2017-08-26
I dont uderstand why you speak about windows... My problem is that device sda is not recognize during installation.

News explanations 
I have erase all the sda device with 
- one partition for swap
- one partition for /
- one partition for /home
I used for that a USB key with Ubuntu 16.04.3

```
ubuntu@ubuntu:~$ sudo parted -l
Modèle: ATA ST3250312AS (scsi)
Disque /dev/sda : 250GB
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : msdos
Disk Flags: 

Numéro  Début   Fin     Taille  Type     Système de fichiers  Fanions
 1      1049kB  4195MB  4194MB  primary  linux-swap(v1)
 2      4195MB  56,6GB  52,4GB  primary  ext4
 3      56,6GB  250GB   193GB   primary  ext4


Modèle: General UDisk (scsi)
Disque /dev/sdb : 1992MB
Taille des secteurs (logiques/physiques): 512B/512B
Table de partitions : msdos
Disk Flags: 

Numéro  Début   Fin     Taille  Type     Système de fichiers  Fanions
 1      32,8kB  1607MB  1607MB  primary                       démarrage, caché

```

```
ubuntu@ubuntu:~$ sudo fdisk -l
Disque /dev/loop0 : 1,5 GiB, 1561751552 octets, 3050296 secteurs
Unités : sectors of 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disque /dev/sda : 232,9 GiB, 250059350016 octets, 488397168 secteurs
Unités : sectors of 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x4b636a12

Périphérique Amorçage     Start       Fin  Secteurs   Size Id Type
/dev/sda1                  2048   8194047   8192000   3,9G 82 partition d'échang
/dev/sda2               8194048 110594047 102400000  48,8G 83 Linux
/dev/sda3             110594048 488396799 377802752 180,2G 83 Linux




Disque /dev/sdb : 1,9 GiB, 1992294400 octets, 3891200 secteurs
Unités : sectors of 1 * 512 = 512 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0d998be5

Périphérique Amorçage Start     Fin Secteurs  Size Id Type
/dev/sdb1    *           64 3139583  3139520  1,5G 17 HPFS/NTFS masquée

```

So you can see that I have no windows installed 

But the situation are always the same - installation is not possible because sda dont appaired during device installation type

[IMG]https://framapic.org/ufKNlWIJLO37/3n9W6CoRPLBQ.jpeg[/IMG]

So . what can I do ?

---

### Post by oldfred on 2017-08-26
Was drive ever RAID or RAID setting on in UEFI/BIOS?
Or Intel SRT which looks like RAID to Linux.
Make sure drive is set to AHCI, not RAID nor IDE.

If it was RAID.
 Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
Even if raid not used BIOS may have set parameters, Also check BIOS settings should be AHCI
sudo dmraid -E -r /dev/sda

---

### Post by belouga18 on 2017-08-26
Drive is setting on AHCI in the BIOS

---

### Post by oldfred on 2017-08-26
Did you try running the dmraid command. It not actually RAID, then it will not hurt anything.

---

### Post by belouga18 on 2017-08-27
YES

I have do your raid instruction :
sudo dmraid -E -r /dev/sda

And it's worked...

So, As I want to understand what I do :
I suppose that first installation (Windows 7) was install with raid system.
Then, when somebody have update to windows 10, he put UEFI mode, but some files linked to RAID was still in the hard disk.
So, when I try to install Ubuntu, he was lost.
The instruction sudo dmraid -E -r /dev/sda erase the files linked to Raid, and it's work.

Is that the explanation ?

If yes : I am very surprised that, with the same configuration, Windows 10 installation was possible but not Ubuntu installation.

---

### Post by oldfred on 2017-08-27
For whatever reason Windows seems to ignore some extraneous data on hard drive. Linux is more particular.
But if drive really was RAID, then Windows would have just overwritten it without warning.

---

