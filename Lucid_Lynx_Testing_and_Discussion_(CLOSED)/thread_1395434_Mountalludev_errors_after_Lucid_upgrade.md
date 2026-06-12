---
title: "Mountall/udev errors after Lucid upgrade"
date: 2010-01-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by awacs on 2010-01-31
after upgrading, I get a string of udev errors (which I couldn't record) and then a mountall failure, and I drop to a maintenance shell.Typing mountall there gives the error:


"libudev: udev_monitor_new_from_netlink: error getting socket: Invalid argument 
"mountall:mountall.c:2955: Assertion failed in main: udev_monitor = udev_monitor_new_from_netlink (udev, "udev")"

Eh?

---

### Post by brettg on 2010-02-01
Got the same here after Hardy -> Lucid

This is apparently a bug in the mountall package.

You can workaround it by issuing the following commands at the tty emergency console;

mount -n -o remount,rw /
mkdir /var/run/network
/etc/init.d/networking restart
mkdir /dev/pts
mount /dev/pts
/etc/init.d/ssh restart

You should be able to ssh into the server like usual and start up any other services that may not be running.

Don't restart the machine or logout though or you will have to go through the above procedure again.

More info here;
[http://www.tumblr.com/tagged/Karmic](http://www.tumblr.com/tagged/Karmic)

---

