---
title: "Win XP alongside with Ubuntu"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by An Sanct on 2011-03-11
Hello!

I have Ubuntu Maverick on my sda and would like to have windows XP on sdb, with GRUB and everything, has anyone got experience doing that?

I tried to install in a virtual machine, but windows did not want to install unless there was a XP (boot) partition on the first disk ...
I have my machine here and can open it (unplug sda for instance).

Any suggestions.

---

### Post by Grenage on 2011-03-11
It should be simple; Windows will overwrite your existing bootloader with its own, but you can easily replace that with a live CD (ubuntu install disc will do).

Make sure that you specify the right partition when installing Windows, then boot off the live CD.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

If you unplug the Ubuntu disc, then Windows will install the boot-loader on its own drive, and you'd need to do a grub-update from the Linux install.  That, or specify the drive to boot via BIOS boot menu.

---

### Post by kansasnoob on 2011-03-11
Are both drives SATA? Or both IDE? Or a mix of the two?

---

### Post by An Sanct on 2011-03-11
Both SATA, 

> If you unplug the Ubuntu disc, then Windows will install the boot-loader  on its own drive, and you'd need to do a grub-update from the Linux  install.  That, or specify the drive to boot via BIOS boot menu.
I figured this could go, I just didn't want to have problems between Ubuntu and Windows (Windows killing my GRUB every time I start them, try to format sda, etc etc etc ...)

PS. The only reason for me going to a dual boot with windows is gaming, I play a game or two a year, so if it would be a hassle, I'd just drop it...

---

### Post by Grenage on 2011-03-11
> **An Sanct said:**
> Both SATA, 


I figured this could go, I just didn't want to have problems between Ubuntu and Windows (Windows killing my GRUB every time I start them, try to format sda, etc etc etc ...)

PS. The only reason for me going to a dual boot with windows is gaming, I play a game or two a year, so if it would be a hassle, I'd just drop it...

Oh no, it should be no problem; about the only time Windows will overwrite the MBR is during an install, or use of the fixboot command.  I use a dual-boot at home; I imagine rather a lot of us do!

---

### Post by An Sanct on 2011-03-11
I have a dual boot of Maverick/Natty right now. And even Natty messed up my GRUB =)

Thanks for the answer! 
(I will mark this thread as solved with an explanation of "what I did" when I'm finished installing)

---

### Post by An Sanct on 2011-03-11
OK, I'm back ...

Something didn't work as planned (plans are so good, sometimes :))

So, with gparted I formatted the first partition of sdb (130Gb of 1Tb) to NTFS, unplugged sda, inserted the CD and found out, that I have GPT partitioning and windows XP 64bit refuse to install there...

So, according to the fact, that sda is MBR and contains my working Ubuntu, windows want an 8Mb partition there. I'm afraid that that would mess up the whole Ubuntu install...

Any ideas? 
Maybe how to convert GPT to MBR without moving all the data from the disk and reformatting?
Or maybe, is it safe to allow windows to hug that 8Mb, what will happen if I allow that?

---

### Post by kansasnoob on 2011-03-12
Is sdb a blank drive? That is, it has no data you wish to retain?

If so, being it's 1TB I think you should be able to select Device > Create Partition Table in Gparted and create a new MSDOS partition table.

[ATTACH]185826[/ATTACH]

Actually it might be smart to first post the output of both of these commands with both drives attached:

```
sudo fdisk -l
sudo parted -l
```

BTW that's a lower case L at the end of each.

---

### Post by srs5694 on 2011-03-12
> **An Sanct said:**
> So, with gparted I formatted the first partition of sdb (130Gb of 1Tb) to NTFS, unplugged sda, inserted the CD and found out, that I have GPT partitioning and windows XP 64bit refuse to install there...

So, according to the fact, that sda is MBR and contains my working Ubuntu, windows want an 8Mb partition there. I'm afraid that that would mess up the whole Ubuntu install...

If it were the other way around you'd have no problems -- Linux is fine on a GPT disk, but Windows is much more limited....

> Any ideas? 
Maybe how to convert GPT to MBR without moving all the data from the disk and reformatting?
Or maybe, is it safe to allow windows to hug that 8Mb, what will happen if I allow that?

You can use my [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) program to non-destructively convert from GPT to MBR; however, there are caveats:


[list]
[*]Depending on how many partitions you've got and what they are, you might not be able to convert completely.
[*]Your boot loader configuration may be disrupted (but if you're booting Linux from /dev/sda and using /dev/sdb only for data, this shouldn't be an issue).
[*]Not so much a caveat, but a "gotcha:" You'll have to use the conversion's user interface to manually adjust the type code of any Linux data partition(s), since in GPT Linux and Windows data partitions share a single type code, but in MBR they've got separate type codes.
[*]*Do not* use the version in the Ubuntu repositories; it's hopelessly out of date (0.5.1 vs. the current 0.7.0) and has bugs in its GPT-to-MBR conversion process. Download the .deb file for your architecture from [here.](https://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.0/gdisk-binaries/) (Note to future readers: Back up the tree to find whatever the current version is; that's a link to the current version as of March 12, 2011.)
[/list]


