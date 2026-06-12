---
title: "Problems installing ubuntu-desktop"
date: 2007-02-20
forum: Installation &amp; Upgrades
---

### Post by Riku67 on 2007-02-20
First of all, hi to everyone. This is my first post here.

I have installed Ubuntu 6.10 server with the LAMP option onto an HP pavillion a1200 pc.

This appeared to work without any problems, and I can connect to apache from another PC.

When it boots it displays the following message, which may be the route of the problem?

 [42949376.600000] PCI: Cannot allocate resource region 3 of device 0000:00:00.0

I can run "sudo apt-get update" and it updates fine, but if I try and install any packages,
it always hangs at some point in downloading. I have a nVidia Quadro PCI-E card as well
as the onboard graphics card, but it seems to make no difference if that is in or out.

I tried installing 6.10 Desktop, but it hangs as well.

I have windows installed on another hard drive, if there is anything I can check from windows.

Any thoughts?

Cheers,

Richard.

---

### Post by taurus on 2007-02-20
Which device your monitor is connected to right now?  If it connects to the PCI card, then I recommend you go into the BIOS and turn off the onboard graphic card.  See if that helps.

---

### Post by Riku67 on 2007-02-20
> **taurus said:**
> Which device your monitor is connected to right now?  If it connects to the PCI card, then I recommend you go into the BIOS and turn off the onboard graphic card.  See if that helps.

Currently connected to PCI-E card, but the behavior is the same if I use the onboard card, with or without the PCI-E card installed.
Unfortunately the bios settings only allow setting the primary display between onboard or the PCI-E card, not actually disabling the onboard card.

---

### Post by taurus on 2007-02-20
So you still get the same message even if you remove the PCI graphic card!  Maybe it's time to update your BIOS.

---

