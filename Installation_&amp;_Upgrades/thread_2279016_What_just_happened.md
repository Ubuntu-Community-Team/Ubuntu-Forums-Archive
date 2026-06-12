---
title: "What just happened?"
date: 2015-05-20
forum: Installation &amp; Upgrades
---

### Post by Lloydb39 on 2015-05-20
I just accepted the latest updates for 14.04 and rebooted as instructed and now my computer has gone into super slow motion mode, especially on Firefox. Getting error messages, such as "Keyboard Input failed." Did they just send out the Mother of all Bugs or is there some other explanation?

---

### Post by QIII on 2015-05-20
Hello!

It would be very helpful to know your machine specifications and which point release you are running.  14.04, 14.04.1 or 14.04.2.

Cheers!

---

### Post by Lloydb39 on 2015-05-20
Sorry, it is a homebuilt 64-bit AMD computer with 8 gigs of memory. All system details shows me is 14.04 LTS and since I keep it updated I assume I have the latest

---

### Post by Bashing-om on 2015-05-20
Lloydb39; Hello;

Can not help but wonder if it is the 'firmware' package at fault, as there was an update this day:
What version do you have ?
```

dpkg -l linux-firmware

```

Mine for reference:
```

sysop@1404mini:~$ dpkg -l linux-firmware
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  linux-firmware 1.127.12     all          Firmware for Linux kernel drivers
sysop@1404mini:~$

```
on an old dual core AMD based system.

[INDENT][INDENT]it's a thought
[/INDENT][/INDENT]

---

### Post by tgalati4 on 2015-05-20
Looking at the changelog for [1.127.12]("https://launchpad.net/ubuntu/+source/linux-firmware/1.127.12"), there was a lot of stuff added (for new hardware) and a lot of patches for existing hardware.  So it's quite possible that you have a hardware regression.  Try rebooting into an older kernel and see if the behavior changes.

Compare the modules that you are running with the changelog list.  As the number increases, your chance of regression increases.

```
lsmod
```

---

### Post by kansasnoob on 2015-05-20
I updated the kernel in two of my Trusty machines this AM to 3.13.0-53-generic and encountered no problems. The only two things I can think of are:

(1) Maybe there is a regression in that kernel that effects your specific hardware so you might try booting the older kernel from the advanced grub menu.

(2) Sometimes kernel updates break proprietary graphics drivers. To see what's up there we'd need some info, like the output of:

```
lspci -v -s `lspci | awk '/VGA/{print $1}'`
```

---

### Post by Lloydb39 on 2015-05-20
lloyd@linux:~$ dpkg -l linux-firmware
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  linux-firmware 1.127.12     all          Firmware for Linux kernel drivers

---

### Post by Lloydb39 on 2015-05-20
and
lloyd@linux:~$ lspci -v -s `lspci | awk '/VGA/{print $1}'`
04:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cedar [Radeon HD 5000/6000/7350/8350 Series] (prog-if 00 [VGA controller])
    Subsystem: PC Partner Limited / Sapphire Technology Device e164
    Flags: bus master, fast devsel, latency 0, IRQ 79
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at fe920000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at d000 [size=256]
    Expansion ROM at fe900000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: radeon

I don't know how to reboot to an earlier kernel or how to get back after I did...

---

### Post by Bashing-om on 2015-05-20
Lloydb39; Wellll ..

Yeah, do check and older kernel:

Grub gives you the option to boot any kernel that is installed, and keeps a list of those kernels:
Boot to the grub menu ( hold shift key as ubuntu boots up ) . -> advanced options and 
select a kernel to boot.

Grub will comply.

[INDENT][INDENT]worth a shot to see what results
[/INDENT][/INDENT]

---

### Post by Lloydb39 on 2015-05-20
Thanks for the help. Turned out to be another AT&T Uverse screwup and not Linux at all. But the tips may be helpful another day.

---

### Post by Bashing-om on 2015-05-20
Lloydb39; Good deal ;

Solution found; appreciate that you provided such.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

