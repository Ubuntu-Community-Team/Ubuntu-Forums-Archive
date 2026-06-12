---
title: "how to transfer a hard drive w/ an existing Ubuntu installation into a new computer?"
date: 2005-06-29
forum: Installation &amp; Upgrades
---

### Post by Zed on 2005-06-29
Hi all,

I rebuilt a computer, and put into it the hard drive with a Hoary installation that was running on the old machine. The only other survivors of the old machine to keep the hard drive company are the video card and monitor -- there's a new motherboard, CPU and wireless NIC.

To no great surprise, the Hoary installation balks at all this new hardware. It won't even start X (but it does boot and I can login at the console.)

Is there any automated way to detect new hardware -- do I have any other choices besides:

1) edit conf files by hand
2) re-install from scratch

?

Thanks.

---

### Post by Krank on 2005-06-29
"sudo dpkg-reconfigure xserver-xorg" shopuld do it, provided you actually get a prompt...


dpkg-reconfigure SHOULD be able to solve almost any such problem, provided you know what packages to run it on...

---

### Post by Zed on 2005-06-30
Thanks, Krank -- that worked great for X.

The old wireless NIC was a D-Link DWL-650+ that was auto-recognized. 

Does anyone know if I have to do anything to make Ubuntu forget about it before I work on building ndiswrapper for my new Linksys card?

---

