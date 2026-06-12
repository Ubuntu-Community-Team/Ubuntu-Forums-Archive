---
title: "Why is Karmic faster?"
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by froggyswamp on 2009-08-13
Folks, who knows, what exactly contributed to Karmic for actually working faster? I don't mean bootup speed, but actual execution speed. Is it thanks to GCC 4.4 and hence system libraries allegedly being better optimized?

Facts:
Sunspider benchmark on Jaunty x64 vs Karmic x64 respectively:
Google Chrome dev channel: 970ms vs 674ms
Firefox (32bit) 3.5.2: 2450ms vs 2055ms

That's about 20-30% faster!

I also have winXP (32bit) and windows 7 (x64) on this computer and Google Chrome in Karmic is as fast as in winXP and 10% faster than in windows 7!

Hopefully Karmic doesn't "revert" to the "usual Linux" speed when it goes final.

---

### Post by godhika on 2009-08-13
While I don't know about all the things which make Karmic faster than Jaunty, I am quite positive that it has at least partially something to do with the newer kernel. There have been some severe regression with SQLite with the kernels up to including 2.6.28 (the version Jaunty was shipped with). Karmic comes with kernel version 2.6.31. Look here [http://www.phoronix.com/scan.php?page=article&item=linux_2629_benchmarks&num=4]("http://www.phoronix.com/scan.php?page=article&item=linux_2629_benchmarks&num=4")

---

### Post by froggyswamp on 2009-08-13
I'm aware of that (SQLite read/write) regression but it shouldn't have anything to do with the JavaScript performance that Sunspider is all about, thus it's something else and as a newbie - gcc 4.4 is all that I can think of.

---

### Post by gnomeuser on 2009-08-13
The new kernel certainly helps, ext4 is also faster and now the default, new toolchain (gcc, binutils, glibc) and the X stack has gotten an upgrade with important driver optimizations.

Many small things add benefits to an overall smoother computing experience.

---

### Post by jerrylamos on 2009-08-14
Not on GtkPerf on intel i830 video, intel i845 video, ati radeon Xpress 200, ati radeon mobility 7500....lately with latest PPA drivers it's taking twice as long to run GtkPerf, available from Synaptic.  On IBM Thinkpad T40 the "progress bar" crawls slowly across.

On this Compaq 3.33 gHz Celeron GtkPerf runs in 11 seconds with kms modeset=0, 27 seconds on kms modeset=1.  Oof.  kms is default on intel but not on ati.  Apparently some developers think it is the way to go since switching runs smoother, however my opinion if mainline video performance is worse it is not worth it.

For reference, jaunty takes 10 seconds.....vs. karmic modeset=0 11 seconds, modeset=1 27 seconds....straight backwards on performance.

Jerry

---

### Post by Regenweald on 2009-08-14
> **gnomeuser said:**
> The new kernel certainly helps, ext4 is also faster and now the default, new toolchain (gcc, binutils, glibc) and the X stack has gotten an upgrade with important driver optimizations.

Many small things add benefits to an overall smoother computing experience.

Sir i believe that you are wrong. It's the red bull. Trust me on this one Gnomeuser....

Edit: Serious answer though, for performance newer kernel, ext4 filesystem. For desktop responsiveness, using metacity compositing can drop memory usage cut away frills and shave off some seconds.

---

### Post by dino99 on 2009-08-14
Faster, yes it is specially with amd64, but it have to start first; that's an other story because of grub2.

---

