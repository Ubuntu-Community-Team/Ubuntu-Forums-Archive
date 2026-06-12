---
title: "New build software RAID 1+0 question..."
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by focaccio on 2010-07-11
Hello,

I'm just planning a new system that will have 4 or 5 SATA drives and I want to use RAID.  The system will be a 64bit workstation and not a webserver.  The mainboard will be an Intel DP55KG.  I'd like to use RAID 1+0 and Ubuntu.  How should I proceed? Does the Ubuntu server 10.04 ISO standard installer have an option for software RAID 1+0? What if I wanted to install the OS on one drive and add a 4 drive RAID 1+0 array after...is there a package or built-in tool to do that?  Would the 4 drive RAID 1+0 array work independently of the one drive OS?  For example, what if my one Ubuntu OS drive was in a removable bay and I put in an Ubuntu development OS drive into the bay...would the 4 drive RAID 1+0 still be available for read/write?

Thanks,
Greg

---

### Post by focaccio on 2010-07-15
My guess is that since the code to control the software RAID would be part of the operating system [therefore on the OS drive], I couldn't swap operating system drives then use the same RAID.

I think I'll be aiming for hardware RAID.  Something like an Adaptec 2405 RAID card. VMware ESX server is supported, so I could install Ubuntu inside that.

---

