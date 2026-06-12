---
title: "slow disk IO since 14.04"
date: 2015-02-06
forum: Installation &amp; Upgrades
---

### Post by serge_o on 2015-02-06
I run several machines with Ubuntu Desktop and always update them to the next version (albeit gradually, one after another). after upgrading 5 of my machines to 14.04 I noticed a significant slow down in disk ops. Or maybe it is just more of them.  For instance, starting a chromium browser, or a firefox now takes 30-40 seconds of disk thrashing with IO, mostly reads. This was not so in 13.10
I first noticed this on a slow Intel I3 3GB laptop with HDD. This is my only 32 bit machine, at that point I thought this is because 32 bit, outdated, and the machine itself is slow. did not pay much attention.  But then I upgraded my Intel I7 8GB laptop (also HDD) and noticed the same increase in disk IO.
after that I upgraded my desktops (all have a minimum of 16 and up to 32 GB RAM, top intel I7) and noticed the same thing except for the 2 machines that had SSD.
Ok, SSD does not slow down, I get this, but why was 13.10 like 5 times faster on all my HDD machines?

I have not yet upgraded to 14.10, maybe I skip this for 15.04

does anybody notice the same thing?

---

### Post by TheFu on 2015-02-07
"Feeling" that things are slower isn't the same as having facts. We need to check a few things first and gather some information.
Pick 1 machine. only reply about that 1, please. We don't want to get confused.

