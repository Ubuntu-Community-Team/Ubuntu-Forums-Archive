---
title: "[SOLVED] After Kernel Upgrade: External USB Harddisk -&amp;gt; Poor Performance"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by wieman01 on 2006-11-04
Hi, 

I have done a kernel upgrade this morning (2.6.15-27) & everything worked fine after I had done so with one exception: 

My external USB harddisk (Buffalo 300GB) would stop transferring data at the used speed (~20 MB/sec) but the transfer rate would drop below 2 MB/sec. I am suspecting that this has to do with system recognizing it as a USB 1.1 device rather than 2.0. **"lshw"** & **"lsusb"** look fine though, so does **"/var/log/auth.log"**.

The log says something about "usb 4-4: new high speed USB device using..." but it did not suggest that there is a performance issue.


Anybody with the same issues and a possible solution?

_**EDIT:**_
I have reversed all updates...

---

### Post by wieman01 on 2006-11-04
Anyone?

---

### Post by wieman01 on 2006-11-05
Last try...

---

### Post by wieman01 on 2008-01-25
I know it's an old thread, but just to close it... Upgrading to Gutsy eventually did the trick.

---

