---
title: "Kernel Version"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by thegasgranny on 2011-06-17
Hello,

I'm running 10.4 (down graded - long story) 

I was wondering if I could run the newer kernel than the stock 10.4 one i.e. 2.6.39.1

Cheers.

TGG.

---

### Post by Sef on 2011-06-17
You could update the kernel, but if you do, then things might break. 

Questions:

1) Do you have a disk around, so you can reinstall if the OS breaks? 

2) Have you backed up your data to a separate drive, so you do not lose all of your data? 

3) Is it ok to have that computer down for a bit?

---

### Post by ajgreeny on 2011-06-17
I was using the kernels available in the ubuntu kernel ppa in 10.04 for some time without too many problems. But the real difficulty I had was a severe degradation of USB transfer speeds, eg using the usb startup disk creator normally takes about 2 -3 minutes to make a ubuntu startup usb, but with the 2.6.37 or 2.6.38 kernels it took nearly an hour.  Similarly using rsync or grsync to backup /home was just about impossible; it took for ever to do very little.

By accident I found that speeds were normal with the standard 2.6.32 kernel, and also the one from the "proposed" repos, 2.6.35, which is what I am now using.

Try the even newer kernels, by all means, but look very carefully at all system operations after installing as some things may be broken, or as in my case, simply not work quite as well as they should.

---

