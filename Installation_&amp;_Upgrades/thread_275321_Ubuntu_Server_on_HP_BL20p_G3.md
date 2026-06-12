---
title: "Ubuntu Server on HP BL20p G3"
date: 2006-10-11
forum: Installation &amp; Upgrades
---

### Post by vdpollm on 2006-10-11
Hi there,

I would like to use Ubuntu server, but have not been able to install it on my HP BL20p Blades.

The machine boots into the installation window. After selecting install, it hangs and goes no further.

has anyone had any luck with this? how did you do it?

regards

Marc van der Poll

---

### Post by vdpollm on 2007-10-08
Finally found out how to do it:

Boot up with the CD.

move the cursor to the selection, e.g. LAMP Server. then select the options button (i think you hit F6?)

append "debian-installer/framebuffer=false" to the end of the parameters that are already there, and press install.

---

