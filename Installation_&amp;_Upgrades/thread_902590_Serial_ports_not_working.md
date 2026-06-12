---
title: "Serial ports not working"
date: 2008-08-27
forum: Installation &amp; Upgrades
---

### Post by jhansonxi on 2008-08-27
(Continuation of an **[archived thread]("http://ubuntuforums.org/showthread.php?t=504492")**)

I filed **[bug #255200]("https://bugs.launchpad.net/ubuntu/+source/udev/+bug/255200")** and a udev patch to correct the permissions problem.  The patch is a permanent workaround and merely implements what everyone else suggested.  The maintainers have questions about the need for the udev change and the behavior of the serial applications (cu, kermit, and minicom), and why dialout group permissions are not adequate.

It would be helpful if someone with programming skill could assist them in identifying the reason for the problem in the applications and why they behave that way in the first place.

---

