---
title: "Installing BURG. GRUB works but I think that isn't corrent"
date: 2013-01-21
forum: Installation &amp; Upgrades
---

### Post by nanoVapor on 2013-01-21
Hi,

I have Ubuntu 12.10 and Win 7 (ubuntu came after the Win instalation) and I have GRUB installed and working fine, booting Ubuntu and Win 7 properly. But I new to Linux world, so...

I already searched about GRUB and BURG on RAID0 but nothing...

I have 2 HDs in RAID0, partitioned in 4:

Partition #1: Sistem Reserved (NTFS)
Partition #2: Win 7 (NTFS)
Partition #3: / (Ubuntu - EXT4)
Partition #4: /home (EXT4)

Here my Boot info:

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/mapper/isw_bbhiajbfic_RAID0 
    and looks at sector 1 of the same hard drive for core.img. core.img is at 
    this location and looks in partition 72 for .

isw_bbhiajbfic_RAID01: _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: sistema de arquivos desconhecido ''

isw_bbhiajbfic_RAID02: _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: sistema de arquivos desconhecido ''
mount: sistema de arquivos desconhecido ''

isw_bbhiajbfic_RAID03: _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: sistema de arquivos desconhecido ''
mount: sistema de arquivos desconhecido ''
mount: sistema de arquivos desconhecido ''

isw_bbhiajbfic_RAID04: _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: sistema de arquivos desconhecido ''
mount: sistema de arquivos desconhecido ''
mount: sistema de arquivos desconhecido ''
mount: sistema de arquivos desconhecido ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabeças, 63 setores/trilhas, 60801 cilindros, total de 976773168 setores
Unidades = setores de 1 * 512 = 512 bytes
Tamanho do setor (lógico/físico): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

Invalid MBR Signature found.


Drive: isw_bbhiajbfic_RAID0 _____________________________________________________________________

Disco /dev/mapper/isw_bbhiajbfic_RAID0: 1000.2 GB, 1000210694144 bytes
255 cabeças, 63 setores/trilhas, 121602 cilindros, total de 1953536512 setores
Unidades = setores de 1 * 512 = 512 bytes
Tamanho do setor (lógico/físico): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_bbhiajbfic_RAID01   *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/mapper/isw_bbhiajbfic_RAID02            206,848 1,031,819,263 1,031,612,416   7 NTFS / exFAT / HPFS
/dev/mapper/isw_bbhiajbfic_RAID03      1,031,819,264 1,105,219,583    73,400,320  83 Linux
/dev/mapper/isw_bbhiajbfic_RAID04      1,105,219,584 1,953,533,951   848,314,368  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/isw_bbhiajbfic_RAID0p1 8256325656324AE5                       ntfs       Reservado pelo Sistema
/dev/mapper/isw_bbhiajbfic_RAID0p2 F4F834EEF834B12A                       ntfs       
/dev/mapper/isw_bbhiajbfic_RAID0p3 551a9a3f-f489-4fa5-93f6-1e7f9988d42f   ext4       
/dev/mapper/isw_bbhiajbfic_RAID0p4 acc9932a-46a5-4786-8394-26f517e512a6   ext4       
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_bbhiajbfic_RAID0
isw_bbhiajbfic_RAID0p1
isw_bbhiajbfic_RAID0p2
isw_bbhiajbfic_RAID0p3
isw_bbhiajbfic_RAID0p4

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/mapper/isw_bbhiajbfic_RAID0p3 /                        ext4       (rw,errors=remount-ro)
/dev/mapper/isw_bbhiajbfic_RAID0p4 /home                    ext4       (rw)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on isw_bbhiajbfic_RAID01


Unknown BootLoader on isw_bbhiajbfic_RAID02


Unknown BootLoader on isw_bbhiajbfic_RAID03


Unknown BootLoader on isw_bbhiajbfic_RAID04



=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/isw_bbhiajbfic_RAID01: Arquivo ou diretório não encontrado
hexdump: /dev/mapper/isw_bbhiajbfic_RAID01: Arquivo ou diretório não encontrado
hexdump: /dev/mapper/isw_bbhiajbfic_RAID02: Arquivo ou diretório não encontrado
hexdump: /dev/mapper/isw_bbhiajbfic_RAID02: Arquivo ou diretório não encontrado
hexdump: /dev/mapper/isw_bbhiajbfic_RAID03: Arquivo ou diretório não encontrado
hexdump: /dev/mapper/isw_bbhiajbfic_RAID03: Arquivo ou diretório não encontrado
hexdump: /dev/mapper/isw_bbhiajbfic_RAID04: Arquivo ou diretório não encontrado
hexdump: /dev/mapper/isw_bbhiajbfic_RAID04: Arquivo ou diretório não encontrado
  No volume groups found

```

But, trying to install BURG, this came up:

```
/usr/sbin/burg-probe: error: cannot find a GRUB drive for /dev/mapper/isw_bbhiajbfic_RAID0p3.  Check your device.map.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
```

Here my device.map (wich I copied from GRUB folder, since the burg-mkdevicemap wasn't identifying my RAID0 partition):

```
(hd0)   /dev/disk/by-id/ata-WDC_WD5000AADS-00S9B0_WD-WCAV94226900
(hd1)   /dev/disk/by-id/ata-WDC_WD5000AADS-00S9B0_WD-WCAV94389897
(hd2)   /dev/mapper/isw_bbhiajbfic_RAID0

```

---

### Post by darkod on 2013-01-21
Grub2 looks installed correctly. If it boots both OSs why do you think it's not installed correctly?

---

### Post by nanoVapor on 2013-01-21
> **darkod said:**
> Grub2 looks installed correctly. If it boots both OSs why do you think it's not installed correctly?

Forget what I said...

I didn't see that Grub2 is installed in the MBR of /dev/mapper/isw_bbhiajbfic_RAID0.. I just saw **=> No boot loader is installed in the MBR of /dev/sda.** and assumed that something wasn't right...

But the post is about the BURG issue... Any device that I use to run burg-install give me that error message...

---

### Post by darkod on 2013-01-21
Maybe it doesn't work correctly with fakeraid?

I think you are risking trouble for nothing. The default ubuntu bootloader seems to be working fine for you. If it didn't, I understand if you wanted to try another solution.

Why would you insist so much to replace the bootloader developed by ubuntu with a bootloader developed by someone and shared? And in a situation where burg gives you problems which is not true of grub?

I don't know anything about burg and I can't help you with that.

---

### Post by nanoVapor on 2013-01-21
I saw on Google Code page of the developer an issue on fakeraid, but it isn't related to my case specific..

Actually, I just wanted to test BURG customization, while GRUB2 only allows a few options like background, colors..

But, anyway, thanks for the replies :)

---

### Post by oldfred on 2013-01-21
It was my understanding that burg is not maintained any more. I see on its launchpad site the last version is from 2010?

       [https://help.ubuntu.com/community/Grub2/Displays#Testing_Fonts_and_Splash_Images](https://help.ubuntu.com/community/Grub2/Displays#Testing_Fonts_and_Splash_Images)
Post Your Grub 2 Themes -  drs305
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)
A Beginner's Guide to Theming GRUB2 - towheedm  & post #28 for grub2 2.00
[http://ubuntuforums.org/showthread.php?t=1534689](http://ubuntuforums.org/showthread.php?t=1534689)

---

