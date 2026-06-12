---
title: "How to install the third OS on Ubuntu 11.04"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by shinokada on 2012-11-01
I run Ubuntu 11.04 and Windows 7(Norwegian) on a Dell  Latitude. Now I would like to install Windows 7 (Japanese). I googled to  find how to install the third OS on Ubuntu, but not able to find one.
  Could anyone tell me how to do or website explaining how to do it?
  Thanks in advance.

---

### Post by rcsheets on 2012-11-01
I realize this is not a direct answer to your question, but it may be worth mentioning that if you upgrade Windows 7 to Ultimate, you'll be able to install multiple localizations at once. I only mention this because it might prevent you having to install two entirely separate instances of Windows on the same system.

---

### Post by oldfred on 2012-11-01
Normal Windows dual boot will install a second copy to any partition that is NTFS, but all the boot files get moved/combined with the install in a primary NTFS partition with the boot flag. Windows then updates the BCD in the boot partition to show both Windows.

Better to have both Windows in primary partitions. Link below is mostly Vista but 7 is the same as Vista.

To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

