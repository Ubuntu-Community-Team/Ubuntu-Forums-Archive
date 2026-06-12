---
title: "how to install programs using memory in disks that need to be mounted."
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by pragya on 2010-10-22
Hi, I am new to ubuntu. I want to install a software that takes 1.5GB and is windows compatible.
Unfortunately, I have only 1.1 gb free memory left in my ubuntu workspace. But, I have 31GB free space in a hard disk that I mount to ubuntu everytime I start my laptop.

Now, when I install my software, I give the correct pathname where I want to install my software. But,somehow the window always shows that free space available is only 1.1GB and so, it cannot install the software.

Can anyone tell me what I should do to install my program in another hard disk??

Thanks, 
pral

---

### Post by oldfred on 2010-10-22
Have you housecleaned? Ubuntu (or any system) works best if there is some free space.  Mount all partitions that you use and run this (only shows mounted partitions):

sudo df -h

HOWTO: Recover Lost Disk Space 
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
 How To: Disk Full? - Check Your Trash 
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by pragya on 2010-10-22
I got this as output, everything seems correct, but it just would not work.

```

hp@ubuntu:~$ sudo df -h
[sudo] password for hp: 
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0            5.6G  4.3G  989M  82% /
udev                  497M  284K  497M   1% /dev
none                  497M  2.9M  494M   1% /dev/shm
none                  497M   96K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sda1              20G   17G  2.6G  87% /host
/dev/sda6              26G   14G   13G  52% /media/62B8253FB82512D9
/dev/sda5              30G   85M   30G   1% /media/44509C3D509C379E
hp@ubuntu:~$

```

---

### Post by oldfred on 2010-10-22
Is this a wubi install? I do not know much about wubi installs but they are more difficult to resize.

---

### Post by pragya on 2010-10-23
well yes, its a wubi install and I have no idea how to make space for my software.

---

### Post by oldfred on 2010-10-23
Wubi is for windows users to give Ubuntu an extended trial as it runs on the NTFS windows partition and can be removed easily.

But once you find you like Ubuntu you should consider a full install with Ubuntu on separate partitions. Even the designer of wubi expects users to do that.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

HOWTO: migrate wubi install to partition by bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

