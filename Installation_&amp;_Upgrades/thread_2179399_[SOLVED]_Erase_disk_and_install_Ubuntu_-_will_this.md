---
title: "[SOLVED] Erase disk and install Ubuntu - will this erase data on all drives?"
date: 2013-10-08
forum: Installation &amp; Upgrades
---

### Post by JYzeeeJ on 2013-10-08
I would like to install Xubuntu onto my C: hard disk (which has Vista on it).

I have a second hard disk (D:) that I haven't backed up yet. I was thinking I would be able to install on C:, and then copy from D: at my leisure. But know I'm wondering whether this "erase disk and install ubuntu" will format everything! Will the install give my options on the next step?

This is the output from fdisk -l

```
[FONT=arial]Disk /dev/sda: 120.0 GB, 120034123776 bytes[/FONT]
[FONT=arial]255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=arial]Disk identifier: 0xe13269ca[/FONT]

[FONT=arial]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sda1            2048    20482047    10240000   27  Hidden NTFS WinRE[/FONT]
[FONT=arial]/dev/sda2   *    20482048   127467519    53492736    7  HPFS/NTFS/exFAT[/FONT]
[FONT=arial]/dev/sda3       127467520   234438655    53485568    7  HPFS/NTFS/exFAT[/FONT]

[FONT=arial]Disk /dev/sdc: 1993 MB, 1993342976 bytes[/FONT]
[FONT=arial]2 heads, 63 sectors/track, 30898 cylinders, total 3893248 sectors[/FONT]
[FONT=arial]Units = sectors of 1 * 512 = 512 bytes[/FONT]
[FONT=arial]Sector size (logical/physical): 512 bytes / 512 bytes[/FONT]
[FONT=arial]I/O size (minimum/optimal): 512 bytes / 512 bytes[/FONT]
[FONT=arial]Disk identifier: 0x0026b695[/FONT]

[FONT=arial]   Device Boot      Start         End      Blocks   Id  System[/FONT]
[FONT=arial]/dev/sdc1   *          32     3893247     1946608    6  FAT16[/FONT]
```

So I believe sda1 and sda2 are C: and sda3 is D: - is that correct?

---

### Post by arubislander on 2013-10-08
The output of fdisk -l shows that you only have one **hard disk drive** with three **partitions** on it. 
The option to erase disk and install ubuntu will reformat the  **drive**, wiping out all the **partitions** in the process. 
/dev/sda1 is probably the recovery partition. It is Hidden, and thus invisible to Windows during normal operation.
/dev/sda2 had the Boot flag set, and is the C:\ under Windows
/dev/sda3 is D:\

What you want to do is choose the last option 'Something Else' I think it is labeled, and then manually select the /dev/sda2 partition and tell the installer to format that and mount it as / (the root of the Linux filesystem)

But only do this if you are defenitely sure that you really want to get rid of Vista alltogether.

---

### Post by JYzeeeJ on 2013-10-08
Thanks arubislander.

There is not a lot of data on sda3 so I might back it up then let the installer wipe everything. Would it keep the size of the partitions, or just reset everything and leave 1 drive/partition?

---

### Post by westie457 on 2013-10-08
arubislander is correct. 
The wipe drive and install option will completely clear the hard drive of all information with no way of recovering it. His suggestion to use the 'something else' option if used properly will preserve the current Windows and hidden partitions.

Using Windows tools shrink your D: drive (/sda2) to create some space for Ubuntu. Leave this space as unallocated, then run the Ubuntu installer and select the 'something else' option.

This way should leave you with a dual-booting system and the recovery software to restore Vista to the state when your computer left the factory.

---

### Post by Elfy on 2013-10-08
> **JYzeeeJ said:**
> Thanks arubislander.

There is not a lot of data on sda3 so I might back it up then let the installer wipe everything. Would it keep the size of the partitions, or just reset everything and leave 1 drive/partition?

It would remove all existing partitions and start again.

In addition to creating the / partition you'll likely want to create a swap partition.

If you delete sda2 - you can then create partitions as you wish.

I'd create an extended partition first.

Then create a swap then /  both as logical partitions in the extended.

I'd leave sda3 - you can use that as a data partition and mount that at boot if you wish with fstab.

[https://help.ubuntu.com/community/Partitioning/Swap](https://help.ubuntu.com/community/Partitioning/Swap)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by JYzeeeJ on 2013-10-08
> **Elfy said:**
> 
In addition to creating the / partition you'll likely want to create a swap partition.


Will it give me the option to create the swap partition after selecting the [COLOR=#000000]**Erase disk and install Ubuntu **[/COLOR]option?

Thanks for the links, it looks like I need to create a 2GB swap file (as I have 2GB RAM and 120GB HD).

---

### Post by Elfy on 2013-10-08
If you use the erase and install option it will do so itself.

---

### Post by JYzeeeJ on 2013-10-08
Thanks. Marked as solved.

---

