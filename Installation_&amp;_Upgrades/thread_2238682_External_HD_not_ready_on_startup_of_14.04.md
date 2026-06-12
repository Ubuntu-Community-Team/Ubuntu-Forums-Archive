---
title: "External HD not ready on startup of 14.04"
date: 2014-08-09
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2014-08-09
I have a USB3 connected external HD. Often i have to wait a long time before it is recognised as being ready. Sometimes it does not go beyond waiting. Are there any grub settings I can change to improve the recognision of the external HD?

R

---

### Post by ajgreeny on 2014-08-09
If you want it to mount to the same place/folder every time you boot you can add a line to /etc/fstab

See [http://ubuntuforums.org/showthread.php?t=2148264](http://ubuntuforums.org/showthread.php?t=2148264) for a similar mount query.

---

### Post by Robbyx on 2014-08-10
Turning off fsck seems to have stopped the startup time lag:

Following your suggestion I checked out the other changes and this article seems relevant: 

[http://linux.koolsolutions.com/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/](http://linux.koolsolutions.com/2009/01/30/installing-linux-on-usb-part-4-noatime-and-relatime-mount-options/)

Those  options seem to be dealing with the same operation,  so I made a further change to your proposal and  decided to keep  relatime  but remove noatime. Is that a fair compromise?

---

