---
title: "Error while installing system upgrades. Possibly because of low HD space."
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by odakrell on 2012-07-05
Hey. Thanks for reading.

I'm using xubuntu 11.10 on an Asus eee PC X101. My root partition is ~6 GB big, swap is ~500 MB, home is ~1 GB (pathetic, I know, but xubuntu is intended for low-end computers, right?).

My Update Manager is set to only download and apply **important security updates**. Despite this setting, I've noticed that over the past year or so, my root partition continually filled up. I don't remember exactly how much space was used after the fresh install, but it was in the range of **3 GB**. Add to that at most **1 GB** for programs I installed myself, leaving me with about **2 GB**. That free space has been getting **smaller and smaller with each update process**, or at least that's my impression. **Note**: I reguarly ran sudo apt-get clean to remove old installation packages, but that didn't reverse the trend by much.

I now have about 500 MB free on root, and a few days ago, the Update manager ran again, downloading and installing an **upgrade to the Linux kernel** (if I remember it right), then threw an error that I can't find anymore. Since then, any attempt to open the Update Manager leads to the warning **Not all updates can be installed**, and the query if I want a **Partial Upgrade**. If I confirm, a window named **Distribution Upgrade** pops up, and closes shortly afterwards. In the short time it is open, I can read something about **No space left on device**. 

Okay, finally, my questions:

**(1)** **Is this caused by too little space on my root partition?** Like I said above, I still have above 500 MB free space on my root, but maybe that's not enough. So I don't really know if that is what causes the upgrade error.

**(2) Assuming it is related to HD space, can I fix it without re-installing xubuntu?** Pretty self-evident question. I already ran apt-get clean and apt-get autoremove to get additional free space, but I don't know what else I can do to free up more space on root. (**Note:** un-installing programs is not the solution. Like I said above, I have hardly installed anything manually)

**(3)** **Assuming I need to re-install, how can I avoid this problem in the future?** Since I already avoided installing additional programs, and I set the Upgrades to "Important only", I don't really know how I can prevent xubuntu from gobbling up all my HD space like that. Is there a way to **force xubuntu to minimize space,** after installation? I mean, a 6 GB root is pretty small, but shouldn't it be enough to run xubuntu continuously?

---

### Post by dino99 on 2012-07-05
if you succeed then you're a lucky guy  :P

you seems begging butter and the butter money  :D

---

