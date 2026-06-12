---
title: "Bug in kernel installation"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by Saltash on 2006-10-14
Hi all,

I've just installed Ubuntu and now I'm setting up a new kernel.
It appears that `make install` calls a script, /usr/sbin/mkboot, 
to set the root device (among other things). This script may fail, 
leaving the installed kernel image in an unbootable state.

On my system, there is a "procbususb" filesystem that gets mounted
automatically. There is also a "proc" filesystem that gets mounted. 
So, when I issue the command `mount`, the following lines are displayed 
(among others):

proc on /proc type proc (rw)
...<SNIP>...
procbususb on /proc/bus/usb type usbfs (rw)

This trips the mkboot script. The script checks the output of 
the `mount` command to see if the proc filesystem is mounted.
But it can't handle two lines beginning with the letters "proc".
I suggest the following patch as a remedy:

=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

20c20,22
< if [ $(mount | grep -o "^proc") ] && [ -e /proc/cmdline ]; then
---
> ## SAW ## patch broken "/proc" check:
> ## if [ $(mount | grep -o "^proc") ] && [ -e /proc/cmdline ]; then
> if [ -n "$(mount | grep -lw proc)" ] && [ -e /proc/cmdline ]; then

=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

Hopefully this is found useful.

---

