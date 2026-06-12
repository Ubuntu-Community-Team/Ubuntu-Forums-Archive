---
title: "Can't Upgrade Ubuntu: No Space on /"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by apolloxi on 2008-06-01
I am currently using Ubuntu 7.04 and I would like to upgrade to 7.10 (and then to 8.04). However, when I go to do so through the Update Manager, I get an error saying I don't have enough space on "/".

So, I went to the Disk Usage Analyzer and, according to that, my usage for "/" is at 100%...which makes no sense to me. My laptop has two hard drives, Windows XP being on one of them (C), and Ubuntu 7.04 being on the other (D), and my D Drive has plenty of space. Each drive has 50GB of space, and my D Drive has about 25 to 30GB of free space...so, obviously, space is not an issue.

Perhaps it has to do with my partitioning? Like, for instance, I have a separate "/" partition that's full? I forgot how I set it up, though, and I forgot how to look at it.

If anyone could tell me what my problem is and how to fix it, I'd really appreciate it.

---

### Post by Pumalite on 2008-06-01
Post:
sudo fdisk -lu
df -h

---

### Post by KenBW2 on 2008-06-01
GParted is a good way to see your drives' partitions.

Install gparted:
> 
sudo aptitude install gparted


Then
System > Administration > Partition Editor

Your Ubuntu partition is the one that's marked as / under Mountpoint

---

### Post by apolloxi on 2008-06-01
Results of sudo fdisk -lu:

> Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63     6152894     3076416   12  Compaq diagnostics
/dev/hda2   *     6152895   100534769    47190937+   7  HPFS/NTFS
/dev/hda3       100534770   110302289     4883760   83  Linux
/dev/hda4       110302290   195366464    42532087+   5  Extended
/dev/hda5       117242370   195366464    39062047+  83  Linux
/dev/hda6       110302416   117226304     3461944+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   976768064   488384001    7  HPFS/NTFS


Results of df -h:

> Filesystem            Size  Used Avail Use% Mounted on
/dev/hda3             4.6G  3.1G  1.3G  71% /
varrun                474M  100K  474M   1% /var/run
varlock               474M     0  474M   0% /var/lock
procbususb            474M  132K  474M   1% /proc/bus/usb
udev                  474M  132K  474M   1% /dev
devshm                474M     0  474M   0% /dev/shm
lrm                   474M   33M  441M   7% /lib/modules/2.6.20-16-generic/volatile
/dev/hda5              37G   16G   19G  46% /home
/dev/hda1             3.0G  1.9G  1.1G  63% /media/hda1
/dev/hda2              46G   39G  7.0G  85% /media/ACER
/dev/sda1             466G   27G  439G   6% /media/FreeAgent Drive


Also, installed GParted.

My "dev/hda3" partition, mountpoint "/", has a size of 4.66GB, 3.16GB of which has been used. 1.49GB is unused.

The error I always get when I try to upgrade says that I need 1650MB to upgrade. I am guessing that translates to about 1.65GB...in which case, I fall 2GB short. At least this makes more sense to me than / being 100% full.

Is this correct, or is something else going on here?

---

### Post by Pumalite on 2008-06-01
You can see for yourself the space you have.

---

### Post by apolloxi on 2008-06-01
> You can see for yourself the space you have.

Well, then, I now ask this question: what course of action should I take?

Should I...

1. Try to free on space on the "/" partition, if that's even possible? And, if it is possible, how do I? I don't want to risk killing the system.

Or, 2. Simply resize these the "/" partition to be bigger?

If possible, I'd like to do choice 1, since it's easier and less time-consuming. I would just like some guidance on what to delete and how to delete it, if deleting from "/" is even a wise or possible option at all.

I heard "sudo apt-get clean" is a good way, but I have already done that numerous times.

---

### Post by Pumalite on 2008-06-01
Post a screenshot of Gparted

---

### Post by apolloxi on 2008-06-01
Here it is.

---

### Post by Happy_Man on 2008-06-01
That's interesting... try some basic housekeeping stuff, such as emptying the Trash and running ```
sudo apt-get clean
``` from the Terminal. Then see if it works.

---

### Post by apolloxi on 2008-06-01
@ Happy_Man: I've already ran "sudo apt-get clean" numerous times, and I still don't have sufficient space. There doesn't seem to be anything else to clean.

Also, my Trash is empty. I always make sure it never builds up.

Beyond this, I don't know what else to do to free up space on "/".

Extra info, if it helps anyone: I have my D Drive (which is my entire Ubuntu Drive) set up in two different partitions (following the suggestion of [this guide]("http://www.psychocats.net/ubuntu/partitioning")): / and /home. I did the last dual-boot scenario on that page. "/" is the problem, as it has too little free space.

---

### Post by Pumalite on 2008-06-01
It seems '/' can only be expanded to the left and very little. Get Gparted Live CD to do the job. Backup everything first. It will take a while.
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.

---

### Post by apolloxi on 2008-06-02
> It seems '/' can only be expanded to the left and very little. Get Gparted Live CD to do the job. Backup everything first. It will take a while.

I had a feeling this was my only option. I'll do that, then.

Thanks for all of your help.

One last question, though (the answer is probably obvious, but I just wanna make sure): I'd prefer to take away from hda5, instead, since it has more free space, but I realize it's a sub-partition of the overall partition of hda4, which doesn't seem to be resizeable. Is there a way to get around that to be able to resize hda5, or is it pretty much impossible or not worth it?

---

### Post by apolloxi on 2008-06-02
?

---

### Post by Pumalite on 2008-06-02
You care asking the impossible as far as I know.

---

