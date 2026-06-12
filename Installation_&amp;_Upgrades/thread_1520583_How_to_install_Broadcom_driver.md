---
title: "How to install Broadcom driver?"
date: 2010-06-29
forum: Installation &amp; Upgrades
---

### Post by Synyster06Gates on 2010-06-29
Never done this before on a Linux based OS. How do I install this on Ubuntu 10.04?

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

---

### Post by davidmohammed on 2010-06-29
most of the time, you dont need to.  Connect your PC via the wired connection to the internet.  Make sure the connection is ok (you can browse to google.com etc).  Then go to Administration, Hardware drivers.  Hopefully you'll see a broadcom driver to activate.

---

### Post by Synyster06Gates on 2010-06-29
I tried, but it still will not connect to the internet. See my other thread at

[http://ubuntuforums.org/showthread.php?t=1519134](http://ubuntuforums.org/showthread.php?t=1519134)

---

### Post by davidmohammed on 2010-06-30
you shouldn't double post... it will upset the forum moderators.


are there any hardware drivers available in the said window?

I presume you can connect to the internet via the wired connection? - if you can't you most probably got a router issue that you need to sort out first.

Assuming you can connect via a wired connection

please type 

dmesg

and post the contents here within code tags - 

the output should indicate what broadcom device is trying to be loaded and any errors.

Possibly if it says "firmware cannot be loaded" - suggest use synaptic manager and search for "firmware" - install the two packages found. Reboot and confirm via dmesg that the firmware has been loaded correctly.

---

### Post by Synyster06Gates on 2010-06-30
This is weird, I literally did NOTHING aside from plug it in to the ethernet wire, and it found all wireless connections. The second the plug went in, it found my home wireless connection. It seems to be working now, though.

---

