---
title: "Moving files from one harddrive to another take the system down to a crawl"
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by eyelessfade on 2009-04-16
I'm moving a lot of files (60 files, 20GB)from one harddrive to another both xfs partitions got the system down to a crawl. The load spiked at 13, and the system was almost useless while the move took place. The system is running from one of those disks, but the os should have a cap on transfer speed if that is whats causing the problem (save some bandwith for system use)


System: 2 x sata drives, 8Gb ram, c2d E8400. So it's not a slow system and even if it was this shouldn't happend.

---

### Post by jmmL on 2009-04-16
I experience the same thing; although I've never seen the load go as high as 15! It usual stays at around 5.

At the moment I experience it on jaunty and ext4, but I've also experienced it with intrepid ext3.

It's very annoying, and now I think of it, I don't know why I haven't complained before! :P

---

### Post by MattiJ on 2009-04-16
Same here, I been digging into this and it seems problem is that it uses all memory for buffer! I hawing 8GB but it's all gone into buffer during copy files. It is very sluggish even long time after the copy is done I found a way to get the memory back.
 ```
sudo sh -c "sync && echo 3 > /proc/sys/vm/drop_caches" 
```

It helps a little but is no solution to the problem!

Also there is an patch for rsynk 'Improving Linux performance by preserving Buffer Cache State'
using that I can copy anything without any slowdown.

[http://insights.oetiker.ch/linux/fadvise.html]("http://insights.oetiker.ch/linux/fadvise.html")

But I'm still locking for a final solution to this problem, to somehow limit the cache usage, for me it even started to use swap! so disabling that improved things a little bit.

---

### Post by ostrm on 2009-04-16
For copying, you could consider using rsync wich has an option to limit the bandwidth used for the file copy. To set a limit for example to ~ 10 MB/s use it like that
```
rsync --bwlimit=10000 -av /src/dir /dest/dir 
```
(about the other options, like -a and -v, look at man rsync)

I don't know about any direct solution for moving, the kernel's IO scheduler should take care of that. But mv between two different hdd is anyway a copy with a subsequent delete, so there should be no performance hit (apart from the bwlimit you set ;-) )

---

### Post by MattiJ on 2009-04-17
I also tested the --bwlimit option but it still eat all memory so don't give much improvement. If using the patched rsynk one can add the --drop-cache option.
 ```
rsync -v -r --drop-cache -l -t /src/dir /dest/dir
```

---

### Post by manuelb on 2009-04-17
> **MattiJ said:**
> 
But I'm still locking for a final solution to this problem, to somehow limit the cache usage, for me it even started to use swap! so disabling that improved things a little bit.

Have you tried [this]("http://rudd-o.com/en/linux-and-free-software/tales-from-responsivenessland-why-linux-feels-slow-and-how-to-fix-that") method? It seems is quite working for me, or at least the machine seems to really prioritize code execution.

---

### Post by eyelessfade on 2009-04-17
> **ostrm said:**
> For copying, you could consider using rsync wich has an option to limit the bandwidth 
No! this is solving the symptom not the problem. And besides I was moving :)

I've seen this problem on several systems, also-none ubuntu but never as bad as this.

---

### Post by MattiJ on 2009-04-17
Thanks for the tips, I now hawing 

```
vm.swappiness=1
vm.vfs_cache_pressure=40
```

in /etc/sysctl.conf 
Time will show if that helps, but I think Hi is right especially if one hawing a bit more ram.

---

### Post by eyelessfade on 2009-04-17
Oh yeah I have zero bytes of swap. Why? because I have 8G of ram and of no time did I use more then 1/4 of my ram total on my system.

---

### Post by ostrm on 2009-04-17
> **eyelessfade said:**
> No! this is solving the symptom not the problem. And besides I was moving :)


Solves at least a part, right? ;-)
And moving between two hdds is not like moving at one hdd, where only inodes are rewritten (and maybe a bit more, I'm not an expert). 
So you will not run into this problem in this case, there's not much to cache...

I'm really interested in a solution to this problem, I played for fun around a bit with what manuelb and MattiJ suggested. It seems to help for big files (O(GB)) but if you have thousands of O(MB) files the problem remains...

---

### Post by eyelessfade on 2009-04-17
> **ostrm said:**
> Solves at least a part, right? ;-)
And moving between two hdds is not like moving at one hdd, 
Partly right. On the same partition on the same disk :)

But yeah I hope it gets fixed.

Now I'm copying to a external usb drive. load 8.11. And this is a 2.5", 5400rpm disk so It didn't crawl my system, but still...

---

### Post by scaine on 2009-04-17
Has anyone raised a bug on launchpad about this?  Or checked to see if there's an existing bug?  It's late here.  If I get time, I'll check tomorrow.

---

### Post by MattiJ on 2009-04-17
It certainly could be a bug even if it's on all systems, maybe it worse in Jaunty but had same problem also in Feisty, Gutsy and Hardy not to mention all windoz*. 

When sys is newly rebooted all is snappy an responsive but 24h later sys is fairly sluggish and all memory is eaten. Reboot or freeing chase make it snappy again!

All I can say is that 8GB worth of mem is not well used. But ```
vm.swappiness=1
vm.vfs_cache_pressure=40
```
in in /etc/sysctl.conf does improve a lot! gonna try lover vm.vfs_cache_pressure even more.

---

