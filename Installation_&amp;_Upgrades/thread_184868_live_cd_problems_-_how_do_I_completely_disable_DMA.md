---
title: "live cd problems - how do I completely disable DMA?"
date: 2006-05-30
forum: Installation &amp; Upgrades
---

### Post by wasteed on 2006-05-30
I'm having problems getting the live CD (now called the 6.06 RC desktop CD) to boot  properly. To get it past the inital boot stage I have to specify "ide=nodma" on the boot line. This will get it to the start of the squashfs stage but then  I start receiving "hdc driveseek"  and "operation not supported" errors.  I had a similar problem with the Dapper beta2 live and install CDs  last month, but found I could get around this with the install CD by going into expert mode and using a hdparm command line option to disable DMA once the 2nd boot stage had started. However this choice isn't available with the live CD. So the question is, is there another way of completely disabling DMA for my CD drive when booting the live CD?

Btw,  I know the CD-Rom still works properly as I have an old Mepis CD (2003-10) lying around and this boots into a live system just fine. I also know the CD media is OK too, as it works in another computer.

---

