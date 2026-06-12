---
title: "Installing Ubuntu on a RAID 0 array"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by C!pheR on 2006-06-15
Hi guys,

I've got 2 SATA drives that have been set up with a stripe in RAID 0 configuration through the nVidia RAID controller on my motherboard (ASUS A8N-SLI).

When I installed Ubuntu I had problem making it recognise the stripe.  It could see both disk drives individually but would not recognise the stripe.  Eventually I had to create a new stripe over 1 disk and do without RAID 0 to install Ubuntu.

Presumably I'm missing files from my Ubuntu installation to be able to communicate with my RAID controller correctly.  Although there is a software RAID configuration within the installer I would like my hardware RAID configuration back please!  Does anyone have any idea which files I need to download, and how they should be incorporated into the installation to get RAID 0 to work please?  Any help is greatly apprecaited!

---

