---
title: "Ruined encrypted partition."
date: 2008-12-09
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by fwhr on 2008-12-09
I've burned a LiveCD 9.04 alfa i386 daily build from 08/12/08 and booted my laptop from this CD. After this I rebooted my laptop, but now I can't mount encrypted /home partition - I enter right password, but have no luck... Why?
I've booted from this CD again in hope of understanding what's wrong with my partition and now I see a problem. 
I have 3 partitions on my disk:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a20f00c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         765     6144831   83  Linux
/dev/sda2   *         766        5227    35840000    7  HPFS/NTFS
/dev/sda3            5228       14593    75232395   83  Linux
```

Where sda1 is my /root partition and sda3 is my encrypted /home partition. Yes, I have no swap (not using sleep or hibernate mode).

BUT look at this:

```
ubuntu@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       2064464    1291720     772744          0     109044     650748
-/+ buffers/cache:     531928    1532536
**Swap**:      2498096          0    2498096
```

And at this:

```
ubuntu@ubuntu:~$ swapon -s
Filename				Type		Size	Used	Priority
**/dev/sda3**                               partition	2498096	0	-1
```

So, first time I boot JJ (like this time, too), my /home partition was mounted as swap and the result is on the thread name...

Thank God I have no unsaved valuable data on /home
So, I do not advise to repeat my experiment with a similar partitioning of HDD, like I have (But I think it's some sort of rare partitioning ;)).

---

### Post by plun on 2008-12-09
I checked the kernel GIT and it seems that support for encrypted partitions is coming

[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=summary](http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-jaunty.git;a=summary)

> UBUNTU: Build ecryptfs into the kernel

Bug: #302870



Latest change....but I can be wrong..

---

### Post by scradock on 2008-12-09
Surely the problem here is that a liveCD is assigning a swap partition AT ALL. If I put a LiveCD into my machine and boot from it, without asking for any install of the OS, I DON'T expect it to write anything anywhere on my disk, do I?

I don't believe the problem lies with encryption, enabled or not. It's simply an egregious error in the LiveCD that it writes to the HD instead of keeping everything in RAM.

---

### Post by ronacc on 2008-12-09
you are correct it is very bad that the live cd would make any changes to your system without being specificly told to infact it should run without even having a HD installed on the system.
@fwhr file a bug on this one .

---

### Post by xebian on 2008-12-10
This is quite interesting too in that if it's a swap the type should have been 82 and looks like this

```

/dev/sda11          13377       23345    80075961   83  Linux
/dev/sda12          23346       24321     7839688+  82  Linux swap / Solaris

```

---

### Post by fwhr on 2008-12-10
> **ronacc said:**
> 
@fwhr file a bug on this one .

Sorry, I am not familiar with launchpad. What package/project I need to choose to report a bug?

---

### Post by scaine on 2008-12-10
I think you just visit [https://launchpad.net/ubuntu/jaunty/](https://launchpad.net/ubuntu/jaunty/) and click on "Report a Bug".

---

### Post by ronacc on 2008-12-10
If you leave the package you are fileing the bug against as "I don't know" the person that triages the report will assign it to a package. just describe what happened as best you can . they will ask for more info if they need it.

---

### Post by tawmas on 2008-12-10
This page from the wiki provides a few guidelines for selecting the proper package: [https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage)

I think the relevant advice for your case is this:

> If you encounter a bug when using the Live CD environment, not the install process, and there is no more obvious package to use (e.g. a particular application is failing), then the package used for the bug should be casper.

---

