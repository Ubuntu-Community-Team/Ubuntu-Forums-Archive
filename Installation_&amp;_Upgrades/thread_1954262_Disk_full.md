---
title: "Disk full ??"
date: 2012-04-07
forum: Installation &amp; Upgrades
---

### Post by MatthewJS on 2012-04-07
I get:
```
 
df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda2              2885812   2383472    355748  88% /
none                   1668284       280   1668004   1% /dev
none                   1672528      7008   1665520   1% /dev/shm
none                   1672528       216   1672312   1% /var/run
none                   1672528         0   1672528   0% /var/lock
none                   1672528         0   1672528   0% /lib/init/rw
/dev/sda5              4806904   1290864   3271856  29% /tmp
/dev/sda8            440152152 192974224 224819468  47% /home
/dev/sda3              6728312   5099452   1287080  80% /usr
/dev/sda6             19228276    255560  17995968   2% /usr/local
/dev/sda7              4806904    681868   3880852  15% /var

```

when I execute df. As you can see all partitions have space. I get:
```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following extra packages will be installed:
  linux-headers-2.6.32-40 linux-headers-2.6.32-40-generic
The following NEW packages will be installed
  linux-headers-2.6.32-40 linux-headers-2.6.32-40-generic
0 upgraded, 2 newly installed, 0 to remove and 131 not upgraded.
2 not fully installed or removed.
Need to get 0B/10.7MB of archives.
After this operation, 85.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 478750 files and directories currently installed.)
Unpacking linux-headers-2.6.32-40 (from .../linux-headers-2.6.32-40_2.6.32-40.87_all.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.32-40_2.6.32-40.87_all.deb (--unpack):
 error creating directory `./usr/src/linux-headers-2.6.32-40/arch/um/os-Linux/sys-i386': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: subprocess paste killed by signal (Broken pipe)
Unpacking linux-headers-2.6.32-40-generic (from .../linux-headers-2.6.32-40-generic_2.6.32-40.87_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.32-40-generic_2.6.32-40.87_i386.deb (--unpack):
 error creating symbolic link `./usr/src/linux-headers-2.6.32-40-generic/include/linux/smp.h': No space left on device
No apport report written because the error message indicates a disk full error
                                                                              Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.32-40_2.6.32-40.87_all.deb
 /var/cache/apt/archives/linux-headers-2.6.32-40-generic_2.6.32-40.87_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

when I execute sudo apt-get -f install. It doesn't make sense to me. It is reporting that there is no disk space left but clearly there is. Anyone got any ideas?

Regards,

Matthew ](*,)

---

### Post by darkod on 2012-04-07
Yes, you do have the 85MB mentioned but I wonder if it complains about root being 88% full. You can't expect it to accept a 100% full root.

The disk full message does mention /usr and not /, but who knows...

---

### Post by BertN45 on 2012-04-07
Linux reserves 5% of the disk space to be sure it still can work and be upgraded, maybe you are running against that limit during the upgrade. You could change that limit as discussed below.

[http://ubuntuforums.org/showthread.php?t=1372331](http://ubuntuforums.org/showthread.php?t=1372331)

---

### Post by iponeverything on 2012-04-07
check your available inodes

```
df -i 
```

---

### Post by MatthewJS on 2012-04-08
> **iponeverything said:**
> check your available inodes

```
df -i 
```
I get:
> df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda2             183264   68466  114798   38% /
none                  212173     814  211359    1% /dev
none                  214294      11  214283    1% /dev/shm
none                  214294      64  214230    1% /var/run
none                  214294       2  214292    1% /var/lock
none                  214294       3  214291    1% /lib/init/rw
/dev/sda5             305824    2857  302967    1% /tmp
/dev/sda8            27951104  328293 27622811    2% /home
/dev/sda3             427392  420918    6474   99% /usr
/dev/sda6            1221600    1517 1220083    1% /usr/local
/dev/sda7             305824   13718  292106    5% /var

---

### Post by roelforg on 2012-04-08
> **MatthewJS said:**
> I get:

/usr is full to the brim
it can't write it's stuff there

---

### Post by MatthewJS on 2012-04-08
> **roelforg said:**
> /usr is full to the brim
it can't write it's stuff there

Thx roelforg. Pardon my ignorance - what can I do about this? Is there some way I can expand /usr (I seem to have capacity elsewhere)?

---

### Post by roelforg on 2012-04-08
> **MatthewJS said:**
> Thx roelforg. Pardon my ignorance - what can I do about this? Is there some way I can expand /usr (I seem to have capacity elsewhere)?

I'd like to know why it's on a seperate partition in the first place as you don't seem to really understand hd-partitions and are probably a beginner (no offense, i was once like that as well)

---

### Post by MatthewJS on 2012-04-08
> **roelforg said:**
> I'd like to know why it's on a seperate partition in the first place as you don't seem to really understand hd-partitions and are probably a beginner (no offense, i was once like that as well)

I took advice from a website  :oops:

Is there anything straightforward that I can do about it?

---

### Post by roelforg on 2012-04-08
> **MatthewJS said:**
> I took advice from a website  :oops:

Is there anything straightforward that I can do about it?

Short answer: no
Long answer: putting seperate essential dirs on seperate partitions is a good idea if you know what youre doing, otherwise it'll be nothing but trouble. I advise adding a second hd and using unionfs(easiest),aufs or similar to merge both partitions on both drives so the second one can take any new writes.

---

### Post by oldfred on 2012-04-08
I think it was 10 or 15 years ago when I installed Redhat for the first time that I had to use separate partitions for system folders. That still can be the case for a server where you may want to have more space for certain applications or security.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Now with most desktops you just need / (root) and maybe swap. Although some use no swap if they have lots of RAM or use a swapfile. Many of use like to separate data from system, so we have /home separate or use separate /data partition(s).

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)


Since you have a separate /home, it would not be difficult to reinstall with just / & swap. If you made custom system settings, you might also backup /etc. Just use manual install, create a 25GB / (root) partition and mount current /home  as /home but DO NOT format it.

---

### Post by roelforg on 2012-04-08
OldFred is right, generally you just use / and swap unless you've got good reason.
I have all my data (personal files+backup of /etc and package list) on a second drive, it's mounted as /data on boot.
If i nuke hd1, the other one still has enough data to rebuild my system.
Besides that there are several shares mounted.
But i still keep /usr on /

---

