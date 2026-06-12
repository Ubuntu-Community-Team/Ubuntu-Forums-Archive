---
title: "Raid 1 install and clarification"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by knottshawk on 2009-12-10
I have a computer which I plan to setup for RAID 1 (hardware setup...in the bios).. once that is complete, do I just step through a normal Ubuntu 9.04 desktop install?

Thanks...

---

### Post by darkod on 2009-12-10
I haven't installed on raid myself, but according to ubuntu you need to use the alternate install cd/image, not standard desktop (liveCD) image.

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:
  
[LIST]
[*]setting up automated deployments;
[*]upgrading from older installations without network access;
[*]LVM and/or RAID partitioning;
[*]installs on systems with less than about 256MB of RAM (although note that low-memory systems may not be able to run a full desktop environment reasonably).
[/LIST]
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

Note: the installer is text based. You will still end up with GUI system. Watch out if you need to select GUI desktop during installation, not sure if it's default.

---

### Post by knottshawk on 2009-12-10
Yeah... I thought that might be for software RAID... the instructions for all of it is, um, not exactly clear.

---

### Post by darkod on 2009-12-10
> **knottshawk said:**
> Yeah... I thought that might be for software RAID... the instructions for all of it is, um, not exactly clear.

I think it's to be able to see the raid at all. I guess no drivers in desktop cd.

---

