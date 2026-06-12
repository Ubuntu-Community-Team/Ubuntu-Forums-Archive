---
title: "unrecognised disk label (macbook hd)"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by shakshirley on 2011-12-13
Hey !
I have a macbook without mac os. When I tried yesterday to run a new os (ubuntu 11/04) on one of my partitions, but after that nothing is bootable anymore (when I press "alt" during boot, there's only the livecd)
So I tried to run gparted from the livedisk but I had an "unrecognised disk label" error. Glups. But I don't think it's erased, because I still have something when I run fdisk : 

(sorry it's in french - i guess it's quite similar to the english one ?)

```

ubuntu@ubuntu:~$ sudo fdisk -l  

ATTENTION : identifiant de table de partitions GPT (GUID) detecté sur "/dev/sda" ! L'utilitaire fdisk ne supporte pas GPT. Utilisez GNU Parted.   

Disque /dev/sda: 250.1 Go, 250059350016 octets 
255 têtes, 63 secteurs/piste, 30401 cylindres 
Unités = cylindres de 16065 * 512 = 8225280 octets 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Identifiant de disque : 0x00000000  

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1               1       24354   195617792    b  W95 FAT32 
/dev/sda2   *       24354       24354         977   ee  GPT 
/dev/sda3           29134       30141     8087552   83  Linux 
/dev/sda4           30141       30402     2097152   82  Linux swap / Solaris


```

Here is how it's supposed to be :
/dev/sda1 : documents fat32 (more than 120go)
/dev/sda2 : brand new ubuntu 11.04 (between 20 and 30go)
/dev/sda3 : old ubuntu, with flag boot (between 7 and 10go)
/dev/sda4 : swap 2go


Does anybody know how to fix it ? Any idea ?
Thanks !!!

---

### Post by coffeecat on 2011-12-13
Welcome to the forum!

You have a GUID partition table (GPT) which fdisk does not support.

> L'utilitaire fdisk ne supporte pas GPT. Utilisez GNU Parted. 

A GUID partition table keeps an mbr-type partition table in the first sector of the disk, and I guess this is what fdisk is reading. In your situation this may be misleading, so we need to see the output of parted. This will probably give a similar error to Gparted, since Gparted uses parted as a back-end, but let's see the output anyway. Post the output of:

```
sudo parted /dev/sda print
```

Please post the output between [noparse]```
 and 
```[/noparse] tags, not quote tags. This is to preserve formatting. Perhaps you could edit your first post and replace the quote tags around the fdisk output with code tags in order to make it more readable. Although the fdisk output may not be useful, it would be helpful to be able to see it formatted in columns.

---

### Post by shakshirley on 2011-12-13
Thank you for your reply, coffeecat _

I tried with parted but it's the same unrecognised disk label error...

```
Erreur: Impossible d'ouvrir /dev/sda - étiquette de disque non reconnue.
```

Bad news, uh ?

ps : first post edited ;)

---

### Post by coffeecat on 2011-12-13
To be honest, I have little experience of GPT partition tables. Or at least I have little experience of repairing them.

I don't suggest you use this just yet, unless you feel confident to do so, but have a look at this link:

