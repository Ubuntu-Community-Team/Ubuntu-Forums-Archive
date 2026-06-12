---
title: "No network after installing via live desktop over nfsshare"
date: 2011-05-10
forum: Installation &amp; Upgrades
---

### Post by Mentski on 2011-05-10
I've recently been attempting to "upgrade" our workshop to a diskless solution for installing operating systems (we refurbish a lot of old, donated machines of varying specs), We've currently got a server, running PXELINUX with the choice of running ubuntu live desktop CD 10.10 or 11.04 via an nfs share.

Both appear to load, operate, and install Ubuntu fine(whilst obviously being connected to the network), yet on reboot after installing to the hard drive, the installed copy won't detect the network card. 

If we install via a physical CD, the network card is detected after reboot, and everything works as it should.

I'm pretty sure this isn't a hardware issue, as I stated earlier, we go through a lot of machines with varying hardware loadouts, and this appears to happen every time right now.

Am I missing something really obvious here, or have I hit upon some kind of bizarre quirk in the installation procedure?

---

