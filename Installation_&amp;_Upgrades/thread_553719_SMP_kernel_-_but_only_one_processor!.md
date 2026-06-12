---
title: "SMP kernel - but only one processor?!"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by jarthurs on 2007-09-18
I've just installed Ubuntu Server 7.04 onto a machine which has three processors installed (Compaq Proliant 5500) and it has correctly detected and installed the generic i686 kernel (2.6.20-16-generic #2 SMP) but I am only able to see processor 0

cat /proc/cpuinfo lists only one processor and there is only a cpu0 entry in /sys/devices/system/cpu

The full system spec is:

Compaq Proliant 5500 (Xeon)
3 x 550MHz Pentium III Xeon processors (all detected on boot)
2Gb RAM
SmartArray 3200 controller (10 x 9.1Gb Ultra2 drives)

Anyone shed some light onto this as everything appears to have installed fine. I'm currently running VMware Server 1.0.3 with a small test VM working well and everything appears to be behaving.

Regards,
Jason.
:confused:

---

### Post by jnorth on 2007-09-18
Sounds like apic.  Your motherboard might be too old.

How about a post of your dmesg?

---

### Post by jarthurs on 2007-09-19
Now solved, see [http://ubuntuforums.org/showthread.php?p=3390477#post3390477](http://ubuntuforums.org/showthread.php?p=3390477#post3390477) for details.

Many Thanks,
Jason.

:)

---

### Post by jnorth on 2007-09-19
Cool - I was wrong but glad you got it solved :)

---

