---
title: "Total messup after update"
date: 2011-10-07
forum: Installation &amp; Upgrades
---

### Post by rienesl on 2011-10-07
Hi,
I have a BIG problem with one of my ubuntu machines. I was running 11.04 and everything was fine. Then update manager wanted to install a lot of uptates and now I have several problems. No X-Server, no network (worst of all) and a lot of errors while starting.
Doing a "normal" startup results in that:
```
udevd[314]: error: runtime directory '/run/udev' not writable, for now falling back to '/dev/.udev'
udevd[641]: Failed to execute '/lib/udev/bluez-udev' '/lib/udev/bluez-udev": No such file or directory
...
init: Unable to connect to the system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
...
Filesystem mounted on /dev/shm; setting up compatibility bind mount
Please remove this mount from /etc/fstab; it is no longer needed, and it is preventing completion of the transition to /run/shm.
 * Activating swap... [OK]
mount: you must specify the filesystem type
 * Cannot check root file system because it is not mounted read only.
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service S20module-init-tools start
 
Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start S12dbus
start: Unknown job: S12dbus
...
start: Unknown job: S89cron
 * Enabling additional executable binary formats binfmt-support [OK]
 * Checking battery state... [OK]

```
That's it. Then the system hangs. When pressing [ctrl]+[alt]+F1 I can open a console and work with that, but typing ifconfig gives only a loopback device and typing startx results in crashing the machine.
 
Where to start?
 
/run/udev is not existent and creating it is useless (it is gone after restart)
fstab is clean, all the mentioned items which are making errors are not in there!
running "sudo init 1" and then "Repair defective packages" (hoefully this is translated right by me) results in 1189 for update, 306 for new install and 43 to delete, but with no network connection this is not possible...
 
Hoping for some help,
 
Martin

---

