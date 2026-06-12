---
title: "Parition"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by roshanbernard on 2011-05-09
Hi ,

i have already installed ubuntu 11.04 in my 2TB hard drive....and i forgot to partition it before the installation..

is there anyway i can create partition now.

gparted wont let me do it....as there is only one drive which has the OS installed.

reagrds

rosh

---

### Post by WthIteh on 2011-05-09
> **roshanbernard said:**
> Hi ,

i have already installed ubuntu 11.04 in my 2TB hard drive....and i forgot to partition it before the installation..

is there anyway i can create partition now.

gparted wont let me do it....as there is only one drive which has the OS installed.

reagrds

rosh
Yes. The gparted does not let you to change partitioning since that partition is mounted. If you boot from a live CD (so the partition could be unmounted), then gparted allows to divide your partition.

---

### Post by Rubi1200 on 2011-05-09
> **roshanbernard said:**
> Hi ,

i have already installed ubuntu 11.04 in my 2TB hard drive....and i forgot to partition it before the installation..

is there anyway i can create partition now.

gparted wont let me do it....as there is only one drive which has the OS installed.

reagrds

rosh
Hi and welcome to the forums :-)

Just to be clear on something, is this a regular install or using Wubi inside Windows?

Please post the output of the following commands from within the Ubuntu install:

```
sudo parted -l

df -H
```

---

### Post by roshanbernard on 2011-05-15
hi rubi,
i got this following error msg.

[B]roshan@roshan:~$ sudo parted -l
Model: ATA WDC WD20EARS-00M (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      17.4kB  1018kB  1000kB                        bios_grub
 2      1018kB  401MB   400MB   ext2
 3      401MB   2401MB  2000MB  linux-swap(v1)
 4      2401MB  22.4GB  20.0GB  ext4
 5      22.4GB  2000GB  1978GB  ext4


roshan@roshan:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda4               20G   6.0G    13G  32% /
none                   6.3G   734k   6.3G   1% /dev
none                   6.4G   635k   6.4G   1% /dev/shm
none                   6.4G   218k   6.4G   1% /var/run
none                   6.4G      0   6.4G   0% /var/lock
/dev/sda2              375M    24M   332M   7% /boot
/dev/sda5              2.0T   109G   1.8T   6% /home
[/B]

i got this msg....

can i make a seperate drive...because i dont wanna store everything in home folder..

regards

roshan

---

### Post by roshanbernard on 2011-05-15
and i installed through the USB..complete install....not wubi install..

---

### Post by srs5694 on 2011-05-16
First, when posting output from text-mode utilities, please enclose the copied-and-pasted text in [noparse]```
[/noparse] and [noparse]
```[/noparse] tags. This improves legibility by keeping columns properly aligned.

Second, the term "drive" is generally applied to physical disks or removable-disk readers (like optical disc drives). It's common in the Windows world to use this term to refer to partitions, but that usage is uncommon in Linux. I'm not trying to scold you here; I'm just trying to inform you of the common usage in Linux so as to avoid miscommunication now or in the future.

Third, your output contained no error messages. The output you  identified as error messages is the normal output of those utilities,  which is what Rubi1200 was asking to see.

Fourth and finally, your partitioning looks fine to me. The /home directory is intended to hold your user data. Creating a separate partition for ordinary user data is, in all probability, re-inventing the wheel. There are exceptions to this rule, but you haven't provided any reasoning behind your desire to create additional partitions, so without further information, I'd have to advise against doing it. If you have a specific reason for wanting to create more partitions, please elaborate about those reasons.

---

### Post by roshanbernard on 2011-05-17
I am done with ubuntu 11.04.....i was workign with 10.10 for 2 months..and everythign worked fine for me...

I am not using linux for fun.I am doing study on genemoic assembly and its very important to me.But 11.04 wasted my time and its a big disappointment for me.None of my software worked with 11.04.....

i am switching back to ubuntu 10.10...
\

---

