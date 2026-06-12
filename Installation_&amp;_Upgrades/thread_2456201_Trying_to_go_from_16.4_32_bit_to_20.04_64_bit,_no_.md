---
title: "Trying to go from 16.4 32 bit to 20.04 64 bit, no boot from usb"
date: 2021-01-06
forum: Installation &amp; Upgrades
---

### Post by ulrichmuc on 2021-01-06
I have Ubuntu 16.04 running on an Eee PC but want to upgrade to 20.04.
So I downloaded (on another host)  ubuntu-mate-20.04.1-amd64.iso and wrote it via Startup Disk Creator to a 32 GByte USB stick.
On the Eee PC I changed the boot priority to Removable Device and tried to boot.
I see some activity on the USB-sticks led, but the computer boots from the hard disk.
I tried different USB ports, without success.

Any ideas?

---

### Post by CelticWarrior on 2021-01-06
Isn't the Eee PC 32-bit hardware? If so it won't boot a 64-bit installer.

---

### Post by crip720 on 2021-01-06
If it is a 32 bit only machine, you can only upgrade to 18.04.  The last 32bit Ubuntu version still supported.  20.04 only works on 64 bit CPUs.  Will have to find another Linux after support for 18.04 stops.

---

### Post by GhX6GZMB on 2021-01-06
Wikipedia says 64-bit, but who knows?

---

### Post by Autodave on 2021-01-06
Both of the ones that I had were 32 bit.

---

### Post by #&amp;thj^% on 2021-01-06
> **Autodave said:**
> Both of the ones that I had were 32 bit.
+1
Also in the title of the OP's thread "16.4** 32 bit **to 20.04 **64 bit**"
I remember even Lubuntu 18.04 ran applications very poorly on these machines. (Browsers and some GUI's would take it to it's knee's)
Eee PC models have typically used netbook specific processors or ultra-low voltage versions of mainstream processors. The earliest Eee PC models used a 900 MHz Intel Celeron M processor underclocked to 630 MHz. Later models shipped with Intel Atom and AMD Fusion processors.

---

### Post by ulrichmuc on 2021-01-07
lscpu says:   
Architecture: x86_64
CPU op-mode(s): 32 bit, 64 bit

and /proc/cpu-info says:
Intel(R) Atom(TM) CPU N455 @ 1.66 GHz
address sizes 32 bits physical 48 virtual

---

### Post by CelticWarrior on 2021-01-07
OK, it is 64-bit.

Please redo the USB or try a different stick.
And, of course, make sure the ISO isn't corrupt, either from a problematic download or from being transferred from one system to another.

---

### Post by ulrichmuc on 2021-01-07
I now verified the checksum: o.k.
Transferred to micro-SD chip (using Startup Disk Creator) now instead of USB-stick, attached via USB-cardreader to the Eee PC.
Same result: immediately after the boot screen, I see the grub menu from the hard disk.
Using dd instead of Startup Disk Creator makes no difference.

Now I found the SOLUTION:
It is not enough to set the boot Device Priority, but one has to
use Boot -> Hard Disk Drives
and make USB the 1st Drive.

Weird!

---

### Post by ActionParsnip on 2021-01-07
All OK now? Booting OK? I suggest you wipe the current 32bit install off and do a clean install of 64bit Ubuntu to avoid any cruft from the old install. You can restore your user data from your backups

---

### Post by ulrichmuc on 2021-01-07
Yes, all going well now. Currently I am installing, looks good. Thanks to all who tried to help.

ulrich

---

