---
title: "Can I Download Updates Prior to Reinstallation?"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by vgrisham on 2008-01-18
I just got a new hard drive, and I'm about to reinstall Gutsy on my desktop. I have the official Gutsy CD. I'm wondering if there is a way to download all of the updates that have been released prior to reinstallation. After reinstalling, it would be great to just pop in an update CD and install the updates.

---

### Post by smartboyathome on 2008-01-18
I don't think there is. I think you might be able to download the updates while the livecd is running before the installation, but that would take the same amount of time as running it after (or probably more).

---

### Post by zvacet on 2008-01-19
Maybe [this](http://www.psychocats.net/ubuntu/partimage) can help you.

---

### Post by Partyboi2 on 2008-01-19
Copy your /var/cache/apt/archives onto a usb stick or cd. Reinstall Gusty and replace /var/cache/apt/archives with the one that you copied.
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
[http://ubuntuforums.org/showthread.php?t=588766](http://ubuntuforums.org/showthread.php?t=588766)

Or like what was suggested, clone ubuntu to the new drive.

---

