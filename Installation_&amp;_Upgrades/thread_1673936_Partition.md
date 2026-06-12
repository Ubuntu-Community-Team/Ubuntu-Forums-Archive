---
title: "Partition"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by Jamezo97 on 2011-01-23
Not too long ago I had one partition on my 160Gig hardrive, which basically took up the whole hard drive.
I wanted to install windows XP on my hard drive, but I have to partition my 160gig hard drive, so i can install both side by side.
Anyway, i installed ubuntu on my 8 gig usb, and started up ubuntu off that. Which allowed me to freely change my 160gig partition. I used a tool called "KDE Partition Manager" to resize my 160gig partition into a 95 gig and a 52 gig, keeping all of my ubuntu files on the 95 gig intact.
Then, i restarted my computer and booted up ubuntu on my hard drive. Everything was fine.
So i now have two partitions on my harddrive. I put in the windows XP ServicePack 1 disk and booted it. When it came to the point where it asked where I wanted to install windows xp, it only had one partition, which was 125gig. Whereas it should have two: 95 and 52 gig.

So, does anyone know how this can be fixed. I can't seem to formulate a question to type into google, bescause it seems to complicated...
So if anyone could help, i would REALLY apreciate it. I try to use Ubuntu as much as I can, but I have to keep using windows to do certain tasks, like play Roller Coaster Tycoon, which sadly doesnt work with ubuntu.
Thanks
James

---

### Post by kansasnoob on 2011-01-23
Boot into Ubuntu and post the output of:

```
sudo parted -l
```

BTW that's a lower case L at the end.

---

### Post by Jamezo97 on 2011-01-23
Here is the output:

> james@james-ubuntu:~$ sudo parted -l
[sudo] password for james: 
Model: ATA ST3160815A (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      8225kB  102GB  102GB   primary   ext4
 3      102GB   159GB  56.5GB  primary   fat32           boot, lba
 2      159GB   160GB  1523MB  extended
 5      159GB   160GB  1523MB  logical   linux-swap(v1)


Model: Generic USB SD Reader (scsi)
Disk /dev/sdb: 1978MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      69.1kB  1976MB  1976MB  primary  fat32


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

I have my SD card reader plugged in BTW
And > /dev/sr0 is obviously my cd drive, which currently has the "Windows XP Installation Disk" inside.

---

### Post by oldfred on 2011-01-24
Normally we install XP to NTFS partitions, but it may have worked with FAT32? I think if you add the boot flag with gparted it will work.

---

### Post by Jamezo97 on 2011-01-24
Yeah tried that too, still no-go.
I think it may have something to do with the partiton table, and that it may be formatted for linux, so windows is then having a hard time trying to find the NTFS partition because it was created for linux...
Maybe... I'm probably going to just going to stuff another hard drive into my computer and install windows on that. That way I have lots of space, and I don't lose my ubuntu data.

---

