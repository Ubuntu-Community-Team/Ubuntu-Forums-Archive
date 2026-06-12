---
title: "error mounting /proc/bus/usbfs - mobile broadband"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by fysiker on 2010-05-18
hi community.
 
I#ve been searching for hours but my problem won't get solved just removing the "usb-line" from /etc/fstab
 
The problem is:
I can mount easily usb-sticks just by plugging them into the pc.
on the other hand i'm not able to use my mobile broadband.
when i go to network icon (marked with a red [COLOR=red]![/COLOR]) network is activated, the settings for the mobile broadband connection is set up correctly. (it used to work in ubuntu 9.10)
 
even the device /dev/sr1 (the mobile broadband) can get mounted just by clicking on the device.
 
thanks for your help

---

### Post by fysiker on 2010-05-18
I think to recognice when I set up the connection via the wizzard the hauweii e160 was recogniced / identified. I removed the old config and tried to make a new one.
Now on the first screen there is nothing selectable as device.

Is this problem caused by kernel?

How to downgrade maybe as alternative solution?

Any info to provide? Syslog didn't told me unusual things. 

Kind reguards

(ubuntu 10.04, x86, amd k8, 512 mb ram)

---

### Post by fysiker on 2010-05-18
sorry for pushing

---

### Post by anglican on 2010-05-19
> **fysiker said:**
> sorry for pushing
I'm not clear on what the problem is here. You mention an error mounting /proc/bus/usbfs in the title but not in the message. Since Karmic, usbfs is not compiled into the kernel so anything depending on it wont work. You may be able to work around the problem with:
```
sudo mount --bind /dev/bus /proc/bus
sudo ln -s /sys/kernel/debug/usb/devices /proc/bus/usb/devices
```To undo the above (which may break other things) use:
```
sudo umount /proc/bus
```H

---

