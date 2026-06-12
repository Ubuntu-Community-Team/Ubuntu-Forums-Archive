---
title: "Where did the rest of my harddrive go?"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by openheart on 2008-02-29
Ok guys I am new here so bear with me..

My machine has a 100GB IDE drive in it.

after an installation of Ubuntu the Operating system tells me that I have 88.9 GB free...

My question is where did the missing 11.1 GB go?

Now since I have 1 GB of RAM installed I am assuming that about 3GB have been allocated as a swap file but that still leaves about 8.1 GB missing..

Here is the output of df-h

$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              89G  2.5G   82G   3% /
varrun                  506M   96K  506M   1% /var/run
varlock                 506M  8.0K  506M   1% /var/lock
udev                    506M   64K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                      506M   34M  472M   7% /lib/modules/2.6.22-14-generic/volatile

here is the output of sudo fdisk -lu

Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   189309959    94654948+  83  Linux
/dev/hda2       189309960   195366464     3028252+   5  Extended
/dev/hda5       189310023   195366464     3028221   82  Linux swap / Solaris

it seems that I am at a real loss here.. any suggestions.. where did the other space go?

---

### Post by taurus on 2008-02-29
If you want to know how space you use for swap partition, run 

```
free
```
And if you are using ext3 filesystem, 5% of disk space is reserved for root in case you fill up your root filesystem, you can still boot up in recovery mode to remove or fix your partition.

p.s.  How come /dev/hda1 starts at 63 instead of 1?

---

### Post by openheart on 2008-02-29
here is the result of that command 

free
             total       used       free     shared    buffers     cached
Mem:       1035696     552760     482936          0      65164     260752
-/+ buffers/cache:     226844     808852
Swap:      3028212          0    3028212

but my question still stands .. where did the rest of my Hardrive go.. from what I can tell it looks like 3 gigabytes have been used here but where did the remaining 8 gb go?

about starting at 63.. i dont know.. can you help me to investigate?

---

### Post by openheart on 2008-02-29
Should I be worried that dev/hda1 starts at 63 instead of 1? A long time ago I had discovered a virus on this PC and disinfected it. Those were the days when I was running in a windows xp environment.. but I had since disinfected it it prior to installing ubuntu.. could this be a remnant? is there a way of proceeding to investigate it?

---

### Post by logos34 on 2008-02-29
OS's see disk capacity differently than hard drive manufacturer specs, where 1 GB = 1,000,000,000 bytes, or base 10 (10^10, exponential form).

linux and windows (in fact all OSs) measure space in base 2 form, where 1 GB =1,073,741,824 bytes

[http://www.hardwaresecrets.com/printpage/482/1](http://www.hardwaresecrets.com/printpage/482/1)

So your "100 GB" drive is like mine, it's really a ~93 GB drive.  Minus the above-mentioned 5% reserved space and the installed ubuntu, it sounds about right.

---

### Post by openheart on 2008-02-29
Firstly how can I thank you?

Secondly should I be worried that /dev/hda1 starts at 'block' 63 instead of 1? why would that be?

---

