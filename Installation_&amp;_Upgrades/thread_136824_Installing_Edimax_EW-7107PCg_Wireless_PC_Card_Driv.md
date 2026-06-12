---
title: "Installing Edimax EW-7107PCg Wireless PC Card Drivers"
date: 2006-02-26
forum: Installation &amp; Upgrades
---

### Post by laplatakid on 2006-02-26
I've been playing with Ubuntu for several days and have it running well on two machines, with plans to install it on a third (now running SuSE 10.1) in the next few days. This means that I know just enough about Linux to be exceedingly dangerous. Hopefully, I also know enough to ask for help when I need it. So here goes...

I have an Edimax EW-7107PCg wireless lan PC card for my Toshiba notebook. The card uses the Inprocomm IPN 2220 chipset, which doesn't seem to be supported by most flavors of linux. Edimax e-mailed me a driver, filename IPN2220STA.o, that I should be able to install but I haven't been able to find any instructions on how to actually go about installing it. :confused: 

I assume I have to copy the driver to the proper directory (/sys/devices/...). Is this it? Can someone walk me through this?

The device manager finds the card and gives the following info for linux.sysfs_path:
> [Key] linux.sysfs_path   [type] text   [value] /sys/devices/pci0000:00/0000:00:11.1/0000:06:00.0
and the same for linux.sysfs_path_device and pci.linux.sysfs_path.

Thanks,
Jim Winters

---

### Post by dabear on 2006-03-18
Hi, I see you havn't got any answers. Did you figure this out? I just use the windows xp driver with ndiswrapper; working great :)

---

