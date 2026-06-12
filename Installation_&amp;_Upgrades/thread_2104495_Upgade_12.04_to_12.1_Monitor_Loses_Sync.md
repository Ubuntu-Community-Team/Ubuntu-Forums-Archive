---
title: "Upgade 12.04 to 12.1 Monitor Loses Sync"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by ve3pkc on 2013-01-13
I recently upgraded my Ubuntu 12.04 to 12.1. When I rebooted into Ubuntu the monitor completely lost sync, so I had to shut the pc down. I made an installation DVD and tried to boot from it and possibly reinstall, but the same thing happened with the monitor. I had no problem with 12.04 and previous Ubuntu versions. My monitor is an older Viewsonic VPA150. In Windows 7 my monitor driver is "generic non-pnp". Any ideas how I can change the driver and be able to see what is going on??
Regards
J.Clark

---

### Post by dino99 on 2013-01-13
with recent kernels, X is directly drived without needing xorg.conf
then all depend on the graphic driver used.

---

### Post by ve3pkc on 2013-01-13
Thanks d99. I was able to use Grub2, advanced ubuntu features, 3.2.0-35-generic-pae to boot up vs the 3.5.0-21-generic. The system features show for graphics "unknown". My computer is an hp p6102f using nVidiaGeForce9100 video. How do I install the correct driver for this. There was a post for using Jockey...is this the way to go?
Regards

---

### Post by NM5TF on 2013-01-13
> **ve3pkc said:**
> Thanks d99. I was able to use Grub2, advanced ubuntu features, 3.2.0-35-generic-pae to boot up vs the 3.5.0-21-generic. The system features show for graphics "unknown". My computer is an hp p6102f using nVidiaGeForce9100 video. How do I install the correct driver for this. There was a post for using Jockey...is this the way to go?
Regards

if everything is working correctly, then don't worry too much about
the "unknown" graphics message...I have the same message about my Nvidia
card but it works perfectly...

in the hardware field we have an old saying  "if it ain't broke, then
don't "fix" it..." this applies to software as well....

Tommy

---

### Post by ve3pkc on 2013-01-15
Thanks Tommy:
I just removed the 3.5.0-21 kernel and headers, then updated the Grub loader and everything is working well. I think next time I will test using a USB stick to make sure everything works before I upgrade. I tested both my hp p6102f pavilion desktop and hp envy 4 laptop with both 12.04 and 12.1 on usb stick. Both had almost black screens out of sync. The hp envy has a complicated partitioning scheme, so I am going to try Ubuntu in a virtual machine either VirtualBox or VmWare.
Regards
J.Clark

---

