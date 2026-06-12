---
title: "Wireless still not working with new kernel 2.6.24-15"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by toghraee on 2008-04-05
Hi

my Intel wireless 3945 (iwl3945) is still not working, it stopped working with 2.6.24 kernel, I tried with compact drivers but didt worked for me. 
I upgraded to kernel 2.6.24-15 but it is also doesnt work.

dmesg | grep iwl
[   38.728493] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26k
[   38.728496] iwl3945: Copyright(c) 2003-2008 Intel Corporation
[   38.729448] iwl3945: Detected Intel Wireless WiFi Link 3945BG
[   38.793236] iwl3945: Tunable channels: 13 802.11bg, 0 802.11a channels
[   38.794619] phy0: Selected rate control algorithm 'iwl-3945-rs'
[   78.499307] iwl3945: Microcode SW error detected.  Restarting 0x82000008.
[   78.499324] iwl3945: Error Reply type 0x00000005 cmd REPLY_SCAN_CMD (0x80) seq 0x4418 ser 0x0000004B
[   79.498420] iwl3945: Can't stop Rx DMA.

when I boot into 2.6.22 kerel, its working fine.
I compiled the [http://linuxwireless.org/download/compat-wireless-2.6/](http://linuxwireless.org/download/compat-wireless-2.6/), compiled, installed and loaded but no wireless network is shown and the output of dmesg is the same.


any comments ?

Regards

---

### Post by dstew on 2008-04-05
It looks like that driver will not work with that kernel. You might try the ipw3945 driver instead. Driver problems for hardware is a chronic problem with Ubuntu because hardware manufacturers do not cooperate with open-source developers to create drivers. Often, developers have to guess to make drivers. The people who work on the kernels need to make updates considering the whole universe of problems and applications, and will not often slow down to wait for a driver to catch up. Sometimes, your hardware just gets left behind.

You might consider using ndiswrapper, and Windows drivers. Ndiswrapper tends to stay up to date relative to kernels, and it might work better.

---

### Post by colddiver on 2008-04-08
Hello,

I can confirm that ndiswrapper also does not work with kernel 2.6.24-15. I have a my wireless card is a Linksys WPM11 (v. 2.7) card (based on the broadcom 4303 chipset) that works flawlessly with ndiswrapper on kernel 2.6.22 but fails to work with 2.6.24.

I have tried the HOW-TO posted here:
[http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003)

And still had no luck.

Colddiver

---

### Post by dstew on 2008-04-08
You might have to compile ndiswrapper from source. The versions packaged for and included with Ubuntu are often pretty far behind the kernels. You can get later ndiswrapper versions directly from the [ndiswrapper site]("http://ndiswrapper.sourceforge.net/joomla/").

---

### Post by colddiver on 2008-04-10
I did compile from source and I am still getting no result...

---

### Post by dstew on 2008-04-10
> I did compile from source and I am still getting no result...Using compiled ndiswrapper is pretty tricky. You have to completely remove all traces of old ndiswrapper that came with the distribution. You have to have a decent Windows driver. Usually the XP or 98 drivers work. This seems like a decent tutorial: [http://johnbokma.com/mexit/2007/12/29/installing-ndiswrapper-acer.html](http://johnbokma.com/mexit/2007/12/29/installing-ndiswrapper-acer.html).

How far did you get with ndiswrapper? Were you able to install the Windows driver into it? Please post the output of```
ndiswrapper -l
```

---

### Post by colddiver on 2008-04-13
Here is what I did...

1. I rebooted into the latest kernel (2.6.24-16 generic).
2. I followed the tutorial you suggested
3. I removed the windows driver and reinstalled it just in case

This didn't do anything. the output of ndiswrapper -l is:

lsbcmnds : driver installed
	device (14E4:4301) present (alternate driver: ssb)

I then went back to this: [http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003)

When I did modprobe ndisrwapper, the computer froze completely (wasn't even able to kill X when in X or use ctrl-c to kill the command). I tried a variation of the above and attempted to modprobe b43, b44, b43legacy and ALL resulted in the same type of freeze (I did modprobe -r everything as describe in the forum pot quoted above).

When I book back into 2.6.22-14-generic, everything works fine. The output of ndiswrapper -l under this kernel is:

lsbcmnds : driver installed
	device (14E4:4301) present (alternate driver: bcm43xx)

I also looked at this thread: [http://ubuntuforums.org/showthread.php?t=665834](http://ubuntuforums.org/showthread.php?t=665834)

This also resulted in a freeze (I wasn't able to rmmod ohci_hcd however - module wasn't present).

Any ideas?

Colddiver

---

### Post by colddiver on 2008-04-13
I also just tried the b43-fwcutter route as described here: [http://ubuntuforums.org/showthread.php?t=738216](http://ubuntuforums.org/showthread.php?t=738216)

I can't even boot (system freeze during the boot process, probably when the drivers are loaded - similar type of freeze as before)...

I am about to give up on this...

Colddiver

---

