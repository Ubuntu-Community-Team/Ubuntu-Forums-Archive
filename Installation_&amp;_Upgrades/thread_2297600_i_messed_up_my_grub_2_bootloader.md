---
title: "i messed up my grub 2 bootloader"
date: 2015-10-05
forum: Installation &amp; Upgrades
---

### Post by twist2 on 2015-10-05
Hallo,

I was experimenting with different linux versions. After i found out kubuntu was the best for me I installed it with encryption. after that i installed win10.

Now i have my test kubuntu on a 30gb partition with no encryption, kubuntu encrypted on a 120gb ssd and win10 on a 250gb ssd.
On the 30gb patition i would like to test more linux versions. the other two os install i will use from now on.

When i start my pc grub 2 only show the old 30gb linux and the win10. i can only boot on my 120 encrypted linux with the [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/) on a thumb drive.

With sudo parted -l   i get an error:

```
Modell: ATA Samsung SSD 840 (scsi)
Festplatte  /dev/sda:  250GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: gpt

Nummer  Anfang  Ende    Größe   Dateisystem  Name                          Flags
 1      1049kB  17,8MB  16,8MB               Microsoft reserved partition  msftres
 2      17,8MB  250GB   250GB   ntfs         Basic data partition          msftdata


Modell: ATA WDC WD15EARS-00Z (scsi)
Festplatte  /dev/sdb:  1500GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos

Nummer  Anfang  Ende    Größe   Typ       Dateisystem  Flags
 1      106MB   1468GB  1468GB  primary   ntfs         boot
 2      1468GB  1500GB  32,2GB  extended
 5      1468GB  1478GB  10,2GB  logical   ext4
 6      1478GB  1487GB  8609MB  logical
 7      1487GB  1500GB  13,4GB  logical   ext4


Modell: ATA SanDisk SDSSDHII (scsi)
Festplatte  /dev/sdc:  120GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: gpt

Nummer  Anfang  Ende   Größe  Dateisystem  Name  Flags
 1      1049kB  538MB  537MB  fat32              boot
 2      538MB   794MB  256MB  ext2
 3      794MB   120GB  119GB


Modell: ATA WDC WD20EARS-00M (scsi)
Festplatte  /dev/sdd:  2000GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: msdos
                                                                                                                                                                                      
Nummer  Anfang  Ende    Größe   Typ      Dateisystem  Flags
 1      1049kB  2000GB  2000GB  primary  ntfs


Warnung: /dev/sde enthält GPT-Signaturen, die anzeigen, dass es eine GPT-Tabelle
hat. Es ist jedoch keine gültige vorgetäuschte MSDOS-Partitionstabelle
vorhanden, die erforderlich wäre. Vielleicht wurde diese zerstört -- eventuell
durch ein Programm, das GPT-Partitionstabellen nicht versteht. Oder vielleicht
haben Sie die GPT-Tabelle gelöscht, und verwenden jetzt eine
MS-DOS-Partitions-Tabelle. Ist dies eine GPT-Partitionstabelle?
Ja/Yes/Nein/No?                                                           

```

i press strg+c because i dont know what to do


```
Ja/Yes/Nein/No? ^C                                                        
Fehler: Sowohl die primäre als auch die Backup-GPT-Tabelle sind defekt. Versuchen Sie, eine neue Tabelle anzulegen und die Partititionen mit Hilfe von Parted's Rettungsmöglichkeiten zu
restaurieren.

Modell: Linux device-mapper (linear) (dm)
Festplatte  /dev/mapper/kubuntu--vg-root:  111GB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: loop

Nummer  Anfang  Ende   Größe  Dateisystem  Flags
 1      0,00B   111GB  111GB  ext4


Modell: Linux device-mapper (linear) (dm)
Festplatte  /dev/mapper/kubuntu--vg-swap_1:  8527MB
Sektorgröße (logisch/physisch): 512B/512B
Partitionstabelle: loop

Nummer  Anfang  Ende    Größe   Dateisystem     Flags
 1      0,00B   8527MB  8527MB  linux-swap(v1)


Fehler: /dev/mapper/sdc3_crypt: unbekannte Partitionstabelle              


```

