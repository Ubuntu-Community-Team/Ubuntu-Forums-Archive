---
title: "modprobe Error on Boot after Upgrade"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by arrow203 on 2011-04-29
Good morning,
 
I did an in place upgrade of 10.10 to 11.04 last night. Upgrade seemed to proceed without problems.
 
Now on boot, the system hangs with the following error:
 
udevd-work[90]: '/sbin/modprobe -bv pci:v000010DEd000001D7sv00001179sd0000FF31bc03sc00i00' unexpected exit with status 0x0009
 
Any advice would be appreciated. modprobe would seem to indicate a driver or kernel issue to me. I'm rather new to Linux, so my apologies ahead of time.
 
Thanks,

---

### Post by ranbo on 2011-04-29
I don't know the answer, but I downloaded 11.04 64-bit desktop .iso file and burned it to a CD.  When I boot from the CD, I get the same error:

  udev-work[90]: '/sbin/modprobe -bv pci:......'
  unexpected exit with status 0x0009.

(Trying to upgrade via update manager just didn't work for me).

Lenovo Thinkpad T500, 4GB RAM.

---

### Post by arrow203 on 2011-04-29
Appears to be a kernel issue for me.

If I allow it to boot automatically, it hangs.  Upon restarting, I'm prompted with the grub selection list.  If I choose previous versions, and load the version listed there, it seems to boot without problems.

The default selection is 2.6.38-8-generic, and the previous versions (the one that works) selection is 2.6.35-27-generic.

Anyone?

---

### Post by zlf341 on 2011-04-30
I have same issue on my Lenovo W500, which has switchable video card (means two video card). I tried to set it to a single video card, it was working for a while and failed again.
 
any solution?
 
 
Jerry Zhang

---

### Post by arrow203 on 2011-04-30
For me, it ended up being a problem with nouveau Nvidia nouveau driver.  I'm not sure if it was updated for 11.04, but it caused my system to hang on boot.  The old 10.10 kernel booted fine, and I was able to update the driver to the proprietary Nvidia driver.  New 11.04 kernel boots fine now.

---

