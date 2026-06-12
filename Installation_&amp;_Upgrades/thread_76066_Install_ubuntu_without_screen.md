---
title: "Install ubuntu without screen?"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by ManLord on 2005-10-14
Is it possible to install ubuntu/kubuntu without a screen, and enable it for VNC?

Is there some sort of VNC that runs off CD, and in bios? So that I can control the installation from my other PC (Laptop)

---

### Post by swerner on 2005-10-14
There is a method that allows a user to do an OEM install for Breezy, I don't know what is required in the configuration though.

Otherwise rip out the HDD, connect via USB or somehow else to your laptop, copy your existing setup directly on the HDD, including partition layout (this will be important for your '/' and '/boot' mounts).  Configure the network.  Make it bootable.  TADA! you have a bootable linux system that you can boot to.

---

