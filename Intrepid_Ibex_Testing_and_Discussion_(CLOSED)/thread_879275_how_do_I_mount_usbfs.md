---
title: "how do I mount usbfs"
date: 2008-08-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-08-03
Hi all, 
 I have bought an APC 800 VA UPS and am on Intrepid Ibex (8.10) . 

There is a cable which gives output from the UPS'es data port to the computer's USB port . I am unable to see some of the info. apparently due to usbfs is not mounted. 

Googling I found there is something called mountdevfs.sh script (which is part of the initscripts package) . 

The problem is that the mountdevfs.sh script doesn't have those lines which many of the links says the script should have. 

[http://www.linuxforums.org/forum/ubuntu-help/121543-usbfs-support-logic-understanding.html](http://www.linuxforums.org/forum/ubuntu-help/121543-usbfs-support-logic-understanding.html)

[https://help.ubuntu.com/community/Nomadii](https://help.ubuntu.com/community/Nomadii)

The above are two examples. 

Giving the file as is shown :-

```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          mountdevsubfs
# Required-Start:    mountkernfs
# Required-Stop:
# Should-Start:      udev
# Default-Start:     S
# Default-Stop:
# Short-Description: Mount special file systems under /dev.
# Description:       Mount the virtual filesystems the kernel provides
#                    that ordinarily live under the /dev filesystem.
### END INIT INFO
#
# This script gets called multiple times during boot
#

PATH=/lib/init:/sbin:/bin
TTYGRP=5
TTYMODE=620
[ -f /etc/default/devpts ] && . /etc/default/devpts

TMPFS_SIZE=
[ -f /etc/default/tmpfs ] && . /etc/default/tmpfs

KERNEL="$(uname -s)"

. /lib/lsb/init-functions
. /lib/init/mount-functions.sh

do_start () {
    #
    # Mount a tmpfs on /dev/shm
    #
    SHM_OPT=
    [ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT=",size=$SHM_SIZE"
    domount tmpfs shmfs /dev/shm tmpfs -onosuid,nodev$SHM_OPT

    #
    # Mount /dev/pts. Master ptmx node is already created by udev.
    #
        domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE
}

case "$1" in
  "")
    echo "Warning: mountdevsubfs should be called with the 'start' argument." >&2
    do_start
    ;;
  start)
    do_start
    ;;
  restart|reload|force-reload)
    echo "Error: argument '$1' not supported" >&2
    exit 3
    ;;
  stop)
    # No-op
    ;;
  *)
    echo "Usage: mountdevsubfs [start|stop]" >&2
    exit 3
    ;;
esac

```This is the file at /etc/init.d/mountdevfs.sh

Now it doesn't have the following code which should be there according to the other links given above 

```

mkdir -p /dev/bus/usb/.usbfs
    domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
    ln -s .usbfs/devices /dev/bus/usb/devices
    mount --rbind /dev/bus/usb /proc/bus/usb
```Now should I add this bit or need to do something else?

Initscripts version 2.86.ds1-59ubuntu2

Any help/additions/suggestions/improvements welcome. I am clueless what I need to do.

---

### Post by stijngysemans on 2008-08-24
I'm having the same problem: I want to load midiman firware drivers using usb filesystem but its not mounted.

---

### Post by ShirishAg75 on 2008-10-16
stijngysemans I was able to solve this one by first doing 

```
mount -t usbdevfs none /proc/bus/usb
```

and getting stuff there and then finally putting that entry into /etc/fstab as :-

```
none  /proc/bus/usb  usbfs  defaults  0  0
```

Yours may differ a bit as you would want to have read and write values so the last bit will differ.

---