* what file system is being used?  **cat /etc/fstab**
* how much RAM - **head -n 5  /proc/meminfo**
* how much swap - **swapon -s**
* are there any warnings or errors in the log files? **egrep -i 'error|warning' /var/log/*log**
* how full is the partition? This can impact performance when nearly full. **df -h**

To gather hdd performance information, we need **sudo hdparm -I {fill-in-the-hdd-device} ** output and may want to run some disk I/O data captures. These tools will tell us if the HDD is the issue or something at a higher level or if it is an application issue. Can't tell yet.
[http://askubuntu.com/questions/87035/how-to-check-hard-disk-performance](http://askubuntu.com/questions/87035/how-to-check-hard-disk-performance) has more ideas to provide facts.  The graphical version isn't much help to us in a forum. Copy/paste the text inside "code tags" here please, so the output lines up nice.

Tools like **iotop** might be useful too.

---

### Post by serge_o on 2015-04-05
hello
sorry for the late answer

and just to repeat myself - I have 3 (written: three) systems minimum affected by this strange slowdown after an 13.10-14.04 upgrade. The data below is from only one of them.

cat /etc/fstab
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=f8ee5cfa-f50b-420d-bd83-4606fdc12b9b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
#UUID=71e0ac7c-cdb6-4b98-b614-3f6e6077686d none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```


head -n 5 /proc/meminfo
```
MemTotal:       16335612 kB
MemFree:        13050992 kB
Buffers:          102496 kB
Cached:          1526680 kB
SwapCached:            0 kB

```

swapon -s
```
Filename                Type        Size    Used    Priority
/dev/mapper/cryptswap1                  partition    8290300    0    -1

```
egrep -i 'error|warning' /var/log/*log  
```
/var/log/bootstrap.log:Setting up libgpg-error0:amd64 (1.12-0.2) ...
/var/log/gpu-manager.log:Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
/var/log/kern.log:Apr   3 14:08:31 sergePC kernel: [    0.000000] ACPI Warning: 32/64 FACS  address mismatch in FADT - two FACS tables! (20131115/tbfadt-395)
/var/log/kern.log:Apr   3 14:08:31 sergePC kernel: [    0.000000] ACPI BIOS Warning (bug):  32/64X FACS address mismatch in FADT - 0xAAFE4E40/0x00000000AAFE4D40,  using 32 (20131115/tbfadt-522)
/var/log/kern.log:Apr  3 14:08:31 sergePC kernel: [   20.750126] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
/var/log/kern.log:Apr   3 14:08:31 sergePC kernel: [   21.911258] ACPI Warning:  0x0000000000000428-0x000000000000042f SystemIO conflicts with Region  \GPIS 1 (20131115/utaddress-251)
/var/log/kern.log:Apr  3 14:08:31  sergePC kernel: [   21.911265] ACPI Warning:  0x0000000000000428-0x000000000000042f SystemIO conflicts with Region  \PMIO 2 (20131115/utaddress-251)
/var/log/kern.log:Apr  3 14:08:31  sergePC kernel: [   21.911275] ACPI Warning:  0x0000000000000540-0x000000000000054f SystemIO conflicts with Region  \GPIO 1 (20131115/utaddress-251)
/var/log/kern.log:Apr  3 14:08:31  sergePC kernel: [   21.911278] ACPI Warning:  0x0000000000000540-0x000000000000054f SystemIO conflicts with Region  \GP01 2 (201:


```

how full is the partition : 14% used, 86% free. size 909G

---

### Post by serge_o on 2015-04-05
Just to add. 
I observed with iotop what happens after I start firefox (which takes about 50 sec on my above mentioned i7 16GB machine). I saw that a firefox Cache2 I/O process reads disk intensively for 50 seconds.

I went to check Cache2 in firefox and it was only 350 MB. So reading this whole Cache2 from disk would have taken maybe 10 seconds at most. 
As I see you have 14.04 as well (albeit Lubuntu) could you please post your cold firefox startup time ? By cold I mean shutdown the machine, poweron the machine, check time, start firefox, wait until it shows a page, check time.

I do not think reading Cache2 for 50 seconds is anything like normal, but it seems that all disk operations take longer than 13.10, I just caught firefox in this case as one example I could repeat and observe.

---

### Post by tgalati4 on 2015-04-06
Your swap is encrypted.  So is it possible that 13.10 was not encrypted and 14.04 is now encrypted?  

For the single machine that you have reported on, have you applied all of the 14.04 updates and rebooted?

---

### Post by serge_o on 2015-04-06
> **tgalati4 said:**
> Your swap is encrypted.  So is it possible that 13.10 was not encrypted and 14.04 is now encrypted?  

For the single machine that you have reported on, have you applied all of the 14.04 updates and rebooted?

1. I think it was encrypted because I did a regular update from 13.10 to 14.04 - it usually preserves everything. Is there a way to check this? a way to check how my swap was?

  Anyway MY MACHINE DOES NOT USE SWAP because it never goes up to 16GB! especially when it is slow I paid specific attention to this fact. My top always showes swap in use = 0;

I disabled swap with swapoff also in february and it did not remedy anything. 
I use iotop to monitor the load during the slowdown and it was not swapping.

so i am positively sure swap has nothing to do with the issue.

2. Yes I do regular updates via "updater" so the machine is always at the last version. Actually all my machines are.

---

### Post by TheFu on 2015-04-06
Any chance you will run the performance tests requested?

---

### Post by serge_o on 2015-04-07
Yes I will run the tests as described here
[http://askubuntu.com/questions/87035/how-to-check-hard-disk-performance](http://askubuntu.com/questions/87035/how-to-check-hard-disk-performance)

plus hdparm -l

as soon as possible today

---

### Post by TheFu on 2015-04-07
> **serge_o said:**
> Yes I will run the tests as described here
[http://askubuntu.com/questions/87035/how-to-check-hard-disk-performance](http://askubuntu.com/questions/87035/how-to-check-hard-disk-performance)

plus hdparm -l

as soon as possible today

That is an upper-case "eye" - just for clarity.  Always check the manpage before running any suggested commands here, BTW. YOU **and only you** are responsible if things go badly. Some of these commands might cause damage if done improperly. Be careful. Know what you are typing, especially with I/L/l/i options.  If you check the manpage, you'll see why you need to be very careful with this command.

---

### Post by tgalati4 on 2015-04-07
My comment on swap was to ascertain whether the entire OS was encrypted or only a few directories.  If the entire OS is encrypted (which would include an encrypted swap) then perhaps there is a bug or an issue running encryption that is causing the slow down.  It's possible that 13.10 was encrypted and now 14.04 is encrypted as well and of course in-place upgrades are convenient but not recommended because strange issues can appear.  Would you classify your slowdown as a strange issue?

If all 3 systems are the same, then I would take one, back up the important data, wipe it and perform a clean install of 14.04.  Perform the updates on 14.04; there will be several hundred megabytes worth.   Then compare performance of that machine with your existing systems that had an in-place upgrade.

It's possible that a kernel version is causing an issue with your motherboards.  What are the CPU's?

```
cat /proc/cpuinfo
```

---

### Post by serge_o on 2015-07-10
sorry for the late reply. I was very busy as many of us possibly. In order to investigate this issue I waited and did not install my brand new SSD into my laptop which I purchased in March.

I ran benchmarks like gnome disks read benchmark, dd of large files and the like. My HDD drive shows perfectly normals speeds for a 5400 laptop 2.5inch drive.
gnome disks shows around 100MB/s for its reading check, varying slightly from 70 to 100MB/s.
I can post the results in a screenshot of a gnome disks graph, but ...

while doing this I seem to have found the issue. This is my encrypted home folder!  The problem is that the performance degrades if you have very many files in your encrypted home folder.
reading the files requires too many IOPS from the drive (not throughput but IOPS)
here is the link where the developer of ecryptfs explains the issue. 
[http://superuser.com/questions/397252/ecryptfs-and-many-many-small-files-bad-performance](http://superuser.com/questions/397252/ecryptfs-and-many-many-small-files-bad-performance)

see the answer from user tyhicks (developer of ecryptfs).

I ran other checks to confirm this. for example du in my home folder runs like 50 times slower than on a normal folder.
to confirm this you can just get a folder with many files (a git clone of a linux kernel would do)
clone the folder into an encrypted home and into e.g. /opt/xxx
then do a clean reboot to ensure no read cache remains and do a "du" on this folder in /home. Time this.
then do a clean reboot once again to ensure no read cache remains and do a "du" on the folder in unencrypted /opt
the difference will be very noticeable, I get up to 50 times, the encrypted version requiring like 10 minutes to complete (atop, iostat both show disk load in the red zone doing this)
in a normal folder this takes  like 5-10-15 seconds in this range maybe, but not minutes.

If you have very many small files in your /home  (this is exactly my case on all my machines as I have many code projects with really many small files) then it also seems to slightly degrade read performance of any folder in your /home even if it does not have that much files in it.

my firefox is affected because its cache is many small folders. It takes a long time to start.

I already 

The answer why normal users does not have this is that if your file count in the encrypted folder is low then you do not really notice the issue, or maybe just only a minor slowdown.


I tested it without ecnryption for users with normal home folder and it works very good.

One thing that is unresolved is that I am pretty sure to have had an encrypted folder on 13.10 as well and did not notice such a slowdown. After the upgrade it became noticeable.

So great respect to the poster who suggested it may be the encryption!!

by the way, encrypted swap does not affect my performance because all my systems do not use the swap (I showed this in the first posts, swap is always at 0 usage because it is swapoffed)

Other encryption systems like truecrypt and dm-crypt do not affect the performance in this way, but they are not really standart for ubuntu (cannot enable dm-crypt with a mouse clik like you can with ecryptfs) I will stick to using ecryptfs just upgrading to an SSD (which will resolve the issue as the thing has more iops than the bus can handle :):)

thanks to everybody for attention, if there are questions to clear I can answer or do additional measurements.

---

### Post by serge_o on 2015-07-11
A question to moderatos: Is it possible to do the following? 

After this issue has been resolved it has become apparent that 
a) the topic name should be changed to "ubuntu ecryptfs encrypted home folder slow on many small files"
b) the topic should be moved somewhere else,  it does not have anything to do with upgrades or Ubuntu versions  (My first assumption it should have to do with 14.04 upgrade turned out to be wrong)

---

### Post by TheFu on 2015-07-11
The original poster can edit those things, I believe.  I know this because I asked for something similar a few months ago and was told where ... of course, I don't recall now. ;(

BTW - dm-crypt can be added to a running system (non-trivial), but it is much easier to do it at installation time.  Basically, setup a boot partition, then make the rest of the disk the remaining partition and put LVM onto it.  Then add PE (1), VG (1), and LVs (3+) as desired for /, /home, swap and other areas.
```
$ lsblk
NAME                            MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINT
sda                               8:0    0 119.2G  0 disk  
&#9500;&#9472;sda1                            8:1    0   243M  0 part  /boot
&#9500;&#9472;sda2                            8:2    0     1K  0 part  
&#9492;&#9472;sda5                            8:5    0   119G  0 part  
  &#9492;&#9472;sda5_crypt (dm-0)           252:0    0   119G  0 crypt 
    &#9500;&#9472;c720--vg-root (dm-1)      252:1    0  51.9G  0 lvm   /
    &#9500;&#9472;c720--vg-lv--swap (dm-2)  252:2    0   4.1G  0 lvm   [SWAP]
    &#9492;&#9472;c720--vg-lv--Home (dm-3) 252:3    0    50G  0 lvm   /home

```
You might need an efi partition, depends on your system. Mine is legacy booting.

---

