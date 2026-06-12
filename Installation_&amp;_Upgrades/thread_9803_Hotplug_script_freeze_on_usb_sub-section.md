---
title: "Hotplug script freeze on usb sub-section"
date: 2005-01-01
forum: Installation &amp; Upgrades
---

### Post by ctof on 2005-01-01
When my ubuntu computer start, i stay in  freeze state during the script: hotplug

after some investigation (VERBOSE variable to yes)
it seems the pb comes from the scripts usb.rc
in this script, in the function maybe_start_usb, at the beginning, when it try to mount the /proc/bus/usb directory, my configuration match this case:
mount -t usbdevfs usbdevfs /proc/bus/usb

no pb for this command line, after that i have in this directory 5 other fields/dir:
001
002
003
004
devices

the pb is when we try to do a cat action on the "devices" file, the call block and never finish
So it's what the usb.rc script do some lines after the mount: 
grep -q -i bus /proc/bus/usb/devices.


when i start manually this scrit, i can see in the process list this grep which never stop.


i don't how fix this pb
maybe it comes fom my PC, it's a MSI Mega-pc 651 with a 5in1 card reader integrated and i suppose this hardware is plugged on the internal usb bus

any help is welcome because for the moment i have to de-activate the usb.rc scripts (to set the right variable in the /etc/default/rcS env file)

Thx 
and happy year to everybody

Christophe

---

