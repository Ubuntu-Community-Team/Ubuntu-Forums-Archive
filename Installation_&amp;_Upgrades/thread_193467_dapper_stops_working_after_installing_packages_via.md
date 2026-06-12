---
title: "dapper stops working after installing packages via apt-get?"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by cruizer on 2006-06-10
i don't know if any of you have experienced something like this, but this has happened to me three times already, once with dapper beta 2 and two times just today with dapper final.

i installed ubuntu dapper on my notebook (generic notebook, with Intel 855GM chipset) and it worked great at first. no need to install 915resolution to go to 1024x768 (previous dapper betas and breezy defaulted to 640x480 unless i did a 915resolution tweak) and my RaLink RT61 wifi chipset worked out of the box.

however after doing an apt-get and shutting down, when i go back to it the system no longer can use my usb mouse nor my synaptic touchpad. it doesn't mount the NTFS partitions (windows xp) anymore. and it couldn't detect the wireless and built-in Ethernet ports anymore. the first time it happened to me i just installed network-manager and network-manager-gnome. the second time it happened to me i just performed an apt-get upgrade to patch my system.

i really couldn't understand what's happening here. could it be that some process here is corrupting my kernel, modules or configuration files? has anybody encountered something similar to this?

anyway i'll try installing dapper again (3rd time i'll do it today) and i'll continue to observe what's happening here...

---

### Post by cruizer on 2006-06-10
well i tried it again...apparently it's not apt-get. but i still couldn't determine what's corrupting it... in all instances of the corruptions i didn't upgrade the kernel.

by the way what i've done different this time is to update without activating the universe/multiverse repositories. could it be that the problem is there?

---

### Post by cruizer on 2006-06-12
really weird but it's no longer happening now. i just hope it won't happen again

---

