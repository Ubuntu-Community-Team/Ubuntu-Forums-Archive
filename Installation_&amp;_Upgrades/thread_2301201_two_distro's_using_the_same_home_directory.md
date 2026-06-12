---
title: "two distro's using the same home directory?"
date: 2015-10-31
forum: Installation &amp; Upgrades
---

### Post by General_Faliure on 2015-10-31
Hello.
I was wondering if this is possible?
I acquired two small, and cheap (30 Gb) ssd's.
One i have installed with Xubuntu with the /home directory mounted on a 250 Gb hard drive, which works well.
The other i want to add to a system which already runs linux mint on a hard disk.
Is it possible to install a different distro on the ssd and just mount the /home directory to the /home directory on the hard drive?
Both are older test systems which i use to try out distro's and things like this.

---

### Post by ajgreeny on 2015-10-31
Depending on the two distros this could be a route to big problems resulting from slightly different configuration files and folders in the two OSs.

It will be much better to keep /home in the main root partition of each OS and use the HDD only as a data partition.  It is very easy to make symbolic links from each data folder on the HDD to a similarly named folder in the home of each OS.  Your data files will then appear to be sitting in the home of each but will actually be on the large HDD.  You will need to edit /etc/fstab in each OS and add a line to mount the HDD at boot which we can help you with if you are not sure how to do so.

---

### Post by oldfred on 2015-10-31
Some more details on sharing a data partition:
 The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by yancek on 2015-10-31
The problems with this are discussed above.  If you don't consider yourself a Linux expert or are not familiar with the various configuration files here, best not to do it.  Much easier to use a separate data partition.

---

### Post by General_Faliure on 2015-11-02
I have made symlinks of of :/media/tux/77333325-7ff0-4791-aefd-145015bb4da6/home/tux/Downloads/ and ~ Documents, ~Video's and~Music to /home tux (on the ssd, i removed the original one's).
I used midnight commander for that.
How should the fstab line look like to mount the hdd at boot?

---

### Post by ajgreeny on 2015-11-02
> **General_Faliure said:**
> I have made symlinks of of :/media/tux/77333325-7ff0-4791-aefd-145015bb4da6/home/tux/Downloads/ and ~ Documents, ~Video's and~Music to /home tux (on the ssd, i removed the original one's).
I used midnight commander for that.
How should the fstab line look like to mount the hdd at boot?
That fstab line depends on the filesystem you have on the partition that is on your HDD and how many partitions are on it.  Show us the output of ```
sudo parted -l
```

---

### Post by General_Faliure on 2015-11-02
It's one ext4 partition and 4 Gb swap:
```
Model: ATA SAMSUNG HD502HI (scsi)
Schijf /dev/sda: 500GB
Sectorgrootte (logisch/fysiek): 512B/512B
Partitietabel: msdos
Schijfvlaggen: 

Nummer  Begin   Einde  Grootte  Type      Bestandssysteem  Vlaggen
 1      1049kB  496GB  496GB    primary   ext4             opstart
 2      496GB   500GB  4293MB   extended
 5      496GB   500GB  4293MB   logical   linux-swap(v1)


Model: ATA FASTDISK 32G (scsi)
Schijf /dev/sdb: 32,0GB
Sectorgrootte (logisch/fysiek): 512B/512B
Partitietabel: msdos
Schijfvlaggen: 

Nummer  Begin   Einde   Grootte  Type      Bestandssysteem  Vlaggen
 1      1049kB  27,7GB  27,7GB   primary   ext4
 2      27,7GB  32,0GB  4292MB   extended
 5      27,7GB  32,0GB  4292MB   logical   linux-swap(v1)

```

Here's my fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=2285a8a5-26cb-4874-8a7a-073c5eb2856b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=62b3761d-0c4e-4813-9ddd-32006ba02932 none            swap    sw              0       0
UUID=77333325-7ff0-4791-aefd-145015bb4da6 /media/tux    ext4    defaults        0    0
```

I added the last line, now it seems to work, i'll let you know if i run into trouble, it's a test system, so it's no big deal if it breaks:P

---

### Post by ajgreeny on 2015-11-02
That last line is fine.
You could to change the final 0 to 1, but otherwise no problem that I can see.

---

