---
title: "no shutdown : sandy bridge: 10.10"
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by chkeller on 2011-07-07
Hello,

on ASUS P8H67-M Pro with i3-2105, power management not working: shutdown/hibernate/suspend all lead to reboot. Restart not working.  Harddrive, DVD and Monitor same as before.
shutdown or poweroff do not work, Ubuntu terminated but power still on. This from Gnome and terminal.

acpi=force doesn't work
 acpi=off doesn't work
 openoffice quickstarter: not started.

Errors in log:   HEST: Table not found!  ERST: Table not found!
Aside from the 4 sec power off, I have no solution, any ideas?

Ch.Keller

---

### Post by chkeller on 2011-07-11
Gave up and upgraded to 11.04. Now restart and shutdown work. Hibernate and suspend also lead to shutdown. Anyway, better than before.

---

### Post by www.rzr.online.fr on 2011-11-02
Hi I also miss those tables on my SB platform (lenovo g460) :

[http://rzr.online.fr/q/lenovo](http://rzr.online.fr/q/lenovo)



what are they for ?


Can we compare our bios ?

sudo acpidump  | grep -v '^ '
DSDT @ 0xbcfee000

FACS @ 0xbcf6e000

FACP @ 0xbcffb000

SLIC @ 0xbcffd000

ASF! @ 0xbcffc000

HPET @ 0xbcffa000

APIC @ 0xbcff9000

MCFG @ 0xbcff8000

WDAT @ 0xbcfed000

SSDT @ 0xbcfec000

BOOT @ 0xbcfea000

ASPT @ 0xbcfe7000

SSDT @ 0xbcfe6000

SSDT @ 0xbcfe5000

XSDT @ 0xbcffe120

RSD PTR @ 0xfe020

---

