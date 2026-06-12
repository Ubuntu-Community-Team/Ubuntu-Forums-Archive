---
title: "Partitioning without GParted"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by egalitarian on 2007-09-20
I'm a little worried about revising my partition scheme at Step 1 below. On the other hand, this is a brand-new out-of-the-box Vostro, and I have the XPSP2 install CD, app software CD, Display CD, Drivers & Utilities CD

Here is my current setup (sorry I can't transcribe the fdisk -l)

Dell Vostro 200 64-bit Intel Dual-Core E2160
Single drive 160GB.

SDA1 = Dell Utility FAT16 (I _assume_ that this is where the Master Boot Record (MBR) is)
SDA2 = NTFS = WINXP
SDA3 = EXT3 = Ubuntu 7.04 32-bit
SDA4 = Extended (seems to overlay the linux-swap ... based on the fdisk -l)
SDA5 = linux-swap

CURRENT:
```

+------------+            +-----------------------------------------+-+
| (DE) Dell  |            | EXT3                                    |S|
| Utility    | ----A----> | GRUB menu.lst                           |W|
|            |            | 7.04 32-bit                             |P|
+------------+ +--------+ +-----------------------------------------+-+
               | WinXP  |               |
               |primary |<- chainload B-+
               |bootable|
               +--------+

```
STEP 1
```

+------------+            +===============+--------------------------+
| (DE) Dell  |            | EXT3          | NTFS                     |S
| Utility    | ---------> | GRUB menu.lst |                          |W
|            |            | 7.04 64-bit   |                          |P
+------------+ +--------+ +===============+--------------------------+
               | WinXP  |               |
               |primary |<- chainload --+
               |bootable|
               +--------+

```
STEP2
```

                                        +--C--+
                                        |     V
+------------+            +---------------+=========+----------------+
| (DE) Dell  |            | EXT3          | EXT3    | NTFS           |S
| Utility    | ---------> | GRUB menu.lst | 7.04    |                |W
|            |            | 7.04 32-bit   | 64-bit  |                |P
+------------+ +--------+ +---------------+=========+----------------+
               | WinXP  |               |
               |primary |<- chainload B-+
               |bootable|
               +--------+

```
It might be nice for me to stick a 5GB Fat32 partition so Ubuntu can exchange files with XP.
Maybe I'll add a 5GB EXT3 /home partition too.  I would love to use GParted on this project, but every time I get a different LiveCD from sourcefourge, I get the silly error:
  /bin/sh: cant access tty
Even a review of [http://ubuntuforums.org/showthread.php?t=415009](http://ubuntuforums.org/showthread.php?t=415009) does nothing to work around this.
I do have Disk Director (Partition Manager) by Acronis... so I think that (as this is a fresh Ubuntu install) I can maybe slip a partion between the current '/swap' and the 7.04 partition without disrupting the operation of menu.lst.

Without GParted, I can only guess which partition has the boot flag. The arrows above are my guess as to how boot operation passes initially from the Dell Utility partition (FAT16) to the Ubuntu partition (EXT3) and then optionally via link B to the WinXP partition.

My intention is to add partitions with Disk Director going first to Step 1 (above) and checking to see that Grub comes up OK.  Then I'll probably add a fresh install of the 64-bit 7.04 (or maybe even 7.10).  I'll probably be OK with Grub even after Step 1.  I think that Step 1 will be risky since I'm shrinking the SDA3 and maybe messing up how Grub interacts with that.  

One sticky point I've discovered in this first install of Ubuntu, is that when ubuntu asks you how big to make 'the' partition, 'the' partition that it is talking about is the existing large partition at the back of the partition (the higher numbered sectors).  Now that I know this, I suppose that in step 2, the Ubuntu installer will actually place EXT3 7.04 64-bit partition to the far right of the ASCII art above, rather than sandwiched as currently shown.

My question, Am I going to loose my Grub capability at Step 1?

Some links I've visited so far:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by srt4play on 2007-09-20
I would assume the MBR is in the very first sectors of the hard disk rather than in the first partition.  Also I wouldn't worry about creating a separate fat32 partition to exchange files and instead use the windows ext3 driver [here]("http://www.fs-driver.org").

---

### Post by dabl on 2007-09-20
> **srt4play said:**
> I would assume the MBR is in the very first sectors of the hard disk rather than in the first partition.  Also I wouldn't worry about creating a separate fat32 partition to exchange files and instead use the windows ext3 driver [here]("http://www.fs-driver.org").

YES, what srt4play said, except why not use NTFS for the shared partition, and install the ntfs-3g package in Ubuntu?  NTFS is a little more reliable/rugged filesystem than FAT32, and with the ntfs-3g package, you can read and write from Ubuntu same as from Windows.

On the partitions, I set up a Kubuntu system on an E-Machines PC that had Vista pre-installed, for a family member.  I just shrunk the big Vista partition, then made an extended partition in the rest of the space, and made 3 logical partitions in that, one each for "/", "/home", and "swap".  Very simple.  :)

---

