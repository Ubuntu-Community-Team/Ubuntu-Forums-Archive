---
title: "[SOLVED] Multi problems after clean install of 7.10"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by MacDuff on 2007-10-20
Acer Aspire 1680 laptop ran Ubuntu 7.04 perfectly 
I did a clean install of 7.10 from Alternate CD.  Before doing the install I formatted the previous Ubuntu partitions and made them one empty space.  On the install I told the installer to use the largest space and format it automatically.  The install appeared to complete without problems and the boot (which had been trashed by removing the previous Linux partitions) was resurrected perfectly.

1st problem:
On Start-up, after log on, Message appers:  "Low Disk Space - 100% of disk is on/in use"

2nd problem:
Cannot start Open Office Writer:  Error "Open Office.org 2.3 The application cannot be started. An internal error occurred".

3rd problem:
Cannot start Evolution:  No error messages but will not start.

4th problem:
Will not shut down.  Icons disappear from screen but background remains and system stalls.

Thinking that all these may be caused by a lack of HD space I looked at the drives using both a Linux partition manager and a Windows partition manager out of curiosity.

Partitions according to G Parted:  (line numbers added for reference)
                                           Size          Used         Free
1. /dev/sda1 Fat32          19.53GB  13.68GB     5.85GB
2. /dev/sda2 extended    34.32GB 
3. /dev/sda5 ntfs             19.8 GB  263.02MB   14.10GB
4. /dev/sda7 linux swap 164.7MB
5.  dev/sda3  ext3              2.04GB   1.99GB   48.97MB

Partitions according to Acronis Disk Director (with Windows)
                                  Capacity    Free 
1. Acer c  Pri, Act    19.53GB    5,856GB   FAT32, (LBA)
2. Data Files (E)       19.8 GB      8.614GB   ntfs
3. Ext3		            14.36GB   14.1 GB	   Ext3
4. Linux Swap        164.7 MB                      Linux Swap
5. Ext3   Pri                 2.038GB  47.81MB   Ext3

I don't understand where G-Parted comes up with the second line 
 "/dev/sda2 extended    34.32GB"   It appears to be the total of the Acronis display lines 2 & 3.

I surmise that this as an indication that Ubuntu thinks it has the right to use the ntsf partition as an extended partition and lump it in with its own Ext3 partition. 

It does not look right but it might work. Does anyone know if this will cause a problem?

It appears that there are still multiple large bugs in Gutsy. Any suggestions to make things work before I blow out Ubuntu 7.10 and re-install 7.04?

---

### Post by Pumalite on 2007-10-20
Read this: [http://ubuntuforums.org/showthread.php?t=583007](http://ubuntuforums.org/showthread.php?t=583007)
(I installed RC a while ago and through updates I have Final Release today. I've had no problems)

---

### Post by MacDuff on 2007-10-20
Yes Puma.  You don't mind if I call you Puma for short do you?..... He grinned.

I did all that EXCEPT waiting for a month before doing an install.  Also I did not but the IS0 at 4x rather I used half of the maximum (on a new drive) but I am not convinced that extremely slow burning is any benefit.  I assume that if the disk passes all the integrity checks it is OK to go.

I did wonder about the quality of the CD but, the checksum and integrity checks all said the CD was good.

Do you have any comment on the funny way the partitions are being reported? 

Mac  (Short for MacDuff :))

---

### Post by Pumalite on 2007-10-20
Hey, Mac, can you post:
sudo fdisk -lu

---

### Post by MacDuff on 2007-10-20
Here it is:
mac@Aspire1680Ubu:~$ sudo fdisk -lu
[sudo] password for mac:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x07980797

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40965749    20482843+   c  W95 FAT32 (LBA)
/dev/sda2        40965750   111732074    35383162+   5  Extended
/dev/sda3       111732078   117210239     2739081   83  Linux
/dev/sda5        40965816    82493774    20763979+   7  HPFS/NTFS
/dev/sda6        82493838   111234059    14370111   83  Linux
/dev/sda7       111234123   111732074      248976   82  Linux swap / Solaris
mac@Aspire1680Ubu:~$ 

While I was waiting for your reply, I increased the size of /dev/sda3 by about 25% 
I also increased the swap file by about the same amount. 
Both Open Office and Evolution now open and the "disk full" message no longer appears on startup.

So the problem appears to be that the install did not size the partitions adequately. 
What would you recommend I make all the Linux partition sizes?

Thanks

---

### Post by Pumalite on 2007-10-20
Usually one needs:
10 GB for '/'
2x RAM up to 1 GB for /swap
The rest for home.

---

### Post by MacDuff on 2007-10-20
Roger that Pumalite

I did read that somewhere but could not recall where.  So much to learn but as each little bit sticks,  my internal knowledge base increases.  Your help is much appreciated.

Mac

---

