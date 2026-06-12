---
title: "Disk drive unallocated"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by ocky7 on 2011-04-29
Dear all,

I'm currently on a USB installation of Ubuntu 11.04. When I try to set the booting partition in GParted 0.7.0, I get the following screen:
[IMG]http://i54.tinypic.com/2n9973r.png[/IMG]

When I do fdisk -l in the terminal I get the following:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x07c1a11d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       33561   269475308+   7  HPFS/NTFS
/dev/sda3   *       33561       38783    41948255+   7  HPFS/NTFS
/dev/sda4           38783       38914     1050624   12  Compaq diagnostics

Disk /dev/sdb: 4004 MB, 4004511744 bytes
255 heads, 63 sectors/track, 486 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0639fc73

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         487     3910640    b  W95 FAT32

```The number of cilinders seems to be one off. But I have no idea what it means.

My situation is the following:

I had a dual boot of Win7 on one partition (C:\, named 'Boot' ) and Ubuntu on the other (D:\, named Recover). There were two other invisible partitions, one name WinPE and another unnamed one, which are 1 GB en 100 MB respectively.  
 

 My Linux partition was nt accessible for some reason so I tried to make it visible. I suppose I made the invisible partition visible as well because I can browse them okay in my current boot from my flash drive. But when I try to boot without the flash drive I get the message 'BootMGR is missing – Press CTRL+ALT+DEL to restart' ad infinitum and the Windows recovery disk doesn't seem to find my Windows installation.  
 

 Also, when I try to install Ubuntu on my hard disk, I get an error, first '??? ???' and later ' ubi-partman failed with exit code 10. Further information mayu be found in /var/log/syslog.', which I think is this:


 ```

Apr 29 08:32:12 ubuntu ubiquity[7299]: switched to page prepare 
 Apr 29 08:32:20 ubuntu ubiquity[7299]: debconffilter_done: ubi-prepare (current: ubi-prepare) 
 Apr 29 08:32:20 ubuntu ubiquity[7299]: Step_before = stepPrepare 
 Apr 29 08:32:20 ubuntu kernel: [ 1072.409964] EXT2-fs (loop1): error: ext2_readdir: bad page in #57833 
 Apr 29 08:32:20 ubuntu kernel: [ 1072.410016] EXT2-fs (loop1): error: ext2_readdir: bad page in #57833 
 Apr 29 08:32:20 ubuntu kernel: [ 1072.410235] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 57857 
 Apr 29 08:32:20 ubuntu kernel: [ 1072.410280] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 57857 
 Apr 29 08:32:20 ubuntu kernel: [ 1072.410324] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 57858 
 Apr 29 08:32:20 ubuntu kernel: [ 1072.410364] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 57858 
 Apr 29 08:32:20 ubuntu kernel: [ 1072.410408] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 57859 
 Apr 29 08:32:20 ubuntu kernel: [ 1072.410447] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 57859 
 Apr 29 08:32:20 ubuntu kernel: [ 1072.410514] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 57860 
 Apr 29 08:32:20 ubuntu kernel: [ 1072.410553] EXT2-fs (loop1): error: ext2_lookup: deleted inode referenced: 57860 
 Apr 29 08:32:20 ubuntu activate-dmraid: No Serial ATA RAID disks detected 
 Apr 29 08:32:20 ubuntu kernel: [ 1072.752786] JFS: nTxBlock = 8192, nTxLock = 65536 
 Apr 29 08:32:20 ubuntu kernel: [ 1072.870693] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled 
 Apr 29 08:32:20 ubuntu kernel: [ 1072.871432] SGI XFS Quota Management subsystem 
 Apr 29 08:32:20 ubuntu ubiquity: Cannot unlink output FIFO: Is a directory 
 Apr 29 08:32:22 ubuntu ubiquity[7299]: Traceback (most recent call last): 
 Apr 29 08:32:22 ubuntu ubiquity[7299]:   File "/usr/lib/ubiquity/ubiquity/misc.py", line 195, in boot_device 
 Apr 29 08:32:22 ubuntu ubiquity[7299]:     for part in p.partitions(): 
 Apr 29 08:32:22 ubuntu ubiquity[7299]:   File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 205, in partitions 
 Apr 29 08:32:22 ubuntu ubiquity[7299]:     self.open_dialog('PARTITIONS') 
 Apr 29 08:32:22 ubuntu ubiquity[7299]:   File "/usr/lib/ubiquity/ubiquity/parted_server.py", line 133, in open_dialog 
 Apr 29 08:32:22 ubuntu ubiquity[7299]:     self.outf = open(outfifo, 'r') 
 Apr 29 08:32:22 ubuntu ubiquity[7299]: IOError: [Errno 21] Is a directory: '/var/lib/partman/outfifo' 
 Apr 29 08:32:22 ubuntu ubiquity[7299]:  
 Apr 29 08:32:22 ubuntu ubiquity[7299]: debconffilter_done: ubi-partman (current: ubi-partman) 
 Apr 29 08:32:22 ubuntu ubiquity[7299]: dbfilter_handle_status: ('ubi-partman', 10)

``` Does anyone know what I should do? :(

---

### Post by dino99 on 2011-04-29
as i see gparted is confused by the weird compaq tatoo

so try with something else than gparted, like partedmagic
[http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)

or to remove the hidden Compaq bytes: use for example western digital tool

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

it seems that a dmraid call is done too:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

scroll down to the latest lines of the page

---

### Post by srs5694 on 2011-04-29
I don't know what dino99 means by "the weird compaq tatoo." I do know that libparted-based tools, including GParted, tend to flake out whenever they see a partition table that's even slightly odd. You can get more information from fdisk, but by default it uses cylinder values, which are way too imprecise for this sort of detective work. Since you're also reporting boot problems, I recommend you run the [Boot Info Script,](http://sourceforge.net/projects/bootinfoscript/) which will report both partitioning data (precise to the sector, which is what's required) and information on boot loader installations and settings. When you run the program, it will create a file called RESULTS.TXT. Post that file here.

---

