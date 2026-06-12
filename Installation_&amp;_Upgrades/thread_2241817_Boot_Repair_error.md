---
title: "Boot Repair error"
date: 2014-08-28
forum: Installation &amp; Upgrades
---

### Post by ddhuy on 2014-08-28
I cannot manange to get Boot Repair to fix my dual boot of Windows 8 and Ubtuntu. Here is the link with Boot Repair results:
[http://paste.ubuntu.com/8170405/](http://paste.ubuntu.com/8170405/)

The error I get is:
[INDENT]The boot files of [The OS now in use - Ubuntu 14.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
[/INDENT]

I have made a seperate partition to use as boot partition (sda8), but in Boot Repair I am unable to select it. I can only use "Seperate /boot/efi partition" and there select the existing efi partition (sda2), the "Speperate /boot partition" is greyed out.

[IMG]http://i.imgur.com/sDFW0d5.png[/IMG]

[IMG]http://i.imgur.com/2BpFYu0.png[/IMG]

[IMG]http://i.imgur.com/kPRjIi7.png[/IMG]

---

### Post by fantab on 2014-08-28
```
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1   500,118,191   500,118,191  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048     2,050,047     2,048,000 Windows Recovery Environment (Windows)
[COLOR=#008000]/dev/sda2       2,050,048     2,582,527       532,480 EFI System partition[/COLOR]
/dev/sda3       2,582,528     2,844,671       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       2,844,672   266,737,663   263,892,992 Data partition (Windows/Linux)
/dev/sda5     464,097,280   500,117,503    36,020,224 Windows Recovery Environment (Windows)
/dev/sda6     428,077,056   464,097,279    36,020,224 Swap partition (Linux)
/dev/sda7     268,785,664   428,077,055   159,291,392 Data partition (Linux)
[COLOR=#b22222]/dev/sda8     266,737,664   268,785,663     2,048,000 EFI System partition[/COLOR]
```

```
parted -l:

Model: ATA SAMSUNG MZ7TD256 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
1      1049kB  1050MB  1049MB  ntfs                                          hidden, diag
2      1050MB  1322MB  273MB   fat32           EFI system partition          boot
3      1322MB  1456MB  134MB                   Microsoft reserved partition  msftres
4      1456MB  137GB   135GB   ntfs            Basic data partition          msftdata
[COLOR=#b22222]8      137GB   138GB   1049MB  ext4                                          boot[/COLOR]
7      138GB   219GB   81.6GB  ext4
6      219GB   238GB   18.4GB  linux-swap(v1)
5      238GB   256GB   18.4GB  ntfs                                          hidden, diag
```

Only one ESP [Efi System Partition] per HDD is recommended.
Also in certain OEM UEFI ESP must be upfront or within the first 100Gb of HDD.

Using Gparted from Live Ubuntu remove the 'boot' flag from the /dev/sda8 partition (the one highlighted in red).

Shutdown. Reboot.

---

