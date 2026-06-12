---
title: "Which updates to do for Ubuntu 12.10"
date: 2014-01-03
forum: Installation &amp; Upgrades
---

### Post by hirumabiff14 on 2014-01-03
Hi, i have posted on here before about problems regarding internet connection. Which i managed to resolve using wireless connection, than managed to get wired connection. After doing updates on ubuntu 13.04 i have had many issues,  form not having any internet connection at all, locked out of my account etc etc. I decided to put the live cd for 13.04 in and ran it, and i was connected to internet, so i did fresh install without updates. I had internet access :-) i then proceeded to do updates, and then i had no connection. I have read many threads here, and to be honest although i may be a newbie, i am not totally stupid!! no comment required thanks! :-) the more i read the more my brain get fried, and the more lost i seem to get. Thought right nothing to lose, so i downloaded Ubuntu 12.10 live burned to disc, rebooted from disc and i was online first with wireless then wired, tho when both were connected i seemed to have an issue, which i have asked about in networking forum. Since i managed to connect to internet i decided to install 12.10. Internet worked fine. I did software updates, and surprise surprise not!! no internet connection. I re-installed 12.10 again, have now made a backup of this. I wanted to know which updates i can do to be sure it don't all go pear shaped again. I have dabbled with Vmware player before, and i will probably try setting up that and install ubuntu or something on it and work from there till i know i can update my main installation without too much grief. Sorry if this seems like a novel, but just wanted to give you full picture. 

Many Thanks 

Dave

---

### Post by ian-weisser on 2014-01-03
A VM install won't tell you if hardware is compatible. The guest does not see much of the hardware.
If you have hardware problems, then watch for kernel updates. The kernel handles hardware compatibility.

I don't quite understand why you want to do all that uninstalling and reinstalling foolishness. Juggling different kernel versions to test (and fallback) hardware compatibility is something GRUB has done very well for many years. All you need to do is expose your GRUB choice screen at boot, and remember which of the listed kernels is the one that works. If a new kernel doesn't work, then reboot into an older kernel, and uninstall the non-working kernel. That's what your package manager is for.

---

### Post by hirumabiff14 on 2014-01-04
> **ian-weisser said:**
> A VM install won't tell you if hardware is compatible. The guest does not see much of the hardware.
If you have hardware problems, then watch for kernel updates. The kernel handles hardware compatibility.

I don't quite understand why you want to do all that uninstalling and reinstalling foolishness. Juggling different kernel versions to test (and fallback) hardware compatibility is something GRUB has done very well for many years. All you need to do is expose your GRUB choice screen at boot, and remember which of the listed kernels is the one that works. If a new kernel doesn't work, then reboot into an older kernel, and uninstall the non-working kernel. That's what your package manager is for.



Ok thanks for that advice. I read so much different threads and things got worse. Re-install was my quickest and easiest option. Ill know in future what to look for if i update and have issues. Ill just need to look into exposing GRUb choice during boot.

Thanks again.

Dave

---

