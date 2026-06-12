---
title: "Nearly 60gbs too small?"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by Legomaniac25 on 2008-07-30
Hey everyone,

First of all I would like to thank anyone who replies to this thread in advance.

I have used linux before (fedora core) but have always been hesitant about making the permanent switch. Now that I have made the descision it seems as though hardy heron has it out for me. (It's ok though, I love the troubleshooting process and people like you make it fun)

Simply put when installing ubuntu the automatic partitioner will give me the choice that I want, 60% windows and 40% ubuntu on a 150 gb drive.

If I keep on following the graphical install as it goes, it simply shows me a dialog box that says nothing but "Size too small" and then boots into the live cd...

If you need anymore info about what's going on you guys should let me know and I will respond promptly.

Thanks for your help in advance!

---

### Post by cdtech on 2008-07-30
While in the Live CD, the output of "df -H" could be useful.

Thanks......

---

### Post by Potatoj316 on 2008-07-30
do you already have windows installed?  If you do try defragmenting the HD before trying to partition.

---

### Post by Legomaniac25 on 2008-07-30
Here is the output of df -H
> 
Filesystem             Size   Used  Avail Use% Mounted on
tmpfs                  531M    17M   514M   4% /lib/modules/2.6.24-19-generic/volatile
tmpfs                  531M    17M   514M   4% /lib/modules/2.6.24-19-generic/volatile
varrun                 531M   107k   530M   1% /var/run
varlock                531M      0   531M   0% /var/lock
udev                   531M    37k   531M   1% /dev
devshm                 531M    13k   531M   1% /dev/shm
tmpfs                  531M    17k   531M   1% /tmp
gvfs-fuse-daemon       531M    85M   446M  16% /home/ubuntu/.gvfs


I will go ahead and defrag in xp. Thanks for the tip.

---

### Post by ajgreeny on 2008-07-30
You must have carried out the df -H in the live CD with no hard disks mounted as there is no disk partition showing and the output is not very helpful.   Mount all your hard drives and then repeat the command and it may help a bit more.

---

### Post by jimv on 2008-07-30
sudo fdisk -l would be good too.

---

### Post by Legomaniac25 on 2008-07-30
Thanks for your help guys.

When my defrag is done I will boot back into the live cd, mount the  drive and give you the outputs of both of the commands.

I should have defragged long long ago, but I have never been one to fully appreciate preventative maintenance until I have something that needs to be maintenanced.

Thanks again, brb.

---

### Post by benisma on 2008-07-30
I don't know if I should jump in here, but I am having the same problem. I ran the two commands above, and this is what I show:

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                1009M   17M  993M   2% /lib/modules/2.6.24-19-generic/volatile
tmpfs                1009M   17M  993M   2% /lib/modules/2.6.24-19-generic/volatile
varrun               1009M  100K 1009M   1% /var/run
varlock              1009M  4.0K 1009M   1% /var/lock
udev                 1009M   44K 1009M   1% /dev
devshm               1009M   12K 1009M   1% /dev/shm
tmpfs                1009M   16K 1009M   1% /tmp
gvfs-fuse-daemon     1009M   36M  973M   4% /home/ubuntu/.gvfs
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7       38481   309050437+   7  HPFS/NTFS
/dev/sda3           38483       38913     3462007+  db  CP/M / CTOS / ...


I am having a hard time understanding what my issue is. Thanks from me too! I apologize if I didn't do something right, what is the word for uber noob?

---

### Post by cdtech on 2008-07-30
So you'll want to split the sda2 partition to allow Ubuntu? I would get into window's and create a separate partition to install to. You have dell backup's and utils in their own partitions so using the whole disk is out of the question, unless you wipe it clean.

If you set up a partition within window's you can use the sudo fdisk -l to see the partition it created afterwards and install Ubuntu using that partition.

I guess I explained it correctly...:)

---

### Post by Legomaniac25 on 2008-07-31
Well, the disk succesfully completed the defrag and when I went to install again there was no luck. 

So here are the values of the suggested commands...

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x958c958c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19453   156256191    7  HPFS/NTFS

```

and...

```
ubuntu@ubuntu:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
tmpfs                  531M    17M   514M   4% /lib/modules/2.6.24-19-generic/volatile
tmpfs                  531M    17M   514M   4% /lib/modules/2.6.24-19-generic/volatile
varrun                 531M   107k   530M   1% /var/run
varlock                531M      0   531M   0% /var/lock
udev                   531M    50k   530M   1% /dev
devshm                 531M    13k   531M   1% /dev/shm
tmpfs                  531M    17k   531M   1% /tmp
gvfs-fuse-daemon       531M    94M   437M  18% /home/ubuntu/.gvfs
/dev/sda1              161G    97G    64G  61% /media/disk

```

Thanks again for helping out guys.

---

### Post by Legomaniac25 on 2008-07-31
Sorry to bump this, I know people get touchy about bumping sometimes, but I have some new info.

Following the advice of the person two posts above I thought I could just try to make a new partition that I then could install ubuntu on, but since I was already in the live CD I decided to try and use GParted since it was, well, you know right there. Not to mention the fact that I have used it before successfully.

However when it got past the running simulation stage it failed, and didn't actually commit any changes to the drive.

I don't know if this info helps, I think GParted makes a log file when it fails so I can try to run it again and grab that log file if you guys need it.

Thanks again.

---

