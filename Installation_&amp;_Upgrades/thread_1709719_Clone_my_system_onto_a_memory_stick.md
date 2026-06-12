---
title: "Clone my system onto a memory stick"
date: 2011-03-18
forum: Installation &amp; Upgrades
---

### Post by pwabrahams on 2011-03-18
I'd like to clone my running system onto a memory stick, to gain the benefits of updates, customizations, and additional programs I've installed.  I see two difficulties with just using dd:

1. I have to get a snapshot of the system, since otherwise it will be changing as I do the operation.  That I can do  using a system in another partition.

2. The system probably has embedded references to /dev/sda or to the disk ID of the hard drive, which probably would not work when I'm running from the memory stick.

Ideas?

---

### Post by Joe of loath on 2011-03-18
Use remastersys to build an ISO image of your install, then use the built in USB installer to install that to a USB stick.

---

### Post by wandalalakers on 2011-03-18
If you have a Nvidia or ATI card and you use their driver, you will have to reinstall it after imaging/cloning.  Whenever I make a copy of my pc and use Remastersys. I have to reinstall Nvidia's driver.  My opengl screensavers work better with Nvidia's drivers.

---

