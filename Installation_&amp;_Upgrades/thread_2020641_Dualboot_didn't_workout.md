---
title: "Dualboot didn't workout"
date: 2012-07-08
forum: Installation &amp; Upgrades
---

### Post by jozi on 2012-07-08
Decided a few days a go with win7 needing a resinstal I would give ubuntu a go for day to day pc stuffs. I still need windows for a few specific programs (I don't think they run well on a virtual box or wine but I will try it) so I set about installing it.

I did a bit of disc shuffeling with gparted, 500gig drive partitioned to 25+75+400gig partitions, 25gig to run windows where it is now installed. I did something wrong while installing windows which meant ubuntu wouldn't instal on my 60gig ssd drive, I used the windows installer to format this drive. Back into gparted and I formatted it again but without a file system (not ntfs).

Back into ubuntu to instal it and I got no mention of installing it along side windows, just which drive to chose and for it to take care of partitioning etc.

I've obviously done something wrong and no dont have the option to dual boot. Is there a way to remedy this or a work around that I can do to get a choice of either OS?

As an aside, ubuntu loads so much faster than win7 from my SSD :D

---

### Post by darkod on 2012-07-08
Sounds like it doesn't detect win7 from what ever reason. That's why it didn't offer the "along side" option and is not adding it to the grub2 menu since it has no clue win7 is there.

Can you boot ubuntu and post the outputs of:
```
sudo fdisk -l
sudo parted /dev/sda print all
```

---

### Post by jozi on 2012-07-08
I'm thinking I might have lost my mbr when I re-formatted the SSD drive? Here's the outputs:

```
Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d106d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   116660223    58329088   83  Linux
/dev/sda2       116662270   125044735     4191233    5  Extended
/dev/sda5       116662272   125044735     4191232   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x52ef156c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907026943  1953512448    7  HPFS/NTFS/exFAT

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5781e948

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048    51202047    25600000    7  HPFS/NTFS/exFAT
/dev/sdc2        51202048   204802047    76800000   83  Linux
/dev/sdc3       204802048   206850047     1024000   82  Linux swap / Solaris
/dev/sdc4       206850048   976769023   384959488   83  Linux

```

```
Model: ATA C300-CTFDDAC064M (scsi)
Disk /dev/sda: 64.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  59.7GB  59.7GB  primary   ext4            boot
 2      59.7GB  64.0GB  4292MB  extended
 5      59.7GB  64.0GB  4292MB  logical   linux-swap(v1)


Model: ATA SAMSUNG HD204UI (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ntfs


Model: ATA SAMSUNG HD501LJ (scsi)
Disk /dev/sdc: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system     Flags
 1      1049kB  26.2GB  26.2GB  primary  ntfs
 2      26.2GB  105GB   78.6GB  primary  ext2
 3      105GB   106GB   1049MB  primary  linux-swap(v1)
 4      106GB   500GB   394GB   primary  ext2

```

---

### Post by oldfred on 2012-07-08
We need to see full bootinfo script to tell what is installed where. Often if Windows is installed to sdb or sdc, it will still install its boot files to sda in a 100MB hidden partition. Most users do not realize that and overwrite it. 

You can post link this creates from BootInfo:
Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

Or download script into Ubuntu or liveCD and post the results.txt:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by jozi on 2012-07-08
I'm pretty sure thats what happened, bootfiles installed on sda, I formatted the drive because initially ubuntu wouldnt instal on it.

I will run though those links/steps a little later on a post my resutls.

Thanks.

---

### Post by darkod on 2012-07-08
> **jozi said:**
> I'm pretty sure thats what happened, bootfiles installed on sda, I formatted the drive because initially ubuntu wouldnt instal on it.

I will run though those links/steps a little later on a post my resutls.

Thanks.

Yeah.

There are few things to improve too, if you want to.
First, I would move the 500GB disk to be in the first sata port (usually SATA0 on board). This is not necessary, but windows likes to be on the first disk. In that case that disk would become sda.
Second, in any case, you need to set the boot flag on the win7 partition, and remove it from the ubuntu partition (where it is now on the current sda). You can do that with Gparted from live mode. The boot flag needs to be on the win7 partition.
Third, once the boot flag is there, you can try the Repair This Computer option when you boot with the win7 dvd. You might need to run it 3-4 times to fix everything. Once win7 is booting fine, you know you have the boot files back.
Fourth, once that is done, you will need to boot ubuntu and run:
sudo update-grub
to make it detect win7. In case grub2 was overwritten during the win7 repair, you will need to reinstall it.

---

