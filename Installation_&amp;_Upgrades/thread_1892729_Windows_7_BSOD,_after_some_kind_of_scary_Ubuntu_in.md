---
title: "Windows 7 BSOD, after some kind of scary Ubuntu installation(WIBU)..."
date: 2011-12-08
forum: Installation &amp; Upgrades
---

### Post by n0rthSH on 2011-12-08
Hi Guys,

During a lecture, I thought, that I could need to install Ubuntu on my new Asus U36S Notebook.
I tried the WIBU installer a couple times, but everytime the installation was finished, the system prompted a message which told me something like "appdata... Permission denied". I had admin and everything. However I wanted to resize my partitions with magic partition and set up ubuntu the "oldschool way" with an image. I shout down my notebook. But when I restarted the Notebook, Windows 7 didnt boot. Just a BSOD. Nothing worked, neither the repairings tools (bluescreen...) nor the safe mode (bluescreen...) Unfortunately the BSOD is shown way too short, to read anyhting and moreover there was not backup cd delivered with the notebook (and I just wanted to make one before making the new partitions) . For some reason the windows boot manager was used. So Ive tried a few how tos in the internet to reinstall gruby. But it didnt work. It still uses the windows boot manager and I still get a BSOD. Im totally desperate. Usually it would be fine, as I would like to get into linux and some programming again, but I really need windows for some applications (for studying). So Ive to get the system running again.
Sorry for my poor english... Ill try to improve it :D!

kind regards from Germany,
Phil alias. n0rth

---

### Post by BC59 on 2011-12-08
If I understood well, you have working Ubuntu installation. If you are speaking about partitions, there is no Wubi installation, because Wubi is installed in Windows as a program, not affecting the partition table.

Let's see now, push CTRL+ALT+T to open a terminal and paste inside this (paste in terminal is SHIFT+CTRL+V):

```
sudo parted /dev/sda print
```

and then this

```
sudo fdisk -l
```

Then please post the results.

---

### Post by n0rthSH on 2011-12-08
Hey BC59,

thanks for your fast response!

1.  

Error: Can't have overlapping partitions.

2.
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x38601c96

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    52436159    26217056   1c  Hidden W95 FAT32 (LBA)
/dev/sda2   *    52430848   443153024   195361088+   7  HPFS/NTFS/exFAT
/dev/sda3       443140096   976771071   266815488    f  W95 Ext'd (LBA)
/dev/sda5       443142144   976771071   266814464    7  HPFS/NTFS/exFAT

kind regards

---

### Post by darkod on 2011-12-08
It looks like Partition Magic left you with overlapping partitions. The end of sda1 is after the start of sda2.

And in win7 it's always better to use Disk Management for resizing partitions.

This recent thread had the same problem and fixparts fixed it.
[http://ubuntuforums.org/showthread.php?t=1892362](http://ubuntuforums.org/showthread.php?t=1892362)

---

### Post by n0rthSH on 2011-12-08
Thanks a lot.  It looks like my post was a little confusing. I wasnt even able to use PM, as Windows didnt boot. 

kind regards

---

