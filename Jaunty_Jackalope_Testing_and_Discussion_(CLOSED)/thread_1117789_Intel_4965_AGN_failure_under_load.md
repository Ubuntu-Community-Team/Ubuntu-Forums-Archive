---
title: "Intel 4965 AGN failure under load"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by chrisdeckard on 2009-04-06
I installed the Jaunty beta on Friday night and have been loving it ever since.  A few little bugs, but so far this has been a great release.

I've encountered an error with the Intel wireless 4965 AGN card while under high load.  I have a fairly large home directory, around 97 GB, two files which are virtual machine images are 30GB each.  When restoring my home directory over wireless, the wireless card would encounter an error and stop transmitting data.  Network Manager appears to show that it is connected to the network, but not until I disable wireless and reenable it does it come back.  The failure of course interrupts the restore process.

I've see these messages in the logs when this happens:

[116045.190862] iwlagn: Microcode SW error detected.  Restarting 0x2000000.
[116045.207821] iwlagn: MAC is in deep sleep!

I don't have enough information yet to file a bug report on it, but wanted to make it known and see if others are experiencing the problem.

Running Ubuntu Jaunty Beta 64-bit, current with all updates, Lenovo R61 laptop with Intel 4965 AGN Kedron wireless card.

-Chris

---

