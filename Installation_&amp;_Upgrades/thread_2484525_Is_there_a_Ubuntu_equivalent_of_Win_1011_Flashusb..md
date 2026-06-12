---
title: "Is there a Ubuntu equivalent of Win 10/11 Flashusb.sys?"
date: 2023-03-01
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2023-03-01
The reason for asking is that Win 11 memory integrity check flags my Dell Precision 7720 laptop as non-compliant.  On a Win 11 forum I learned that this is a not significant problem as Dell won't write a driver that fixes the problem, and my laptop works fine anyway.  I am not seeing any strange behavior with 22.10 other than I needed to install wireplumber to so a no-sound problem with the built-in audio.

Thank you,

John

---

### Post by MAFoElffen on 2023-03-02
'flashusb.sys' is part of USB driver for Flash Loader utility, written by Intel Mobile Communications. Win 11, running especially on a Dells, reports that flashusb.sys is incompatible with memory integrity. The way flashusb.sys accesses memory and interacts with Windows services probably exposes potential security holes. Intel people tell people to contact Microsoft or Dell. But Intel is the one who wrote the driver.

Linux doesn't use things like this, and if there were something like this, there are Security CVE updates included with each kernel update. Then there is this sort of partnership between Canonical and Dell where they try to work on some specific drivers for Ubuntu to work on Dell hardware.

I know that working with Dell EMC PowerEdge Servers, that Dell has had their own Ubuntu repo's for their own tool sets and drivers for their hardware, for at least about a decade now.

I am not an employee of Canonical nor Dell. I was a happy customer, who later was certified to work for a contractor doing Dell, Lenovo and HP onsite warranty service for them.

---

