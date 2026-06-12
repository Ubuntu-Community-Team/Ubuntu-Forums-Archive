---
title: "Dual boot installation on a multdisc PC"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by pritcharded on 2008-07-08
I've just installed 8.04 on my old P4 (it has two hard drives and is to be used for general family use) using the dual boot guided partitioning option. It has worked fine as does XP that was already on the machine. In this case as I had already stripped off all the data (on to a new machine) I more or less left it to the installer software to establish and size partitions. Using "GParted" this is what I've ended up with:

Partition details

/dev/sda  (111.76 GiB)

/dev/sda1 (111.75 GiB)
File system: ntfs
Size: 111.75 GiB
Used: ...
Unused: ...
Flags:  boot

/dev/sdb  (149 GiB)

/dev/sdb1
File system: ntfs
Size:  48.45 GiB
Used:  ...
Unused:  ....
Flags

/dev/sdb2
File system:  extended
Size:  100.56 GiB
Used: ...
Unused: ....
Flags:

   /dev/sdb5
   File system:  ext3
   Mountpoint:   /
   Size:  97.67 GiB
   Used:  5.34 GiB
   Unused:  92.33 GiB

   /dev/sdb6
   File system:  linux swap
   Size:  2.89 GiB
   Used:  ...
    Unused:  ...

I've set up accounts for individual users and each has been given a home folder with some sub folders for saving documents, etc. But reading through some of the other documentation I'm not sure that I've ended up with quite the optimum result. In particular:

1. Elsewhere in the documentation I've read that I should have my data in a separate partition for security. In Windows it's easy to see which drive holds each file but as I'm a complete beginner with linux I'm a bit lost here (using File Browser I can see computer/file system/dev/ but no sda, sdb, etc, subfolders).

2. Elsewhere I've read that should I need to reinstall XP (a not unknown phenomena) confusion may well result within Ubuntu. As I have multiple hard drives I would have thought I should be able to avoid that problem, but how.

My main PC has three hard drives and a lot of data. I would like to also install 8.04 on it but I need to understand this a lot better before I have a go.

Any help would be appreciated.

Ted

---

### Post by crwmike on 2008-07-08
Open the terminal, type df. This will tell you the mount points of all your partitions.

Reinstalling window overwrites the boot sector and you may loose the grub

---

### Post by Barriehie on 2008-07-08
> 
2. Elsewhere I've read that should I need to reinstall XP (a not unknown phenomena) confusion may well result within Ubuntu. As I have multiple hard drives I would have thought I should be able to avoid that problem, but how.

I've had to reinstall M$ and it wasn't much of an issue with a supergrub CD and a written list of steps.  You can find out more about [ supergrub here.]("http://supergrub.forjamari.linex.org/")

Barrie

---

### Post by Barriehie on 2008-07-08
Deleted.

---

### Post by pritcharded on 2008-07-08
> **crwmike said:**
> Open the terminal, type df. This will tell you the mount points of all your partitions.

Reinstalling window overwrites the boot sector and you may loose the grub

Thanks. This is what I've got:

ted@administrator-desktop:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sdb5            101606836   4837816  91648304   6% /
varrun                  517412       108    517304   1% /var/run
varlock                 517412         0    517412   0% /var/lock
udev                    517412        56    517356   1% /dev
devshm                  517412        24    517388   1% /dev/shm
lrm                     517412     38684    478728   8% /lib/modules/2.6.24-19-generic/volatile
/dev/scd0               162156    162156         0 100% /media/cdrom0
gvfs-fuse-daemon     101606836   4837816  91648304   6% /home/ted/.gvfs
ted@administrator-desktop:~$ 


Does this mean that on /dev/sdb1 contains all the Windows material; /dev/sdb2 contains all the linux material in two partitions /dev/sdb5 and /dev/sbd6?

Thanks, Ted

PS: Sorry - the pasted terminal output looks OK when I write and edit this message but loses its formating when posted and I can't see how to overcome the problem!

---

### Post by crwmike on 2008-07-08
it shows that /dev/sdb5 is mounted to /, /dev/sdb6 is swap and is not mounted so it is not shown here.

Apparently the NTFS filesystems are not mounted. Ubuntu should automount these filesystems. Does icons for these partitions appear on the desktop when you boot the system?

Check /etc/fstab for entries of these partitions.

To manually mount a partition for example /dev/sdb1, first make sure a mountpoint dir exist.  cd to /media and see if there is a dir sdb1, if not, create one by typing.```
sudo mkdir /media/sdb1
```
Then to mount```
sudo mount -t ntfs /dev/sdb1 /media/sdb1
```

---

### Post by pritcharded on 2008-07-10
[FONT="Book Antiqua"]
crwmike

There is no reference to NTFS on the desktop when first booted. This is what is on /etc/fstab:
[/FONT]
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=9fbce897-8887-4479-ab99-ec2d499064db /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=be890164-82c4-4a7e-8185-fba38b928a2e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

[FONT="Book Antiqua"]The only reference to NTFS that I can see only comes up when I load the partition editor. It indicates that /dev/sda1 contains a NTFS file system. However looking at the file browser, /dev contains only folders named bus,disk,fd,input,net,pts,shm,snd and usb. It also contains a number of documents including "block devices" named sda, sda1, sdb and sdb1.

As I've allowed the automated installer to do the job I assume this is intentional.
Do you still think I should enter "sudo mount -t ntfs /dev/sdb1 /media/sdb1" and if so what benefit will result?

Regards Ted[/FONT]

---

### Post by crwmike on 2008-07-12
> **pritcharded said:**
> [FONT="Book Antiqua"]
Do you still think I should enter "sudo mount -t ntfs /dev/sdb1 /media/sdb1" and if so what benefit will result?
[/FONT]

The mount command will mount the partition until the next reboot(or login), entering it into the /etc/fstab will mount every time the system is booted.

To find the UUID for the partitions enter...
```
blkid
```
Use the mount command to test it, put it in the fstab after a successful mount. With the above command, you should be able to cd to /media/sdb1 and see the contents of the mounted partition.

---

### Post by crwmike on 2008-07-12
I found this post on editing fstab...
[HTML]http://ubuntuforums.org/showthread.php?t=283131[/HTML]

---

### Post by pritcharded on 2008-07-13
Thanks all for your help. It's been very helpful.
Kind regards, Ted

---

