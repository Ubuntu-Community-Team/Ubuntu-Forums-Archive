---
title: "lot of issue during install"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by Seylar on 2010-07-04
Hi guys it's been one day that i try without succes to install ubuntu on my computer. i have 2 HD samsung spinpoint 750 go which are in RAID 0. and my mother card is a gigabyte GA-MA790XT-UD4P. i tried to install ubuntu from the original CD 10.04 (the one we can ask for) and from an USB stick where the version here is a 64 bits. both of them fail when i have to install, first i had an error that he can't make the ext4 part on my SATA RAID disk, but when i tried many things on my bios i now have an error while launching the installation and put me on the live CD, and when i still try to install Ubuntu, i says that there is a gmicron_GRAID problem or something like that. please guys help me, thanks =)

---

### Post by darkod on 2010-07-04
For installation on raid you should use the Alternate Install CD, not the standard Desktop CD.

Also, will you dual boot with windows on the raid? If not, it's better not to use the BIOS raid, to disable it, and instead use ubuntu software raid. But you still need to use the alternate cd for that.

---

### Post by Seylar on 2010-07-04
thanks for you answer, well ok for the CD i'm gonna look for that
i just have ubuntu well i will ^^'

---

### Post by darkod on 2010-07-04
For only ubuntu software raid is better. Short guide about it:
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

For raid0 make sure you create the separate /boot primary partition outside the array, as it says in that guide. Software raid can't work as raid0 without that partition being separate outside the array. At least that's what it says there.

---

### Post by Seylar on 2010-07-04
sorry but i can't find the alternate cd version, where can i download it please?

---

### Post by darkod on 2010-07-04
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

Scroll to the bottom, you have all images. Select the alternate 32bit or 64bit, as you wish. Also from there you can get just the torrent file (ending in .torrent) and download using a torrent client.

---

### Post by Seylar on 2010-07-04
thanks a lot. i'm gonna try this

---

### Post by Seylar on 2010-07-04
ok i start to create the partition but i don't have any idea of the weight of the partitions, what do you recommend to me?

sorry for my newbie questions :s

EDIT: finaly succeded to install, but no boot ...,any ideas?

---

### Post by darkod on 2010-07-05
Did you select a disk where to install grub2? And are you booting with that disk as first option in BIOS?

When asked where to install grub2 in text mode, you need to select a disk by using the Space bar, it will put a * mark next to it. Don't hit Enter to select it, it doesn't select anything, just continues the process with nothing selected.

---

### Post by Seylar on 2010-07-05
i finished my install, but when ubuntu launch, i have this message during the loading:
> 
udevd-work[128]: inotify_add_watch(6, /dev/dm-2, 10) failed: no such file or directory
ALERT! /dev/disk/by-uuid/badc5269-a0f3-4b97-b644-4754cfe2cc37 does not exist. Dropping to a shell!!
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash) 

---

### Post by darkod on 2010-07-05
OK, now use the standard desktop cd to boot into live mode, and post the output of:

sudo blkid

---

### Post by Seylar on 2010-07-05
this is the message:
> ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs"
/dev/sda: TYPE="promise_fasttrack_raid_member"
/dev/sdb: TYPE="promise_fasttrack_raid_member"

---

### Post by darkod on 2010-07-05
I thought you were going to use software raid, not the fakeraid?

For software raid, the BIOS raid settings need to be disabled. Or these are just settings remained from when you were trying the fakeraid.

What are you trying to set up first of all, fakeraid or ubuntu software raid?

---

### Post by Seylar on 2010-07-05
i tried the software, i put the hard drives as IDE in my bios, if i put them in AHCI i can't use my CD drive

---

### Post by darkod on 2010-07-05
Does putting them in IDE automatically disable raid? There might be separate setting that needs to be disabled.

Also, to get rid of the raid meta data, from live mode do:

sudo dmraid -r -E /dev/sda
sudo dmraid -r -E /dev/sdb

That should remove the meta data. After that try to run:

sudo fdisk -l

and

sudo blkid

and post the results. You did create the separate /boot partition for softraid right?

---

### Post by Seylar on 2010-07-05
i did a /home, /swap/ and / in raid
and a boot which wasn't in raid

---

### Post by Seylar on 2010-07-05
here is the results: 
> ubuntu@ubuntu:~$ sudo fdisk -l
            
Disque /dev/sda: 750.2 Go, 750156374016 octets
255 têtes, 63 secteurs/piste, 91201 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identifiant de disque : 0x000ccf64

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda1   *           1        6079    48827392   fd  Linux raid autodetect
/dev/sda2            6079       91202   683744257    5  Etendue
/dev/sda5            6079        6566     3905536   fd  Linux raid autodetect
/dev/sda6            6566        6687      975872   83  Linux
/dev/sda7            6687       91202   678860800   fd  Linux raid autodetect

Disque /dev/sdb: 750.2 Go, 750156374016 octets
255 têtes, 63 secteurs/piste, 91201 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identifiant de disque : 0x00015ccb

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdb1               1        6079    48827392   fd  Linux raid autodetect
/dev/sdb2            6079       91086   682811393    5  Etendue
/dev/sdb5            6079        6566     3905536   fd  Linux raid autodetect
/dev/sdb6            6566       91086   678904832   fd  Linux raid autodetect
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ 



---

### Post by darkod on 2010-07-05
If sda6 is your /boot partition, it is logical. If I'm not wrong, it needs to be primary partition.

Not just outside the array, but primary partition outside the array. You would usually create it at the start of the disk. You can make another one on the other disk too, for symmetry even if you don't use it.

---

### Post by Seylar on 2010-07-05
ok just tried to reinstall but i've got a problem just after i made the partitions, the RAID, and give back the RAID part /home, /, swap ... it fail:
the file suppression in conflict failed.
The installation has to delete system files, but this operation can't be done. The install can't proceed

---

### Post by ronparent on 2010-07-05
I have been advising any one attempting to install any flavor of 10.04 on a raid to pre-create all of their target partitions for the install with gparted in an earlier ubuntu version (either a functioning system or live cd) prior to attempting to run the install. Otherwise, since gparted in 10.04 doesn't seem to work on raid partitions, the partitioning step will fail. Once the pre-created partitions are selected _without formatting_ for the install things should proceed normally. If you intend to boot from the raid you will need additional instruction to complete a grub install. Post how you do.:p

---

### Post by Seylar on 2010-07-05
well i just forgot to put them in a format mode active in the partition part, then it actually worked :D so i'm on ubuntu and thank you for the help, i guess i'm gonna make a how to to the french community from my experience ^^ again thanks a lot to you ;)

---

