---
title: "Ubuntu 9.1 doesn't recognize drive on install"
date: 2010-01-29
forum: Installation &amp; Upgrades
---

### Post by tizzod on 2010-01-29
I have a WD Sata drive 200G.  When I run through the installer, it doesn't show up when I hit the partitioning part.  Not disks are listed.  What's odd though is that if I boot into Ubuntu with the CD, I can see the drive there.  I even created partition table with GParted and made an FS on it, but when I reboot and try the installer, again nothing.

I know it's the drive for sure because I have another drive that the installer does recognize.  What's screwing me up is that Ubuntu DOES in fact see the drive when I'm booted.  Can someone tell me what might be the problem?  Is there some way I can analyze this drive for some defect that might cause it to not show up, only when using the installer?

This is the same whether I use the initial boot install, or boot to ubuntu and run through the graphical install from the desktop.

---

### Post by tachuela on 2010-01-29
Disconnect the one that is seen and check if the installation sees the other one.

---

### Post by darkod on 2010-01-29
> **tizzod said:**
> I have a WD Sata drive 200G.  When I run through the installer, it doesn't show up when I hit the partitioning part.  Not disks are listed.  What's odd though is that if I boot into Ubuntu with the CD, I can see the drive there.  I even created partition table with GParted and made an FS on it, but when I reboot and try the installer, again nothing.

I know it's the drive for sure because I have another drive that the installer does recognize.  What's screwing me up is that Ubuntu DOES in fact see the drive when I'm booted.  Can someone tell me what might be the problem?  Is there some way I can analyze this drive for some defect that might cause it to not show up, only when using the installer?

This is the same whether I use the initial boot install, or boot to ubuntu and run through the graphical install from the desktop.

The most frequent reason for this is raid settings on the drive. If you are NOT running raid, try the following:
First, go into BIOS and make sure no raid settings are enabled.
Then boot again the live desktop, and depending how the disk that can't be seen is called (/dev/sda or /dev/sdb), in terminal execute:

sudo dmraid -E -r /dev/sda
sudo apt-get remove dmraid

Reboot and start the install process. It should be fine.

---

### Post by tizzod on 2010-01-29
darkod, I bet you anything that's it!  I got the HD from a friend and I remember him saying he had it in an array.  I'll take a look when I'm home next.  Thanks so much!

---

### Post by lindsay7 on 2010-01-29
sometimes the partition table gets messed up or there may have been a partition format and something stopped it.  I would start of on the live cd and go to gparted and reformat the drive in question.  See if will fix it.

---

### Post by audiomick on 2010-01-29
Darko is probably right. If you still have trouble, try using the alternate CD to install instead of the live CD. Last time I installed ( a few weeks ago) I tried the Live CD installer for the first time (had been using Ubuntu Studio perviously), and it didn't find both of my drives. I had read that the alternate CD sometimes works better, and it did for me. My drives were definitely never in a RAID array. I bought them new.

---

### Post by darkod on 2010-01-29
> **audiomick said:**
> I bought them new.

Just to mention that I've seen cases here when this was the "problem" even with new drives. Can't explain it. You buy a sealed hdd expecting that it's never been used. Maybe some testing process left something on it. Who knows...

---

### Post by audiomick on 2010-01-29
> **darkod said:**
> Just to mention that I've seen cases here when this was the "problem" even with new drives. Can't explain it. You buy a sealed hdd expecting that it's never been used. Maybe some testing process left something on it. Who knows...

Ok, good to know. Thanks Darko.

---

### Post by tizzod on 2010-01-29
ya that was it darko...   thanks so much!  Deleting that raid meta data worked like a charm

---

