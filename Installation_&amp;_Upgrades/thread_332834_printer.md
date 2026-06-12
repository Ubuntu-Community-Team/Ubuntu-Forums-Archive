---
title: "printer"
date: 2007-01-06
forum: Installation &amp; Upgrades
---

### Post by miro14 on 2007-01-06
Im trying to install epson dx4250 printer. The conection is via USB. 
The problem:
ubuntu does not autodetect my printer.

My  ls -lR /dev/bus/usb looks like this:
/dev/bus/usb:
total 0
drwxr-xr-x 2 root root 60 2007-01-06 20:11 001
drwxr-xr-x 2 root root 60 2007-01-06 20:11 002
drwxr-xr-x 2 root root 60 2007-01-06 20:11 003
lrwxrwxrwx 1 root root 14 2007-01-06 19:11 devices -> .usbfs/devices

/dev/bus/usb/001:
total 0
crw-rw-r-- 1 root root 189, 0 2007-01-06 20:11 001

/dev/bus/usb/002:
total 0
crw-rw-r-- 1 root root 189, 128 2007-01-06 20:11 001

/dev/bus/usb/003:
total 0
crw-rw-r-- 1 root root 189, 256 2007-01-06 20:11 001


i don't have choice in printer properties to select Printer Port :usb or something
What is the solution?

---

### Post by miro14 on 2007-01-06
Anyone please?

---

