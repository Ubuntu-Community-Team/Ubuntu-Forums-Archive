---
title: "[SOLVED] kubuntu intrepid: where's the mount manager?"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by linomac on 2008-10-06
in kubuntu 8.04 i had a gui mount manager under control panel.
now at systemsettings i dont see such a tool.
do i have to install something?

how mounting of usb external disks or other internal disk partitions takes place in kubuntu intrepid? without cli

Added later: i found kvpm at adept and tried.
still it is not what i m looking for, like it was in the past.

I d like to mount automatically the partitions that i choose, either internal (eg my windows partition, either external).
I d like to mount them directly from dolphin.
now i see hard disk icons (they represent partitions and disks) at dolphin, i click them but nothing happens.

Gparted also recognized partitions.
The funny thing is that i saw all partitions at "devices recently pluged in" widget, but still choosing was doing nothing

Thanks

thanks

---

### Post by linomac on 2008-10-07
i see that if i run kdesudo dolphin (dolphin as root)
then i can mount
anyway to do it automatically?

---

### Post by beartard on 2008-10-07
On my Kubuntu install, removable media are mounted automatically.  Dolphin lets you unmount and remount them much the same as the applet.  Haven't seen the same situation with konqueror, though.

---

### Post by Vorian on 2008-10-07
mountmanger is available in the universe

---

### Post by linomac on 2008-10-07
@beartard i made upgrade. u probably made new install

@vorian thanks for mountmanager. yes it can mount, but still i would like to be able to mount directly from dolphin, or some kde systemsettings control panel applet
thanks

---

### Post by linomac on 2008-10-08
maybe something has changed in HAL or other things responsible for hardware in the new version?

---

### Post by hardhu on 2008-10-08
> **linomac said:**
> maybe something has changed in HAL or other things responsible for hardware in the new version?

Check this bug:
[https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/269615](https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/269615)

---

### Post by linomac on 2008-10-08
ok, let's hope bug will be fixed soon.
thanks

---

### Post by linomac on 2008-10-16
after yesterday update dolphin can see other partitions, so urgent need for mount manager.
althought it would be a useful tool if it existed a kde4 mouning manager at system settings

---

