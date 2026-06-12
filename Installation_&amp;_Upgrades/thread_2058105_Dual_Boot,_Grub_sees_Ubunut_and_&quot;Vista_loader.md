---
title: "Dual Boot, Grub sees Ubunut and &quot;Vista loader (recovery)&quot;, but not XP partition"
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by dukebob on 2012-09-14
OK, I have read for days and have tried many different ways, including reinstalling xp, then ubuntu a second time.

After I finish my Ubuntu install, grub runs at boot like it is supposed to.

Only grub displays Ubuntu, Ubuntu repair, memtest, and Vista recovery.

I have installed XP over the Vista partition, leaving the recovery partition alone for now.  Then installed Ubuntu side by side.  I did notice that when I select side by side, the ubuntu installation says "Vista Loader is already installed"  (That is correct because that goes to the recovery partition?)  But why doesn't it see my XP partition?


I can see each partition in Disk Utility
sda1 says extended on top, below it shows it is broken into these partitions: sda5-ntfs windows, sda 6-ext4 ubuntu, sda7-swap

Anyone know what I am missing or point me in the right direction in materials???
Thanks in advance!

---

### Post by oldfred on 2012-09-14
Windows has to be in a primary or sda1 thru sda4 partition. If your Windows is in sda5 that is a logical. A second install of Windows only boots from a logical thru anther install in a primary.

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

