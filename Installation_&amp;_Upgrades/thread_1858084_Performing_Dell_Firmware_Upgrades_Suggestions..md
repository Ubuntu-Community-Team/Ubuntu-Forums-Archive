---
title: "Performing Dell Firmware Upgrades: Suggestions."
date: 2011-10-11
forum: Installation &amp; Upgrades
---

### Post by Larry Mateo on 2011-10-11
I work primarily with Dell servers, currently PowerEdge 1900 and PowerEdge 1950 systems. Dell provides firmware upgrade packages for various versions of Red Hat Enterprise Linux and SuSE ES Linux only; none for Ubuntu Linux.

I have been unsuccessful in getting these packages to work properly on a Ubuntu server running Lucid. I'm going to try using a Red Hat Fedora Live boot CD and installing the Red Hat package that way.

I'm just wondering if others have been successful in updating PE 1900 or PE 1950 firmware on servers running Ubuntu, and, if so, how?

Thanks much.

---

### Post by sillejo on 2013-01-27
I could not boot to 12.04 but I was able to boot my PE 1900 to v. 10.04 and install that via DVD from the download ISO.

---

### Post by Cheesemill on 2013-01-27
If they provide a DOS program for flashing your firmware then you can use that.

Use Unetbootin to create a FreeDOS bootable USB drive and copy the flashing software and files onto it, you can then boot into DOS from the USB stick and flash the BIOS from there.

---

### Post by sillejo on 2013-01-27
I misunderstood the original post. I thought it was the OS you couldn't update. I missed the BIOS part.

But, with that out of the way, any idea why my OS upgrade on the PE 1900 knocked out the video?  The upgrade from 10.04.4 to 12.04 got to the reboot step and after I got an Ubuntu splash screen then the monitor went black (it has a timeout when no signal is detected.  The VGA signal stopped so it shut down).

Any thoughts?

---

