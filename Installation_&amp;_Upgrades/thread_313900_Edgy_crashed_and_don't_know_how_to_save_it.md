---
title: "Edgy crashed and don't know how to save it"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by fw0127 on 2006-12-06
Hi,
I have update to edgy, it runs, but after using the automatic updater,then restart,the graphic booting processing is stopped](*,) , reason

udevd[2175] add_to_rules:invalid ACTION operation
udevd[2175] add_to_rules:invalid rule '/etc/udev/rules.d/85-hal.rules:5'

and the file look like this:
#Have udev pass data over a socket to hal
RUN+="socket:/org/freedesktop/hal/udev_event"

#unmout block devices when thez are removed
SUBSYSTEM=="block",ACTION="remove", RUN+="/usr/lib/hal/hal-unmount.sh"

many thanks,

---

### Post by shin on 2006-12-06
After Action there should be double '='. This is my file:

```
# Have udev pass data over a socket to hal
RUN+="socket:/org/freedesktop/hal/udev_event"

# unmount block devices when they are removed
SUBSYSTEM=="block", ACTION=="remove", RUN+="/usr/lib/hal/hal-unmount.sh"
```

Try it.

Probably some syntax changed with new version of udev and update didnt change contents of rules files.

---

### Post by fw0127 on 2006-12-06
hi,shin,
thank you for the tips, but how to change it, it shows  "read-only system" after I try to save it as root, this happens also in recover-mode:( 
???

---

### Post by fw0127 on 2006-12-06
I have changed the file use the live-cd, but the system halt, should I remove the file and have a try?:mad:

---

### Post by shin on 2006-12-06
There is no error? it just halts?

You may try to reinstall udev. Or just remove it for now. It's not that vital for system. Use livecd - mount your ubuntu partition in e.g. /media/ubuntu
then 
```
sudo chroot /media/ubuntu
```
and either 
```
sudo apt-get remove udev
```
(write down all packets that it would want to remove) and then install one more time or maybe just 
```
sudo dpkg-reconfigure udev
```
will help (I doubt it)

Strange that it just halts with no message.

---

### Post by fw0127 on 2006-12-06
sorry, it is worse now, the reinstall of udev fails,due to the package broken; and now the boot cannot proceed, the console enter ash, all job are stoped ...it is just like a nightmare:twisted:

---