[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

There is a section, "Repairing GPT disks", which might be of help.

While you are digesting that, I'll pm another forum member who would know much more than I about GPTs, and ask them to have a look at this thread. They are in another time-zone so unlikely to be on-line for a few hours, so you'll need to wait a bit.

---

### Post by shakshirley on 2011-12-13
Thanks a lot
I'm reading the gdisk documentation. I get some more information about my disk, it may help... At least, it shows that's a real mess :s

```

Command (? for help): p
Disk /dev/sda: 488397168 sectors, 232.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): BD44D286-4018-4B31-AA59-FC4F1B6F8EBF
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 2-sector boundaries
Total free space is 2349 sectors (1.1 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048       391237631   186.6 GiB   0700   &#65533;!8&#65533;`&#65533;
   2       391237632       391239585   977.0 KiB   EF02  
   3       468027392       484202495   7.7 GiB     EF00    &#65533;!; 
   4       484202496       488396799   2.0 GiB     8200  @ &#65533;!;@
   5       391239586       460214195   32.9 GiB    0700  
   6       460214196       468027391   3.7 GiB     8200

```

The first partition ("0700") is still intact. But I have now an efi of 7gb ("EF00"), two swaps ("8200") and... a bios partition ("EF02") ???
I forgot to say that I tried to install Fedora 16 before Ubuntu. I guess there was a problem during the modification of partition table...

To be continued

---

### Post by coffeecat on 2011-12-13
The BIOS partition is needed for grub's core.img with a GUID partition table if you have BIOS machine. But since you have a Mac, which is an EFI machine not a BIOS one, it shouldn't be there. Perhaps the Fedora installer did something odd. I thought Fedora was moving to GPT anyway, so it shouldn't have made a mess of it.

I've pm'd the other forum member. I'm sure the answer to this following will be no, but if you run the Ubuntu live CD (or USB) are you able to mount and read any of the partitions?

---

### Post by shakshirley on 2011-12-13
No, I can't access any of the partitions.
But my precedent post was incomplete. When I launch gdisk :

```

GPT fdisk (gdisk) version 0.6.14

Caution: invalid main GPT header, but valid backup; regenerating main header
from backup!

Caution! After loading partitions, the CRC doesn't check out!
Warning! Main partition table CRC mismatch! Loaded backup partition table
instead of main partition table!

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: damaged

Found valid MBR and corrupt GPT. Which do you want to use? (Using the
GPT MAY permit recovery of GPT data.)
 1 - MBR
 2 - GPT
 3 - Create blank GPT

```

So the previous post was with GPT-choice. But I tried again with MBR-choice :

```

Your answer: 1

Command (? for help): p
Disk /dev/sda: 488397168 sectors, 232.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 05FFA8C1-C704-4C01-A4C5-F6A9B01CC317
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 488397134
Partitions will be aligned on 2048-sector boundaries
Total free space is 76792109 sectors (36.6 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048       391237631   186.6 GiB   0700  Linux/Windows data
   3       468027392       484202495   7.7 GiB     0700  Linux/Windows data
   4       484202496       488396799   2.0 GiB     8200  Linux swap

```

And this is closer to what I want and tried to do (with a missing partNumber2 for a new linux partition) I think I was using a "fake" MBR system and Fedora 16, recognising it was actually a GPT system made an hybrid MBR-GPT solution that broke everything. Or something like that. Kind of.
I don't know enough for the moment to try a repair so I will wait for the other forum member. And keep reading gdisk doc : that's helpful, I don't understand everything but that's what I needed to learn. Thank you for the help :)

---

### Post by oldfred on 2011-12-13
I am one the coffeecat asked to help. I do use gpt on two drives and a USB flash drive just to learn a little about gpt, but I do not know Macs and how they are configured. 

As I understand a Mac it is a UEFI/EFI system and uses gpt. With Windows it converts to the hybrid MBR system as most Windows installs are MBR and I guess the Windows UEFI install is not compatible with the Mac EFI version. If only Linux I would think you can stay with gpt and not have the hybrid system, but I do not know how the Mac boots with grub & its own boot loader. 

With Linux & Windows UEFI, the efi boot partition has to be a FAT formated partition and the first partition on the drive. It has the boot flag which is not really the same as a boot flag in BIOS/MBR but sets the gpt type to know it is where the boot files are.

This has more info on Mac & Linux EFI systems:
[https://help.ubuntu.com/community/UEFIBooting#Apple_Mac_EFI_systems](https://help.ubuntu.com/community/UEFIBooting#Apple_Mac_EFI_systems)

---

### Post by shakshirley on 2011-12-14
Okay, finally I fixed the disk label error with gdisk (choosing restauration of mbr, option 1)
So now I can access and copy my data :) 
Next step : erasing everything and stop using hybrid mbr that I don't need, haha, it seems that you're right, oldfred :P The biggest challenge will be : how to boot, but I'm sure your documentation will help a lot.
I keep you update !

---

