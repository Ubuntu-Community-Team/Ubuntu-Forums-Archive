---
title: "Please help me with GRUB Error 21"
date: 2007-03-27
forum: Installation &amp; Upgrades
---

### Post by fr@mes on 2007-03-27
Hi! I recently installed Ubuntu GNU/Linux 6.10 (Edgy Eft) on my SONY VAIO VGN-AR190G.

I installed on partition "D" or /hda/sdb(i think) for i wish to have dualboot(It's the games that keep me on Windows...) Anyway now that i tried to restart it shows the following


POST Screen -> BIOS PWD -> Loading GRUB Stage1._5. Grub Loading please wait... Error 21

Now i can not access my windows partition where i have some important school work. I didn't backup my data because i alredy had installed Ubuntu 6.10 on my old laptop(Sony VAIO PCG-K23) and did not except this kind of problems. Now i am writing this message from our familys home computer(with WXP :(  )

So if someone could help me i would greatly appreciate it.

(PS. Not afraid to use BASH ::) )

/Billy , Sweden (:confused: )



** Installed from Ubuntu 6.10 livecd (CRC checked, Burned ISO, Checked CD for fault with CD Writing Tool)

---

### Post by mahy on 2007-03-27
Assuming /dev/sda1 is your windows partition and /dev/sda2 is the Linux one:

Boot Ubuntu Live CD

```
sudo mkdir /mnt/aux
sudo mount -t [fs_type] /dev/sda2 /mnt/aux
sudo chroot /mnt/aux
sudo grub-install /dev/sda
```

replace [fs_type] with the name of your Linux filesystem. ext3 by default.

This should help fix it. If not, post the outcome of 'sudo fdisk -l'

---

### Post by confused57 on 2007-03-27
You also might want to burn a copy of the Super Grub Disk(500 kb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it may be able to boot your Window's partition

You can also reinstall grub with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

As mahy suggested, wouldn't hurt to post the output of:
```
sudo fdisk -l
```

---

### Post by fr@mes on 2007-03-27
Yes, i have the windows and ubuntu set up as you have wisely foreseen. But mount returns me the following: 

mount: wrong fs type, bad option, bad superblock on /dev/sda2, missing codepage or other error In some cases useful info is found in syslog - try dmesg | tail or so

:S

EDIT: I just did a fdisk list and it shows /dev/sdb1 as linux and /dev/sdb2 as swap so i assume i should try to change /dev/sda to /dev/sdb1? it still lists /dev/sda2 as NTFS, and sda1 as Compaq 
Diag... :S


i am a slow write at night so i didn't notice that you had posted confused57...



***

now that i try the sudo grub-install /dev/sdb1
it says:

/dev/sdb1/: Not found or not a block device

---

### Post by Southtown on 2007-03-27
There should be no number after "/dev/sdb".
```
sudo grub-install /dev/sdb
```

---

### Post by ChristopherL on 2007-03-30
Have exactly the same problem.

But now I reinstalled with some other settings and
now I got only: Loading GRUB Stage1._5. Grub Loading please wait...

Are Ubuntu having trouble with Raid?

When I type fdisk -l, I got this:

/dev/sda 100.0 GB
Device boot  - Start      - End         - Blocks         - Id  
/dev/sda1     -1          -12123     -97377966        -83
/dev/sda2     -12124   -12161    -305235             -5
/dev/sda5     -12124   -12161    -305203+          -82
 
- System 
  -Linux
  -Extended
  -Linux swap / Solaris

/dev/sdb 100.0 GB

Someone knows how to fix this?

---