### Post by spjackson on 2012-07-05
"No space left on device" when  installing upgrades does imply that your  root partition (or other system partition - depending how you've carved  it up) is full.

I think 6GB should be quite adequate for a root partition, depending on what you want to install of course.

Here are some things to look at:
```

df -h
sudo du -sk /tmp /var/mail /var/spool /var/log

```Does xubuntu include Baobab (Disk Usage Analyzer) or something similar?

---

### Post by odakrell on 2012-07-05
> **dino99 said:**
> if you succeed then you're a lucky guy  :P

you seems begging butter and the butter money  :D

I don't think I get what you're saying.

---

### Post by odakrell on 2012-07-05
> **spjackson said:**
> 
Here are some things to look at:
```

df -h
sudo du -sk /tmp /var/mail /var/spool /var/log

```

```

>df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             6.0G  5.2G  589M  90% /
udev                  490M  4.0K  490M   1% /dev
tmpfs                 199M  904K  198M   1% /run
none                  5.0M     0  5.0M   0% /run/lock
none                  497M  164K  497M   1% /run/shm
/dev/sda2             961M  353M  560M  39% /home

>sudo du -sk /tmp /var/mail /var/spool /var/log

29844    /tmp
4    /var/mail
52    /var/spool
6952    /var/log

```> 
Does xubuntu include Baobab (Disk Usage Analyzer) or something similar?
I can't find any dedicated DUA. There's a "System Profiler" that includes a disk usage overview, but the output of that seems to be the same information as **df -h**. I would install Baobab, but I can't: any attempt to install via command line or Synaptic leads to an error (see below).

I just found this Disk Usage guide [(http://ubuntuforums.org/showthread.php?t=1122670]("http://ubuntuforums.org/showthread.php?t=1122670")) which suggests removing older kernel via Synaptic, but when I start Synaptic, I get the error:

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```Running **dpkg --configure -a** gives me the "not enough space" error again. Bit of a vicious circle...

---

### Post by spjackson on 2012-07-06
It is surprising that you get no space left on device when you have over 0.5GB free. However, you can get this error if the filesystem is out of inodes. What does
```
 df -i
``` report?

---

### Post by odakrell on 2012-07-06
```
>df -i
Filesystem            Inodes   IUsed   IFree IUse% Mounted on
/dev/sda3             398272  397585     687  100% /
udev                  125296     476  124820    1% /dev
tmpfs                 127048     380  126668    1% /run
none                  127048       1  127047    1% /run/lock
none                  127048      13  127035    1% /run/shm
/dev/sda2              62464    5772   56692   10% /home
```

Hm, no idea what Inodes are, but 100% use doesn't sound good. What should I do now?

---

### Post by spjackson on 2012-07-06
> **odakrell said:**
> Hm, no idea what Inodes are, but 100% use doesn't sound good. What should I do now?
Yes, the fact that the / partition has 100% of its inodes used is almost certainly the cause of the "no space left on device" error.

An inode is essentially a file or directory. Running out of inodes is usually caused by having very many small or empty files (or directories).

As far as I know, it isn't possible to increase the inode allocation without backing up the partition, recreating the filesystem with an increased inode allocation and then restoring from the backup. There may be a way but I'm not an expert in this area.

What I would do in your situation would be to look for lots of unnecessary files and remove them. I'd start with /tmp and possibly /var/log . It's possible that empty (or small) files are being created elsewhere, but I'd suggest starting with /tmp.

---

### Post by Onesimus on 2012-07-06
Have you tried 

```
sudo apt-get clean
```
This will remove all the temporary files that you have downloaded during the software updates.  It could free as much as 500Mb.

---

### Post by odakrell on 2012-07-06
> **spjackson said:**
> What I would do in your situation would be to look for lots of unnecessary files and remove them. I'd start with /tmp and possibly /var/log . It's possible that empty (or small) files are being created elsewhere, but I'd suggest starting with /tmp.

I'll do that and report back.

One question: I guess while I'm looking for small/empty files to remove, I could also try and see if there bigger files that I could delete that used up all my space in the process of updating. Is there some known list of Linux directories that only contain temporary or backup files, i.e. files that I can delete safely if I'm willing to remove the abilty to roll back changes, etc.?

---

### Post by odakrell on 2012-07-06
> **Onesimus said:**
> Have you tried 

```
sudo apt-get clean
```This will remove all the temporary files that you have downloaded during the software updates.  It could free as much as 500Mb.

Thanks. I already tried that, and it did free up some space, but still only a fraction of what was used in the past update processes.

---

### Post by odakrell on 2012-07-07
Thanks everybody, especially spjackson for the suggestion to check inodes. 

My system works again, and the Update Manager doesn' throw an error anymore. Here's how I got there:

As per suggestion of spjackson, I cleaned out /tmp and /var/log. That freed up about 1k inodes, but wasn't enough. Then I also nuked /var/cache, which was probably a mistake, as a number of programs had some trouble running after system restart. Nothing permanent however, it seems, because after another restart they seem to work fine again.

I then followed some suggestions in this guide ([http://en.gentoo-wiki.com/wiki/Freeing_Up_Disk_Space](http://en.gentoo-wiki.com/wiki/Freeing_Up_Disk_Space)) on how to free up space, though I didn't use the program they recommended but just followed their general suggestions which directories can be (partially) deleted.

In the end what made the difference was **/usr/src**, i.e. the source files of previous kernel versions (apologies if I use the wrong terminology, I'm pretty green when it comes to Linux). I deleted about 12 old kernel versions, only leaving the current and the one-before-current version in place. That freed up almost 1GB of space and about 200k inodes, bringing my inode usage from 100% to 57%. That was all I really needed to do. Maybe somebody else with a similar problem should try this as a first step, it seems to have a drastic influence if you're running out of HD space/number of free inodes.

Thanks again for your help!

---

