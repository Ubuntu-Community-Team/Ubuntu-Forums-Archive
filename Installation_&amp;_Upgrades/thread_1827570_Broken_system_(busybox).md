---
title: "Broken system (busybox)"
date: 2011-08-18
forum: Installation &amp; Upgrades
---

### Post by jawaka. on 2011-08-18
Hello, I've got Ubuntu 11.04 on a 40G hard disk in dual boot with a Windows XP on a 300G hard disk.

I've got back data with an USB key from a broken Windows Seven, then I've shutdown my ubuntu, but it has difficulties to stop (a mp3 player, which doesn't work well,  has already damaged my Ubuntu previously). Then my Ubuntu doesn't manage to boot : it launches "Busy Box" with "initramf".  When I boot in recovery mode it fails to boot something at 5s then it tries to launch something constantly.

I've launched a live CD in order to recover my data, but when I try to mount my hard disk I get :

```
Error mounting: mount: wrong fs type,bad option, bad superblock on /dev/sdb1, missing codepage on helper program, or other error. In some cases useful info is found in syslog - try dmsg  tail or so
```I've found this link about this problem : [http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html), but it's too complicated for me.

I just want to recover my data, a system reinstallation wouldn't bother me.

Thank you for any help ! :)

---

### Post by jawaka. on 2011-08-18
Here's what I get with "dmesg | tail" : 

```

[ 9231.120387] sd 2:0:1:0: [sdb]  Result: hostbyte=DID_OK  driverbyte=DRIVER_SENSE 
[ 9231.120391] sd 2:0:1:0: [sdb]  Sense Key :  Medium Error [current] [descriptor]
[ 9231.120396] Descriptor sense data  with sense descriptors (in hex):
[ 9231.120398]         72 03 11 04 00  00 00 0c 00 0a 80 00 00 00 00 00  
[ 9231.120406]         00 00 08 10  
[  9231.120409] sd 2:0:1:0: [sdb]  Add. Sense: Unrecovered read error -  auto reallocate failed 
[ 9231.120415] sd 2:0:1:0: [sdb] CDB: Read(10):  28 00 00 00 08 10 00 00 08 00 
[ 9231.120423] end_request: I/O error, dev  sdb, sector 2064 
[ 9231.120435] ata3: EH complete [ 9231.120449]  EXT4-fs (sdb1): can't read group descriptor 1
```

---

### Post by jawaka. on 2011-08-20
I've tried this : [http://linuxexpresso.wordpress.com/2010 … in-ubuntu/]("http://linuxexpresso.wordpress.com/2010%20%E2%80%A6%20in-ubuntu/")
But when I do  "sudo fsck.ext4 -v /dev/sdb1"  I get : 

```

e2fsck 1.41.14 (22-Dec-2010) 
fsck.ext4: Attempt to read block from filesystem resulted in short read while attempting to open  /dev/sdb1 
Maybe the size of the partition is zero.

```

So it's not a problem of superblock ?

---

### Post by jacksaff on 2011-08-20
I started getting these messages a week before my hard drive went to digital heaven. I was able to get it running occasionally at first, was able to fsck it and make a back-up, but I got increasing errors until the disk bricked a couple of days later.
If you do manage to start and mount your disk, I'd advise a backup of important files asap.

Get another hard drive (you may be able to use your second one as it's bigger than the linux drive) and try backing up:
# dd if=/dev/sdb1 of=/path/to/where/you/wantthe/backup

then try recovering the disk using the backup superblocks:

find them with 
# dumpe2fs /dev/sdb1|grep -i superblock

and then try recover with
# e2fsck -f -b 8193 /dev/sdb1

where 8193 is the first of the backups the last command returned.
Good luck.

---

### Post by jawaka. on 2011-08-20
Thank you for your help ! but it doesn't seem to work :

```



ubuntu@ubuntu:~$ sudo dd if=/dev/sdb1 of=/media/36D40FBED40F7F7D/backup
dd: reading «/dev/sdb1»: error of input/output
8192 octets (8,2 kB) copied, 36,5191 s, 0,2 kB/s


ubuntu@ubuntu:~$ sudo dumpe2fs /dev/sdb1|grep -i superblock
dumpe2fs 1.41.14 (22-Dec-2010)
dumpe2fs: Attempt to read block from filesystem resulted in short read while attempting to open /dev/sdb1


```

Is it possible that this problem comes from an extern hard disk that have been "badly" (ubuntu had difficulties to shutdown) removed ?




So, I'm trying testdisk : I've chosen Intel and Analyse. Then I get 5 partitions with 2 swaps (which I've not installed). Then I press Enter and I get this :

```

Disk /dev/sdb - 41 GB / 38 GiB - CHS 4999 255 63
     Partition               Start        End    Size in sectors
* Linux                    0   1  1  4786 254 63   76903092
L Linux Swap            4787 118  4  4997 254 63    3382278


Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
EXT3 Large file Sparse superblock, 39 GB / 36 GiB

```

What should I do ? Press Enter or press "L" for Load Backup ?

---

### Post by jacksaff on 2011-08-20
The last bit suggests your data is still intact though I don't know much about testdisk. Type man testdisk into a terminal to read the manual pages for it.

Googling some of the output lines you have given gives some things that might work:

there are people having trouble with sata data cables. Try combinations of changing the port it's plugged into, switching the cable etc.

the disk may not be getting enough power, especially if you're power supply is old. Try switching the psu power lead the disk it plugged in with and if possible have it be the only device connected on that lead.

there are a number of bits of hardware with known problems. Google for the numbers printed on the top of the drive. You may find others with the same problems. If the drive has a known fault you should at least get a new one from the manufacturer for your troubles...

---

