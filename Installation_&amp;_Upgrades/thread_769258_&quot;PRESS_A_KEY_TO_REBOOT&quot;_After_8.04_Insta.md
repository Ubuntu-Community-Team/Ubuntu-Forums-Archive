---
title: "&quot;PRESS A KEY TO REBOOT&quot; After 8.04 Install"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by theh3brewhammer on 2008-04-26
I have a spare computer that I wanted to try out Ubuntu 8.04 with.  There are two hard-drives, a 120GB drive and a 250GB drive.  

The Ubuntu install CD defaults to use the free space on the 250GB drive, but I told it to use the entire 120GB disk.  After the installation, when I reboot I can't get past a black screen that says "PRESS A KEY TO REBOOT" in white text.

I definitely removed the install CD and even set the BIOS to only boot from the 120GB drive.  Also, I've tried reinstalling onto the entire 120GB disk a couple more times (with no change).

Thanks for your help!

---

### Post by lithiumX on 2008-06-11
Change your BIOS to boot into the original drive and it should ask you which OS you want to boot. I am by no means an expert, but I tried it and it worked for me. Cheers!

---

### Post by theh3brewhammer on 2008-06-11
I ended up using trial and error to properly modify the grub.conf file.  Thanks anyways for the tip.

---

