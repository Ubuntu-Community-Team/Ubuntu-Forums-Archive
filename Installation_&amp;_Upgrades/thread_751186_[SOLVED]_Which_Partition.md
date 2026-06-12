---
title: "[SOLVED] Which Partition ?"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by hobo on 2008-04-10
I have a USB drive partitioned with both KDE 7.10 and Hardy 8.04 installed. I am about to install KDE4 8.04 over the existing KDE partition. How do I determine which partition the old KDE image resides from the LIVE install CD? Yes., I want to overwrite KDE 7.04 not Hardy 8.04 .

---

### Post by Gauvenator on 2008-04-10
Maybe try sudo fdisk -l to find your root partion, then logically the other partition would be the OS you're not currently in.

Try it, but I'm not sure it applys to usb disks.

---

### Post by hobo on 2008-04-10
Thanks for the reply. I did figure it out on my own by looking at the sizes etc. 
tks again!

---

