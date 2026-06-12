---
title: "Installation do not detect a HDD"
date: 2009-11-17
forum: Installation &amp; Upgrades
---

### Post by Exodus78 on 2009-11-17
Hello and Greetings to all.
I'm writing here cause i have a problem installing Kubuntu 9.10 64Bit.

I have a motherboard Gigabyte Ga-k8nf-9 with nForce4 chipset with 3 HDD in serial ata:
160 Gb, 320 Gb and 1000 Gb.

Both 320 and 1000 are for data, while the 160 Gb is used for operating systems.
Well the problem is this: installation program doesn't not see in any way (that i tried) the 160Gb hdd.

Normally it is positioned as sda while 320 is sdb and 1000 is sdc.
I tried to switch the cable posistions of the 3 HDD, i tried to physically disconnect the other 2, i disabled and enabled SMART capability, i deleted with gparted  (of a live version of ubuntu 8.10) all the partitions of the 160 Gb HDD, but installation continues to see only other 2 Hard drives (when they are connected, else it DOESN'T see anything to partition when i have the only 160 connected).

The weird thing is that live version of kubuntu 9.10 is able to see and mount all the partitions of ALL the three hard drives.

I tried to do the same with Kubuntu 9.10 64bit Alternate CD and Ubuntu 9.10 64bit. All the same.
Previous versions had not this problem.

Thanks in advance

---

### Post by darkod on 2009-11-17
There have been some posts with drives having leftovers of raid settings, even if people never set up raid.
But Gparted would make that visible. You could double check with fdisk -l and sudo blkid, what information do they show.

PS. Since the liveCD of Kubuntu 9.10 can see the drive, I believe there is icon Install on the desktop. I don't use that way to instal but since it doesn't see it otherwise, have you tried using that icon to install?

---

### Post by Exodus78 on 2009-11-18
> Since the liveCD of Kubuntu 9.10 can see the drive, I believe there is icon Install on the desktop. I don't use that way to instal but since it doesn't see it otherwise, have you tried using that icon to install?Yes, i only tried the icon of the desktop, except of course for the alternate version of kubuntu.

I'm going to reboot and run again my pc with kubuntu 9.10 live doing fdisk -l and sudo blkid as you suggested me

---

### Post by oldfred on 2009-11-18
I have also heard of some cases where the BIOS had the drive off, but windows & previous Ubuntu installs saw the drive. The new grub/Karmic now follows the BIOS and if the drive is not on it will not see it. 
Check your BIOS settings.

---

### Post by Exodus78 on 2009-11-18
> ...You could double check with fdisk -l and sudo blkid, what information do they show.
Here it is:

fdisk -l
```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x23826494

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11473    92156841    7  HPFS/NTFS

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x99b299b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2446    19647463+   7  HPFS/NTFS
/dev/sdb2            2447       38913   292921177+   5  Extended
/dev/sdb5            2447       38913   292921146    7  HPFS/NTFS

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4dce6899

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      121601   976760001    7  HPFS/NTFS
```


blkid
```
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="E2E8C039E8C00DAB" LABEL="Win7 Operativo" TYPE="ntfs"
/dev/sdb1: UUID="849040C09040BB06" LABEL="XP-320" TYPE="ntfs"
/dev/sdb5: UUID="60A6FCE04D89294B" LABEL="Dati-280" TYPE="ntfs"
/dev/sdc1: UUID="03D08FE54BB1595E" LABEL="Dati-1000" TYPE="ntfs"
```

As i can see, the system detect the sda, but it doesn't appear at the installation process

---

### Post by darkod on 2009-11-18
It might be slightly off topic, but why all three drives have boot mark? Aren't two of them just for data as you said?
Not that it matters for the question why the 160GB is not detected.

---

### Post by Exodus78 on 2009-11-18
> It might be slightly off topic, but why all three drives have boot mark? Aren't two of them just for data as you said?

Ooops, you have right, i didn't noticed it :D.
The sdb1 remained bootable cause of an old intallation of XP that i do not use since prehistory (and still i have to force myself to remove it)
But for the sdc1... i don't know.

I will search an help on how to remove the boot marks on linux.

P.S. Some time ago, i bought the 1000Gb HDD (the sdc). Only kubuntu 9.04 was able to see and use it correctly (as a 1000Gb HDD). XP and the BIOS were able to see a only 32Mb HDD (maybe the cache?).
After many unsuccesful adventures, i wrote an email to the motherboard vendor (Gigabyte) and they answered me this:
> ...Thank you for your kind mail and inquiry. About the issue you
 mentioned, please try to made a DOS bootable USB stick.
 
 2. Put this application on it:
 [http://hddguru.com/content/en/software/2005.10.02-MHDD/](http://hddguru.com/content/en/software/2005.10.02-MHDD/)
 
 3. Boot to DOS.
 
 4. Run MHDD
 
 5.Selecte the drive.
 
 6. Typed HPA into the prompt
 
 7.Selected permanent HPA
 
 8. Entered the value for the LBA number.(Please contact harddisk manufacturer)
 
 9.It should back full size.

....

It is possible that this operation interferred with the topic?
(even if i touched only the sdc)

---

### Post by Exodus78 on 2009-11-18
> Check your BIOS settings

BIOS settings seems to be ok, all the three hard disks are on

---

### Post by Exodus78 on 2009-11-30
I'm Continuing to try.
I just Low Level formatted my 160Gb HDD, and retried again with the karmic installations, but nothing has changed :(.

So i wanted to see if some other distribution of linux can use that HDD.
I tried with Mandriva 2010 (here it is) and it is working, but i want to install Kubuntu ](*,)

Any advice? Things to try... things to check.. any idea?

---

### Post by dhavalbbhatt on 2009-11-30
A couple of things -

1) Try using the alternate CD for installing *buntu

2) If you want to use LiveCD (desktop) version to install *buntu, then boot in the LiveCD environment and go to synaptic and remove any packages related to "dmraid". After you've done this, you should re-boot with the CD in the drive and use it to install the OS.

See if the above can help.

---

### Post by Exodus78 on 2009-12-01
> ...If you want to use LiveCD (desktop) version to install *buntu, then boot in the LiveCD environment and go to synaptic and remove any packages related to "dmraid"....


THANK YOU THANK YOU a lot! :guitar:

It was the dmraid.
I entered the terminal and wrote
```
sudo apt-get remove dmraid
```
Sincerely, i was surprised of this, cause i did not think possible in a live version. But i did not reboot the system; just i launched the installation process to see if it was able to see sda.

> Try using the alternate CD for installing *buntu

I already did before, i tried:

Kubuntu Karmic 64bit
Kubuntu Karmic 64bit alternate CD
Kubuntu Karmic 32bit
Ubuntu Karmic 64bit
Ubuntu Karmic 64bit alternate CD

But with all the version was the same.

Thanks again.

---