Can you help me making a new bootloader on the 120 ssd. i want my new linux (encrypted) first than the win10 second and my test kubuntu. if you have problems with the terminal i posted because its German i can translate it.

Greetings

ps. i am writing this on the encrypted linux. and my bios is set to only uefi boot.

---

### Post by oldfred on 2015-10-05
Your drives are mixed gpt & MBR(msdos) partitioning.
Which probably means you have installed one or more systems in BIOS and others in UEFI boot mode. 
UEFI & BIOS are not compatible. Once you start booting in one, you cannot switch to the other. Or from grub you can only boot systems installed in the same boot mode as the install you are booting from. You could even have BIOS based grub on one drive and UEFI based grub on another drive.

Windows only boots from gpt with UEFI.
Windows only boots from MBR with BIOS.

But Ubuntu can boot with either UEFI or BIOS from gpt partitioned drives if you have correct supporting partitions, ESP - efi system partition for UEFI or bios_grub for BIOS.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

How you boot install media for both Windows & Ubuntu UEFI or BIOS mode, is then how it installs.

---

### Post by twist2 on 2015-10-05
Hi,

[http://paste.ubuntu.com/12689904/](http://paste.ubuntu.com/12689904/)

The problem were i pushed strg+c is gone. it was the thumb drive after i removed it no error with parted -l.

---

### Post by oldfred on 2015-10-05
Was sdc originally sda? Both Windows & grub expect the ESP - efi system partition to be on sda. If you moved drives around so the now sdc is not in SATA port 0 then it was changed to sdc.

Your install in sdc is UEFI. Not sure about Windows in sda. I think the efi boot files on sdc will boot the Windows install.

Your install in sdb is BIOS. And it has a Windows boot partition, but I did not think you could use it boot boot a Windows on a gpt drive like your sda? Did you have an old BIOS install of Windows on sdb?

Since two drives are gpt, would would think about converting sdb to gpt and only using UEFI. But if you have lots of data on sdb already then not so easy to do. 
You can dual boot systems in UEFI & BIOS from UEFI boot tab. Some systems require you to turn on/off UEFI or CSM/BIOS boot mode to boot system in that mode. Others may auto switch or know which mode you need and then you also can boot with one time boot key like f10 or f12.

Best of using UEFI to only use UEFI and gpt partitioning. 
Or if you want BIOS only use BIOS/MBR.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

   UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by twist2 on 2015-10-05
Hi,

i want UEFI only. And /dev/sdb:  1500GB - the 3 non ntfs partions are  "/" "/boot" "/home" from my kubuntu test. this is not really important because i will delete it soon. i want give mint a try. so if it makes easier i can delete it right now.
And no sdc is a new drive after i put it into the pc a few days ago i changed nothing. 

So important right now is only a bootloader witch loads kubuntu encryptet on sdc (my normal everyday os) and windows 10 (only for gaming) on sda.

---

### Post by oldfred on 2015-10-05
You need to boot Kubuntu installer in UEFI mode to install.
But grub will want to install to an ESP on sda. Not sure what it will do in your case where it is only on sdc.

I have installed a second Ubuntu on sdb, told it to install grub to ESP I had already created in sdb, it told me during install it was installing to sdb, and it overwrote my main working install's efi partition folder in ESP on sda.

I prefer to partition in advance. And have both an ESP & bios_grub partition on every drive. And an install on every drive. I also like to configure system, so each drive can boot without other drives. With UEFI that can be difficult, but you can disconnect other drives to make sure install is only to one drive. But you may have to reset UEFI entries as when you disconnect a drive it seems to lose those UEFI entries.

How you partition depends a lot on how you are using system and what you have on other drives.

 It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot.

   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.


[LIST=1]
[*]10-25 GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[URL="http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme"]http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme

[/URL]  I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

[URL="http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme"]
[/URL]

---

### Post by twist2 on 2015-10-05
Hi,

ah ^^ And how this help me with my actual problem. all three os are installed. this will only help me when i do a new install. but right now i need a working bootloader for at least my two main os.

---

### Post by oldfred on 2015-10-05
If you go into UEFI/BIOS and turn on BIOS/CSM/Legacy mode and boot from drive that is sdb, does it not boot the install on sdb?

And if you go into UEFI/BIOS and turn on UEFI mode does it not boot the install on sdc?

---

