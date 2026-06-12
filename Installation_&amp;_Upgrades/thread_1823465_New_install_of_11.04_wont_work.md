---
title: "New install of 11.04 wont work"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by 1guy21 on 2011-08-12
after many minutes of getting ubuntu 11.04 to finally begin installation, it now freezes when booting
> Begin: running /scripts/init-bottom ...done.
 
i managed to log on after going through recovery mode. but mouse didnt work.
now recovery mode stops at > [ 3.020137] sd 2:0:0:3: [sde] attached SCSI removeable disk
 
boots into xp just fine
 
 
 
compaq sr1120nx
1.5 gb ram
320 gb hdd
32 mb intel graphics
intel celeron processor @2.67 ghz

---

### Post by manzdagratiano on 2011-08-13
If you are using the 32-bit installer, try using the 64-bit one, and see if it changes anything.

---

### Post by steve11911 on 2011-08-15
If the install fails after making sure the install disk and the cd drive are good...then...

Because the hardware is older I'd recommend trying a small handful of linux live cd's to verify compatibility before attempting the full install.Might start with 10.04LTS and work backwards...

In your favor:
Intel shows CURRENT linux driver support for the 845 chipset:

[http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Embedded+Components+and+Flash+Memory&ProductLine=Embedded+Chipsets&ProductProduct=Intel%C2%AE+845+Chipset+Family]("http://downloadcenter.intel.com/SearchResult.aspx?lang=eng&ProductFamily=Embedded+Components+and+Flash+Memory&ProductLine=Embedded+Chipsets&ProductProduct=Intel%C2%AE+845+Chipset+Family")

2005 posted erratta,specific to this hardware, worth a glance:

[http://www.linux-noob.com/forums/index.php?/topic/1276-how-to-fedora-core-3-on-compaq-persario-sr1120nx/](http://www.linux-noob.com/forums/index.php?/topic/1276-how-to-fedora-core-3-on-compaq-persario-sr1120nx/)

Before giving up, I'd look here:

[http://www.tuxradar.com/content/whats-best-lightweight-linux-distro](http://www.tuxradar.com/content/whats-best-lightweight-linux-distro)

---

