---
title: "Intrepid update disabled my e1000 adapter?"
date: 2008-09-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by aussiebuddha on 2008-09-26
Hi.

I just updated intrepid to the latest kernel and it seems to have disabled my e1000 intel gigabit adapter.
I did some googling but found no way to get it back to work.
can you guys please help me? I have no wifi either, so i'm desperate to get ubuntu working again.

I'm posting this from my windows install :-(

---

### Post by Ayuthia on 2008-09-27
I think that they disabled the adapter because there is talk that the driver might hurt the hardware.  If that is really the case, you might not want to try to enable it quite yet.

Here is the link that talks about it:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555)

---

### Post by aussiebuddha on 2008-09-27
WOW. that is a monster sized bug!
madagascar cockroach sized.

better forget about reinstating the e1000 driver for the time being.

I might look for help getting my wifi to work properly so i don't need my LAN adapter until they fix it.

this is what i hate from linux...

Sorry i'm just really dissapointed with linux lately LAN/WIFI/VIDEO problems not only on beta versions but on final versions as well.

this is what scares people from linux, and gets them to stay on windows.

:-(

---

### Post by drunken_sapo on 2008-10-26
Any ides about when will this be corrected?
Thanks in advance guys!

---

### Post by dinxter on 2008-10-26
the new kernel has fixed this bug, the e1000 module should not be blacklisted anymore on an updated installation

---

### Post by drunken_sapo on 2008-10-26
> **dinxter said:**
> the new kernel has fixed this bug, the e1000 module should not be blacklisted anymore on an updated installation

However, i still get no ethernet interface. I think I have the latest kernel available:

Linux laia 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

e1000 module is not blacklisted. the only things blacklisted in /etc/modprobe.d/blacklist are:

# replaced by e100
blacklist eepro100
blacklist e1000e


When I try to load the e1000 module, it loads but i dont get any interface and no error messages:

>>modprobe -v e1000
insmod /lib/modules/2.6.27-7-generic/kernel/drivers/net/e1000/e1000.ko

>>tail -f /var/log/messages

Oct 26 08:44:59 laia kernel: [ 2028.910825] Intel(R) PRO/1000 Network Driver - version 7.3.20-k3-NAPI
Oct 26 08:44:59 laia kernel: [ 2028.910839] Copyright (c) 1999-2006 Intel Corporation


And that's all folks. I'm not sure what to do next since I don't get any clues.

Thanks in advance for your help.
Best regards.

---

