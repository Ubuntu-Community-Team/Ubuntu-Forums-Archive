---
title: "Grub first error 15, now 22"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by SSamiK on 2009-11-15
After running 9.10 for a while after updating from 9.04 I wanted to do a clean install to get rid of a couple of hickups. 
The install finishes without any problems, but upon reboot I got Grub error 15, this happend a couple of times so I went on to format all my HDD's to get rid of every little bit of old installs. This in turn caused a Grub error 22... Now I'm in the dark here.. This seems like Grub legacy, but from where does it come? As earlier stated, I have formatted all disks, not only formatted, but deleted all partitions and made new ones.. So, where do I go from here?

---

### Post by SSamiK on 2009-11-15
ah... after som fiddeling around I got it working. First off I used fdisk to emty out my MBR
```
fdisk /mbr
```
And deleted all my partitions once more (probably not necessary, but hey...) Reinstalled once more, and still no luck. 
Now I had no grub errors, but anther message; somethung about no partition or no bootable partition. No worries, I stated up with a livecd and chrootet into my install and did a grub-install as described here: [https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2]("https://help.ubuntu.com/community/Grub2#Reinstalling GRUB 2") And hey presto, I'm back in a freshly installed Karmic. 

The last step would probably have fixed the problem to start with, but I had to go the long way around till I realized what to do.

---

