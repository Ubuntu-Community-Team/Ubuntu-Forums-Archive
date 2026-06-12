---
title: "High RAM usage at boot"
date: 2010-02-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by LADmaticCA on 2010-02-15
Hello. I notice my system reports a high amount of RAM being used on a fresh boot. High meaning about 800MB. The only start-up program I added was pidgin. Doing rough math from the system monitor my ram usage should be about 380-400MB, which is what I expect. Anyone else getting this? Oh, I'm running 64bit Lucid.

---

### Post by vade on 2010-02-15
That probably includes system cache so it should be ok. You can see the size of the system cache with 'top' (cached). System cache is freed as programs need memory.

---

### Post by LADmaticCA on 2010-02-15
> **vade said:**
> That probably includes system cache so it should be ok. You can see the size of the system cache with 'top' (cached). System cache is freed as programs need memory.

Thanks for the response. I thought system cache was cleared on a reboot? Am I wrong?

---

### Post by mharrison on 2010-02-15
I could be wrong, but from watching my system, system cache starts to build as the computer is idle or as you close down programs.  Not sure about a fresh boot, but my system starts with 5% of my memory being used (roughly 200 megs) and if I open my VirtualBox install of XP to sync my Ipod it uses 50% of my memory, but when I close VirtualBox that memory that was in use stays as system cache....or at least a chunk of it does.  If I don't do anything after a fresh boot, say boot up in the morning and then leave to go get ready for work, I can come back and the 5% is still in use but there is 20% cached.

---

### Post by dino99 on 2010-02-16
could you load htop and see what process eat cpu & memory. Whith that info it's easier to find a solution.
On my end, pulseaudio is doing that kind of problem til i start it into console.

---

### Post by LADmaticCA on 2010-02-16
> **dino99 said:**
> could you load htop and see what process eat cpu & memory. Whith that info it's easier to find a solution.
On my end, pulseaudio is doing that kind of problem til i start it into console.

Virtuoso-t seems to be using the most ram for me. I think I may have installed that when I added the kubuntu-desktop. Not even sure what it is.

---

### Post by andrewabc on 2010-02-16
So you go to
system->admin->system monitor->resources tab and it shows 800mb on startup?
Unless they changed sys monitor to include cache, it shouldn't be that high.

On 9.10 fresh start I only use 400mb or so. Currently running for 24 hours and sys monitor is reporting 1.1gb.

$ cat /proc/meminfo 
Shows
> MemTotal:        3071472 kB
MemFree:           53580 kB
Buffers:          732580 kB
Cached:          1150660 kB
SwapCached:           32 kB
Active:          1385108 kB
Inactive:        1564616 kB
Active(anon):     859696 kB
Inactive(anon):   277988 kB
Active(file):     525412 kB
Inactive(file):  1286628 kB
Unevictable:           0 kB
Mlocked:               0 kB
HighTotal:       2210696 kB
HighFree:          31628 kB
LowTotal:         860776 kB
LowFree:           21952 kB
SwapTotal:        506008 kB
SwapFree:         505976 kB
Dirty:               272 kB
Writeback:             0 kB
AnonPages:       1066464 kB
Mapped:            98252 kB
Slab:              45516 kB
SReclaimable:      27336 kB
SUnreclaim:        18180 kB
PageTables:         6160 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:     2041744 kB
Committed_AS:    1668792 kB
VmallocTotal:     122880 kB
VmallocUsed:       14796 kB
VmallocChunk:     103404 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       4096 kB
DirectMap4k:       16376 kB
DirectMap4M:      892928 kB

Which is normal for me.

How much ram in your computer?
I don't think it should use 800mb on a fresh install/boot. Unless some new technology is auto putting stuff into cache (assuming they've combined cache+ram in sys monitor).

preload is supposed to put most used files into ram on startup. It doesn't work for me on 9.10 though.

---

### Post by dino99 on 2010-02-17
> **LADmaticCA said:**
> Virtuoso-t seems to be using the most ram for me. I think I may have installed that when I added the kubuntu-desktop. Not even sure what it is.

so, if you have made lot of tweaking by the past, maybe it's time to clean it up a little bit ;)

you have several ways to do that:
- remove old settings and packages with "computer janitor"
- install gtkorphan (gnome) to find unused packages
- or better: install "bleachbit" and run it (take care to understand what you are doing, it's powerfull ;))

---

### Post by LADmaticCA on 2010-02-17
> So you go to
system->admin->system monitor->resources tab and it shows 800mb on startup?

> you have several ways to do that:
- remove old settings and packages with "computer janitor"
- install gtkorphan (gnome) to find unused packages
- or better: install "bleachbit" and run it (take care to understand what you are doing, it's powerfull ) 

Thanks for the replies everyone. 

I ran bleachbit and removed virtuoso-t my ram is around 655MB on a fresh boot. Less, but still more than my jaunty 64bit which is around 400MB. I have 4gigs of ram.

---

### Post by Yellow Pasque on 2010-02-17
Can we see the output of:
```
free -m
```

---

### Post by andrewabc on 2010-02-17
> **Temüjin said:**
> Can we see the output of:
```
free -m
```

On a fresh boot. :)

---

### Post by LADmaticCA on 2010-02-18
> **andrewabc said:**
> On a fresh boot. :)

I'm not sure what's changed but it appears to be about normal now.

```
luciousjr@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3965        643       3322          0         52        177
-/+ buffers/cache:        413       3552
Swap:         2086          0       2086
```

---

### Post by andrewabc on 2010-02-18
> **LADmaticCA said:**
> I'm not sure what's changed but it appears to be about normal now.

```
luciousjr@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3965        643       3322          0         52        177
-/+ buffers/cache:        413       3552
Swap:         2086          0       2086
```

Next time you reboot do

cat /proc/meminfo 

It will give more detailed info.

643 still seems high. Unless ubuntu is now loading more on startup.

---

### Post by Yellow Pasque on 2010-02-18
It's not 643. It's 643 - 413 = 230MB actually used.

---

### Post by lavinog on 2010-03-10
ureadahead might be the issue since it seemed to fix itself after boot:
[https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715](https://bugs.launchpad.net/ubuntu/+source/ureadahead/+bug/501715)

---

### Post by hardran3 on 2010-03-26
I am running Lucid on 2 machines. The first is a Aspire One Netbook. It is a minimal install, xorg, gnome-core, and a browser (chromium) If I check immediately at boot it is using around 120MB, but then this happens

```
             total       used       free     shared    buffers     cached
Mem:          1496       1245        250          0         18        760
-/+ buffers/cache:        467       1029
Swap:            0          0          0
```

And this is with me doing nothing.

2nd machine is a desktop with a dual core atom and 1GB of RAM, and a full install of Lucid. ~350MB at boot, but soon jumps up to ~660MB, on an idle machine.

---

### Post by lavinog on 2010-03-27
> **hardran3 said:**
> I am running Lucid on 2 machines. The first is a Aspire One Netbook. It is a minimal install, xorg, gnome-core, and a browser (chromium) If I check immediately at boot it is using around 120MB, but then this happens

```
             total       used       free     shared    buffers     cached
Mem:          1496       1245        250          0         18        760
-/+ buffers/cache:        467       1029
Swap:            0          0          0
```

And this is with me doing nothing.

2nd machine is a desktop with a dual core atom and 1GB of RAM, and a full install of Lucid. ~350MB at boot, but soon jumps up to ~660MB, on an idle machine.
use htop and press shift-m to sort by memory usage, and find out what is using most of your memory.
It could be a memory leak or just the package manager running in the background...there have been a couple of reports that it uses a lot of memory.

---