Only the first of those is a potential deal-breaker, and it's not certain that you'll run into that problem -- it'll be fine if you've got no more than four partitions, for instance.

If you can't get gdisk to work, please post back with the output of the following two commands, posted between [noparse]```
[/noparse] and [noparse]
```[/noparse] strings:

```

sudo parted /dev/sda unit s print
sudo parted /dev/sdb unit s print

```

Those commands will show us how your disks are partitioned, so we may be able to offer some alternatives tailored to your situation rather than just general advice.

---

### Post by An Sanct on 2011-03-13
kansasnoob:

No, the disk is almost full (its my "data store")

the results...

of fdisk -l
```

Disk /dev/sda: 64.1 GB, 64105742336 bytes
255 heads, 63 sectors/track, 7793 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a3190

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7794    62601216   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa09ea09e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121602   976762583+  ee  GPT

```of parted -l

```

Model: ATA TS64GSSD25S-M (scsi)
Disk /dev/sda: 64.1GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  64.1GB  64.1GB  primary  ext4         boot


Model: ATA WDC WD10EADS-00M (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  140GB   140GB   ntfs            Basic data partition
 2      140GB   279GB   140GB   ext4
 3      279GB   966GB   687GB   ext4
 4      966GB   1000GB  34.4GB  linux-swap(v1)

```srs5694:

I downloaded your software and will post back when I get the results...

until then, here are the results of
```

sudo parted /dev/sda unit s print 
sudo parted /dev/sdb unit s print

``````

[SDA results]

Model: ATA TS64GSSD25S-M (scsi)
Disk /dev/sda: 125206528s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End         Size        Type     File system  Flags
 1      2048s  125204479s  125202432s  primary  ext4         boot

------------------------------------------------------------------------
[SDB results]

Model: ATA WDC WD10EADS-00M (scsi)
Disk /dev/sdb: 1953525168s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start        End          Size         File system     Name                  Flags
 1      2048s        272631807s   272629760s   ntfs            Basic data partition
 2      272631808s   545261567s   272629760s   ext4
 3      545261568s   1886416895s  1341155328s  ext4
 4      1886416896s  1953523711s  67106816s    linux-swap(v1)

```So I figured, if XP (being old and all) wouldn't want to work, maybe MSs best and newest OS, Windows7 will handle this situation.

(personal note from me: all mentioned software is **legal**, bought or public beta/preview)

Windows 7, like XP, just lets you wipe the disk, but doesn't want to install... disappointed ...

---

### Post by An Sanct on 2011-03-13
haha :)

> **x** - Enter the experts' menu. Using this option provides access to features you can use to get into even more trouble than the main menu allows. So I should use the "**g**" or "**h**" option?

---

### Post by srs5694 on 2011-03-13
> **An Sanct said:**
> So I should use the "**g**" or "**h**" option?

Use "g" to convert fully to MBR. It should be possible for you -- just barely. You've got four partitions, with no space between them, so only the first one will be convertible to logical form, and that won't work if you intend to install Windows on it. Thus, you must ensure that all the partitions are primary. (Use the "r" option in the conversion menu to convert partition 1 to primary if it turns up as logical initially.)

If you need to add more partitions in the future, you'll need to resize partitions in such a way that you can convert what you want into logicals.

Another option entirely would be to move your Linux installation to /dev/sdb and install Windows on /dev/sda. Windows itself will fit there, and Windows 7 will be able to read the GPT disk as a data disk, although it won't boot from it. Windows XP won't read GPT disks, though, at least not without third-party tools to help it.

---

### Post by An Sanct on 2011-03-13
hm ... I'm confused :)

I assume, that "sudo" has to be used before gdisk. then it says:
> Type device filename, or press <Enter> to exit:
and whatever I enter, it says
> Problem opening %whateve_entered% for reading! Error is 2.
The specified file does not exist!

---

### Post by An Sanct on 2011-03-13
Okay, I figured it out, with the help of "man gdisk", I should have entered "/dev/sdb"

---

### Post by An Sanct on 2011-03-13
Great :) I've got it working!

Thanks to you all!

---

