---
title: "Have to switch HDD between IDE and RAID to boot XP and 8.04"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by macruadhi on 2008-11-27
I just installed gOS which is built on Ubuntu 8.04. After restart and attempt to boot I got the Busybox dialogue. Switched bios from IDE to RAID and it booted fine. Wife wanted to use XP, on reboot XP would try to start, get to the "XP is loading screen" then reboot itself. Had to reset bios to RAID to get successful boot.

---

### Post by lemming465 on 2008-11-28
Could we see the output from ```
sudo fdisk -l; sudo blkid; df -m
```?  It sounds like you have more than one hard drive.  Model number information on your computer, particularly your motherboard, would help too.

---

### Post by macruadhi on 2008-11-29
/dev/sda1: UUID="D24886514886346F" TYPE="ntfs" 
/dev/sda2: UUID="6c704a49-084a-4a00-a46c-3b74a71def4d" TYPE="ext2" 
/dev/sda5: UUID="135B-4027" TYPE="vfat" 
/dev/sda6: TYPE="swap" UUID="ce6e3283-d373-405c-b62f-b1a17251e381" 
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda2                18778      3377     14448  19% /
varrun                     756         1       755   1% /var/run
varlock                    756         0       756   0% /var/lock
udev                       756         1       755   1% /dev
devshm                     756         1       756   1% /dev/shm
lrm                        756        39       717   6% /lib/modules/2.6.24-22-generic/volatile
gvfs-fuse-daemon         18778      3377     14448  19% /home/eric/.gvfs
/dev/scd0           

It is a dell Inspiron 530. It does have two HDDs. Just installed a 500gb to use as extra storage. And no idea about the mobo.

---

### Post by lemming465 on 2008-11-29
> It is a dell Inspiron 530. It does have two HDDs. Just installed a 500gb to use as extra storage. And no idea about the mobo.
So the motherboard is some Dell OEM thing.  Probably some kind of intel chipset?

If I've infered the history of this system correctly, it started off with 1 disk and XP, which you repartitioned to share between XP and gOS.  Then you added a second disk, which isn't currently plugged in.  (internal SATA? external USB?).  So the XP install isn't split across an intel software "fake" RAID?  In that case, it's odd that anything wants the motherboard chipset in RAID mode to boot.

Was the second disk active when gOS was installed?  And did you make any Linux partitions there other than root (/ on sda2) and swap (sda6)?  It would be particularly relevant if there were a separate /boot. And what is currently on the master boot record (MBR), XP or Grub or Lilo, or what?

---

### Post by macruadhi on 2008-11-29
Actually I just realized that I posted the output from my Dell laptop. Here is the output for the Other one.

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6        1311    10485760    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            1312       19452   145717582+   f  W95 Ext'd (LBA)
/dev/sda5            1312       10400    73007361    7  HPFS/NTFS
/dev/sda6           10401       19079    69714036   83  Linux
/dev/sda7           19080       19452     2996091   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x597bbc9c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-091A" TYPE="vfat" 
/dev/sda2: UUID="FE1E3CBD1E3C712F" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="42588CE4588CD7D5" TYPE="ntfs" 
/dev/sda6: UUID="573b7175-a269-458c-8821-dbf1649ff73e" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="26ba238e-0df4-4dc4-8fd1-e32c9945dc9e" 
/dev/sdb1: UUID="AD9A1C435CCCBE15" LABEL="500 gig" TYPE="ntfs" 
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda6                67544      3911     60230   7% /
varrun                     501         1       501   1% /var/run
varlock                    501         0       501   0% /var/lock
udev                       501         1       501   1% /dev
devshm                     501         1       501   1% /dev/shm
lrm                        501        39       462   8% /lib/modules/2.6.24-22-generic/volatile
gvfs-fuse-daemon         67544      3911     60230   7% /home/eric/.gvfs
/dev/scd0                  699       699         0 100% /media/cdrom0

I did try to install gOS on the 2nd HDD so I could have a triple boot system but that buggered everything. The 2nd HDD is all NTFS at the moment. When I tried booting to linux the first time I got the busy box dialog and that is when I switched to RAID to boot to linux, then back to IDE when I booted to XP. After that linux booted just fine in IDE mode. It just gets curiouser and curiouser...

---

### Post by lemming465 on 2008-11-30
Given your disk setup it looks like setting the BIOS to disk RAID mode would be a mistake.  I do see intermittent boot failures that drop to busybox out of the initrd on some of my systems; I generally don't worry too much about them if the system boots successfully after being power cycled.  I'd try a soft reset followed by a hard power cycle first.  If in 3 tries you always get the boot failure into busybox, then I'd start looking for actual problems.

---

