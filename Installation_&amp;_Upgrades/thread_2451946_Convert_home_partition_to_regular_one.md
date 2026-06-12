---
title: "Convert /home partition to regular one"
date: 2020-10-13
forum: Installation &amp; Upgrades
---

### Post by adelpozoman-f on 2020-10-13
Hi, I have been using a small SSD for /() and a large HDD for /home. 
I bought a new larger SSD and want to have all my configuration and programs (.local, etc) on my ssd and then have films, etc on the HDD.

My plan is to do a regular install on the new SSD and then start moving the folders on the HDD from hdd:/user/Downloads to hdd:/Downloads, etc.
The problem is that I cant do this (because it is a /home partition?). What can I do?
Thanks!

---

### Post by rsteinmetz70112 on 2020-10-13
If Your HDD is /home then where is /user? 
Post your fstab, you should be able to temporarily mount your existing /home on the new drive then move the files in /home to a new /home on the ssd then edit fstab to use the new copy of home. Them mvode the files around on you hdd.

---

### Post by oldfred on 2020-10-13
I keep /home inside / (root) on SSD and use data partition(s) for my data. Primarily as I have several installs and want access to same data on all of them and do not want /home modified when testing another install. So I do not mount a /home from another install in a new install.

[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by ActionParsnip on 2020-10-13
Install as you expect then mount the old /home to something like /data then copy the data across (or rsync)

---

### Post by adelpozoman-f on 2020-10-13
/usr is in the small SSD.
The problem is that my actual /home folder (on the HDD) is larger than the new big SSD, so I just want to have the entire / on the big SSD and store files on HDD, because having /home on the HDD stores firefox and other programs there and slows downs the system. Then I will link the Documents, Downloads, etc to folders on the HDD. I want to do it as windows, with everything in C: (big ssd) and what I decide in D: (HDD). The problem is that I cant modify D: (the HDD) for some reason (really because it is the /home right now).
The true question is how can I create and modify folders at the root of the HDD (where right now is my user folder)

EDIT:
```
[FONT=monospace][COLOR=#18b2b2]# /etc/fstab: static file system information.[/COLOR]
[COLOR=#18b2b2]#[/COLOR]
[COLOR=#18b2b2]# Use 'blkid' to print the universally unique identifier for a[/COLOR]
[COLOR=#18b2b2]# device; this may be used with UUID= as a more robust way to name devices[/COLOR]
[COLOR=#18b2b2]# that works even if disks are added and removed. See fstab(5).[/COLOR]
[COLOR=#18b2b2]#[/COLOR]
[COLOR=#18b2b2]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/COLOR]
[COLOR=#18b2b2]# / was on /dev/sda2 during installation[/COLOR]
UUID=dab4b254-8328-4758-b13e-2307582c666f /               ext4    errors=remount-ro 0       1 
[COLOR=#18b2b2]# /home was on /dev/sdb1 during installation[/COLOR]
UUID=e5623093-acd9-4b1b-af95-24be3a35db9c /home           ext4    defaults        0       2 
[COLOR=#18b2b2]# swap was on /dev/sdb4 during installation[/COLOR]
[COLOR=#18b2b2]#UUID=633b5658-d545-4fae-8016-33816dc8cf9d none            swap    sw              0       0[/COLOR]
UUID=f6468b35-3515-41a9-9c06-5a67e8a37722 none            swap    sw              0       0
[/FONT]
```

---

### Post by oldfred on 2020-10-13
You cannot change partitions when mounted.
You have to use live installer's gparted or a gparted ISO on flash drive to edit partitions.
Do you have room on HDD to make new partition and move all your folders in /home to its own partition and mount as /data or /mnt/data?

---

### Post by adelpozoman-f on 2020-10-13
> **oldfred said:**
> You cannot change partitions when mounted.
You have to use live installer's gparted or a gparted ISO on flash drive to edit partitions.
Do you have room on HDD to make new partition and move all your folders in /home to its own partition and mount as /data or /mnt/data?

I know that it has to be unmounted, I want to do it whilst using the system installed on the new SSD. Sadly not, the /home partition at HDD is so big that my only option is to somewhat transform it to a regular partition. I have no clue how to do this.

---

### Post by garvinrick4 on 2020-10-13
Are you talking about making the /home partition and making it a new partition? Like installing gparted
and opening as like 
> sudo gparted 
and right clicking on partition and reformatting partition to use for something else? When booting into
while in sdb open gparted as superuser and right click on partition and do what you have to do. Apply on top when right.
Hope this what you meant but...  You say there is a Ubuntu install on sdb to use or as oldfred stated use Live usb and boot from it
to make changes.

---

### Post by rsteinmetz70112 on 2020-10-13
The /home partition is not 'special'mit is just like every other partition, it is simply mounted on /home not some other mount point.
post the results of :
```
$ blkid
```
and
```
$lsblk
```

---

### Post by adelpozoman-f on 2020-10-14
blkid:
```
[FONT=monospace][COLOR=#000000]/dev/nvme0n1p1: LABEL="NVMe" UUID="98d3e7af-3609-4e36-a0c0-791eb2454660" BLOCK_SIZE="[/COLOR]
4096" TYPE="ext4" PARTUUID="940be9ba-01" 
/dev/nvme0n1p2: UUID="2eae420b-23df-44cf-92ff-4883dcfc6ecc" TYPE="swap" PARTUUID="940be9ba-0
2" 
/dev/sda1: LABEL="WIN7SSD" BLOCK_SIZE="512" UUID="3C1A1BE11A1B96CC" TYPE="ntfs" PARTUUID="cd
aca2c8-01" 
/dev/sda2: BLOCK_SIZE="512" UUID="E054E65854E630C8" TYPE="ntfs" PARTUUID="cdaca2c8-02" 
/dev/sda3: LABEL="LinuxSSD" UUID="dab4b254-8328-4758-b13e-2307582c666f" BLOCK_SIZE="4096" TY
PE="ext4" PARTUUID="cdaca2c8-03" 
/dev/sdb1: LABEL="WinDATA" BLOCK_SIZE="512" UUID="F4D471F5D471BB06" TYPE="ntfs" PTTYPE="atar
i" PARTUUID="69314dd9-2490-4def-ab4c-7f215929084d" 
/dev/sdb2: LABEL="LinuxData" UUID="e5623093-acd9-4b1b-af95-24be3a35db9c" BLOCK_SIZE="4096" T
YPE="ext4" PARTUUID="4fc20fd4-30b7-4839-9d70-8fff38c888fc" 
/dev/sdb3: UUID="f6468b35-3515-41a9-9c06-5a67e8a37722" TYPE="swap" PARTUUID="8e978853-a193-4
c86-b097-bf7b24b48c30"
[/FONT]
```
nvme is the new ssd that will have the entire /.
/dev/sda3 is the old small linux partition
/dev/sdb2 is the old very big linux /home partition


lsblk:
```

[FONT=monospace][COLOR=#000000]NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT [/COLOR]
sda           8:0    0 223,6G  0 disk  
&#9500;&#9472;sda1        8:1    0 162,2G  0 part  
&#9500;&#9472;sda2        8:2    0   563M  0 part  
&#9492;&#9472;sda3        8:3    0  60,8G  0 part  
sdb           8:16   0   2,7T  0 disk  
&#9500;&#9472;sdb1        8:17   0   1,1T  0 part /run/media/adelpozoman/WinDATA 
&#9500;&#9472;sdb2        8:18   0   1,7T  0 part /run/media/adelpozoman/LinuxData 
&#9492;&#9472;sdb3        8:19   0   3,4G  0 part  
nvme0n1     259:0    0 931,5G  0 disk  
&#9500;&#9472;nvme0n1p1 259:1    0 922,7G  0 part / 
&#9492;&#9472;nvme0n1p2 259:2    0   8,8G  0 part [SWAP]
[/FONT]
```

---

### Post by adelpozoman-f on 2020-10-14
> **rsteinmetz70112 said:**
> The /home partition is not 'special'mit is just like every other partition, it is simply mounted on /home not some other mount point.
post the results of :
```
$ blkid
```
and
```
$lsblk
```

but I donthave permissions to modify it from a live usb, its locked.

---

### Post by adelpozoman-f on 2020-10-14
Ok I used an external drive and got all my data outside the SSD. Now I formatted it but creating a new ext4 system creates a lost+found folder and the drive is unwrittable. What can I dO?

---

### Post by oldfred on 2020-10-14
Did you give yourself ownership & permissions.
I usually manually mount before I have added it to my fstab & do chown & chmod & then edit fstab to permanently mount.

As posted above on splitting /home and using data partition with links to folders in data partition.
[https://ubuntuforums.org/showthread.php?t=1811198&p=11081384#post11081384](https://ubuntuforums.org/showthread.php?t=1811198&p=11081384#post11081384)

---

### Post by rsteinmetz70112 on 2020-10-15
I'm not confused. The lsblk and fstab don't seem to match. 

Is sda a SATA SDD?

Blkid indicates sdb3 is only 3.4 GB. So if nvme0n1p1 id the new larger SSD then you would have some space there for some other uses but not as much as you have on sdb. I don't see the mount points for sda1-2 or sdb3. If you want to move the existing root file system to the new root. 
I would usually use gddrescue and then gparted to increase the size of the partition or you can do a new install. But there are other ways. 

/dev/sdb2: LABEL="LinuxData" UUID="e5623093-acd9-4b1b-af95-24be3a35db9c" appears to be your /home partition, but that's not what lsblk shows. It appears to 1.7TB and substantially larger than the space available on nvme0n1p1

/dev/sda3: LABEL="LinuxSSD" UUID=UUID="dab4b254-8328-4758-b13e-2307582c666f" appears to be you old root  / partition but thats not what lsblk says       

How much space is used in the /home partition? 
Where is the /user folder?

---

