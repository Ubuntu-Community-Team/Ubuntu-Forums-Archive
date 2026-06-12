---
title: "Upgrading but not enough space on /boot!!!"
date: 2010-05-21
forum: Installation &amp; Upgrades
---

### Post by freesparks on 2010-05-21
Hello all,

     I am trying to upgrade to Ubuntu 10.04 and stumbled on a little problem.  My partition scheme is as follows and I am installing Ubuntu on an External USB harddrive:

499 GB HARD DISK
WD My Passport 070B
MBR Partition table

49 MB Filesystem              --/boot
Linux Ext4 (version1.0)

244 GB Extended 
Contains logical partitions

    20 GB Filesystem          --/opt
    Linux Ext4(version1.0)
    
    4.0 GB Swap Space
    4.0 GB

    60 GB Filesystem        --/root
        Linux Ext4 (version1.0)

    60 GB Filesystem        --/home
        Linux Ext4 (version1.0)

    60 GB Filesystem        --/usr
        Linux Ext4 (version1.0)

    30 GB Filesystem        --/var
        Linux Ext4 (version1.0)

    10 GB Filesystem        --/tmp
        Linux Ext4 (version1.0)

255 GB Unrecognized        --this is what I eventually want to use as free space to back up Unknown or Unused          file


As noted above my ./boot space is only 49MB, and the error I  got read this:
> 
Not enough free disk space.

The upgrade is now aborted.  The upgrade needs a total of 19.9MB free space on disk '/boot'.  Please free at least an additional 10.3MB of disk space on '/boot'.  Empty your trash and remove temporary packages of former installations using:```

sudo apt-get clean
```I ran: sudo apt-get clean in the Terminal.  And, still have the same amount of disk space being utilized.  Am I missing something?

Any help on this would be greatly appreciated.

Best Regards,

freesparks


OHH, these are my system specs:

Ubuntu
Release 9.10(karmic)
Kernel Linux 2.6.31-20-generic-pae
GNOME 2.28.1

Hardware:
    Memory: 2.9GB
Processor:0 Intel (R) Pentium (R) Dual CPU t2390@1.86GHz
Processor:1 Intel (R) Pentium (R) Dual CPU t2390@1.86GHz

---

### Post by kansasnoob on 2010-05-21
Please just post the output of:

```
df -H
```

and:

```
sudo du -sh /*
```

---

### Post by oldfred on 2010-05-21
Clean just removes files for installs that it does not need anymore. It does not houseclean kernels.

You should be able to go into synaptic and remove some of the older kernels.
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

Was there some reason why you have so many partitions? Ubuntu's standard install is just root & swap. We typically recommend adding /home. Generally only servers dedicated to a specific application that heavily uses different directories have separate partitions.

My root with lots of programs (and all the system folders)  is only about 5-6GB since I have all my data in a separate /data partition. My /home with the user settings and some misc data is about 1GB. I kept the extra space for potential other install's root partitions.

---

### Post by freesparks on 2010-05-22
Hello kansasnoob,

   Thank you so much for the reply!!  
My output to
: ```
df -H
``` is as follows:

Filesystem             Size   Used  Avail Use% Mounted on
/dev/sdb5                 60G   427M    56G   1% /
udev         1.6G   324k   1.6G   1% /dev
none                           1.6G   213k   1.6G   1% /dev/shm
none                          1.6G   320k   1.6G   1% /var/run
none                          1.6G      0   1.6G   0% /var/lock
none                          1.6G      0   1.6G   0% /lib/init/rw
/dev/sdb1                48M    36M   9.7M  79% /boot
/dev/sdb10              20G   181M    19G   1% /opt
/dev/sdb6                60G   555M    56G   1% /home
/dev/sdb7                60G   3.9G    53G   7% /usr
/dev/sdb8                30G   546M    28G   2% /var
/dev/sdb9               9.9G   182M   9.2G   2% /tmp
/dev/sr1                  675M   675M      0 100% /media/cdrom1

And , my output to```
 sudo du -sh /*
``` is as follows:

