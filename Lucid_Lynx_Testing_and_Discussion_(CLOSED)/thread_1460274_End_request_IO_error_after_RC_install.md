---
title: "End_request: I/O error after RC install"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Odisej on 2010-04-22
Ok, I am not sure whether to report this as a bug or not. I installed Lucid just now and after installation was completed and CD ejected instead of rebooting the screen was filled with the following error:

end_request: I/O error, dev sr0, sector 497136 

The number at the end varies.

Bug or not a bug? To report or not to report? 

The system seems to be working just fine after forceful reboot.

Regards,

Odisej

---

### Post by cariboo on 2010-04-22
/dev/sr0 is your cdrom drive.

---

### Post by jfernyhough on 2010-04-22
Perhaps a badly burned CD?

If the install process completed the installed copy will be fine; next time just burn at a lower speed. Or use a USB stick for maximum speed!

---

### Post by schmickey on 2010-04-22
> **jfernyhough said:**
> Perhaps a badly burned CD?

If the install process completed the installed copy will be fine; next time just burn at a lower speed. Or use a USB stick for maximum speed!

I too got an I/O error but mine was during the install/copy phase.  I can't get beyond 56% on the progress bar.  Keep getting I/O error.  I tried 2 different downloads of 10.04 (one via bittorrent, another a straight D/L via a mirror site) and two different flash drives to do the install from (my laptop has no optical drive).  I've never had problems with this method in the past. 9.10 installed this way just fine.

I shrunk my Win7 partition and left about 100GB unallocated space on a 500GB hard drive and told it to use the available free space.  I've done it this way with half a dozen previous releases with no problem.  The Windows 7 installation is working fine, so I don't think I have a hardware problem.

---

### Post by flipper9 on 2010-04-23
I got the same error after installing a fresh copy of the RC via USB key.

---

### Post by powder on 2010-04-23
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/539027](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/539027)

---