5.3M    /bin
30M    /boot
0    /cdrom
524K    /dev
12M    /etc
du: cannot access `/home/myhomedirectory/.gvfs': Permission denied
346M    /home
0    /initrd.img
0    /initrd.img.old
204M    /lib
16K    /lost+found
422M    /media
4.0K    /mnt
20K    /opt
du: cannot access `/proc/5606/task/5606/fd/4': No such file or directory
du: cannot access `/proc/5606/task/5606/fdinfo/4': No such file or directory
du: cannot access `/proc/5606/fd/4': No such file or directory
du: cannot access `/proc/5606/fdinfo/4': No such file or directory
0    /proc
452K    /root
6.6M    /sbin
4.0K    /selinux
200K    /srv
0    /sys
24M    /tmp
3.5G    /usr
327M    /var
0    /vmlinuz
0    /vmlinuz.old

Best Regards,

freesparks

---

### Post by freesparks on 2010-05-22
Hello oldfred,

    I really don't have any specific reason why other than the fact that this is the way the person who attempted to teach me how to do it showed me.  He maintains servers for a living, so go figure.  You were correct in your intuition. This brings me to a specific question that I've had for quite sometime.  Is it necessarry to make these disks, eg. /root, /boot, /tmp, /var, /usr, /root, /opt..  I also read somewhere in the post that your swap size should 2x the size of your ram..  Is this true?  So for example if my Memory is 4Gb, than should the size of my Swap be 8GB?  Any help on this would be greatly appreciated.

Best regards,

freesparks

---

### Post by oldfred on 2010-05-22
Then it makes sense. 10 years ago I installed redhat and it was server type install and wanted all those extra partitions. I had more trouble figuring out what size each should be. My first (and for 3 years) install of Ubuntu only had root & swap with a shared NTFS as I converted from XP. (still not 100% weaned from windows). I have now added /home and a /data partition as I have a larger hard drive. I also left room for additional roots (about 20-25GB each), as I have 3 Ubuntu roots, last install, current install & beta just to test. 

When memory was only 256MB they recommended 2x RAM for swap. When memory got to about 2GB they started recommending making it the same size as RAM. Some with lots of RAM say swap is never used and run without swap, but I think it is still a good idea to have some. Hard drives are so large allocating 2 or 4GB for swap is no big deal. If you want to hibernate it should be slightly larger than RAM as that is where memory is stored when you hibernate.

---

### Post by freesparks on 2010-05-22
Hello oldfred,

    Well, based on what you are saying then, I guess my only option is to partition my 255GB of unused and unallocated space to 30GB so that I can install version 10.04..  My only problem is I am not as savy as yet to do this.  And, it seems as though I would need a live CD of 10.04 in order to successfully do this.  There doesn't seem to be a way during the upgrade process to redirect the upgrade to its own new /boot rather than residing on the same old one, which is in my case limited for space.

Best Regards,

freesparks

---

### Post by freesparks on 2010-05-22
On my MAC,

   This is my partition scheme, which is installed on the internal harddrive:

Filesystem        Size        Used        Avail        Use%        Mounted on
/dev/sd4           29G         7.3G        20G             27%             /
none                2.1G        332k        2.1G            1%              /dev
none                2.1G        664k        2.1G            1%              /dev/shm
none                2.1G        115k        2.1G            1%              /var/run
none                2.1G        0             2.1G            0%              /var/lock
none                2.1G        0             2.1G            0%              /lib/init/rw


  This was achieved without me temparing with the file structure and creating disks upon installation.  For the sake of understanding this,  I don't see a /boot, I only see / , which from my understanding is root.  Can you expound on this, I really appreciate your last post because it gives me great insight on the history of all this and where it all came from.

Best Regards,

freesparks

---

### Post by oldfred on 2010-05-22
There only are a few cases where a /boot partition is required. Old computers with BIOS limits may require the boot at the beginning of a disk, servers, possibly RAID or other special setups. Normally /boot is inside the root partition as a folder as are all the other system folders. Then we like to keep data - /home and or /data in separate partitions so you can reinstall with less risk to data and most user settings. That is also what many recommend for windows, moving My Docs to a separate partitions to separate the operating system from data.  

Explaination of file structure
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

I have partitioned prior to install for many years, so I always partition the way I want and then use manual install and choose the partitions I want to use. Of course with my new drive I create a bunch of partitions and then forgot which was which and installed my production to the beta (labeled) and beta to production. I just had to change labels but it points out you still have to keep track of labels vs. partition numbers.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
With add'l info on manually partitioning
[http://guvnr.com/pc/ubuntu-partition-planning/](http://guvnr.com/pc/ubuntu-partition-planning/)
This difference between instructions to install karmic and lucid is mostly color scheme.
[http://guvnr.com/pc/karmic-install-tutorial/](http://guvnr.com/pc/karmic-install-tutorial/)

---

### Post by freesparks on 2010-05-22
Hello oldfred,

  I launched gparted from a livecd as the tutorial suggested and I feel pretty comfortable in it and have a pretty good grasp on the instructions but I don't see a place where I can increase the size of my boot drive.  Basically, inside gparted I have the following after I selected /dev/sdb, which is my external harddrive:  

> 
PARTITION         Filesystem                  Size                     Used                             Unused         Flags

/dev/sdb1              ext3                            47.03MiB             35.7MiB                          11.34MiB      boot
/dev/sdb2              extended                    227.25GiB
       /dev/sdb5       ext3                            55.88GiB              1.27GiB                         54.61GiB
       /dev/sdb6       ext3                            55.88GiB              1.36GiB                         54.52GiB
       /dev/sdb7       ext3                            55.88GiB              4.49GiB                         51.39GiB
       /dev/sdb8       ext3                            27.94GiB             948.01MiB                     27.01GiB
       /dev/sdb9       ext3                            9.32GiB               322.70MiB                     9.00GiB
       /dev/sdb10     ext3                            18.63GiB             471.48MiB                      18.17GiB
       /dev/sdb11     linux-swap                  3.72GiB              -------                                ---------      
 unallocated           unallocated                 237.80GiB 

All I want to do is increase the size of /dev/sdb1.  Is this even possible? Currently as shown above /dev/sdb1 is only 47.03MiB, I want to increase it to 4GB.  Can you explain me how to go about doing this?  Can I go about it by first partitioning the unallocated 237.80GiB of space at the very end to 4Gib then copying and pasting /dev/sdb1 to that space?  Any help on this would be greatly appreciated.

Best Regards,

freesparks

---

### Post by oldfred on 2010-05-22
You cannot increase where it is as it is trapped. If you could decrease sda2 and then move it over you could add a little space. I do not like moving partitions as all the data has to be moved and that is higher risk. Yes you could copy sda1 to the unallocated space. Any thing that depends on the location of /boot will have to be updated, like reinstalling grub.

Be careful not to trap the extended partition as you can have only 3 primary in addition to the extended. If you put a primary after the extended then you will not be able to expand the extended and add new partitions.

---

