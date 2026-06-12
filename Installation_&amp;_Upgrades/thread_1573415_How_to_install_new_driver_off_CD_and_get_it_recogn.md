---
title: "How to install new driver off CD and get it recognized"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by buggyruss on 2010-09-12
System - Xubuntu 8.04.4 but equally valid for other Ubuntu variants

I installed an updated driver for an Intel network card by doing a "make install" from its src directory (copied from install CD). That appears to have successfully created a file named "e1000.ko" and placed it in a subdirectory named "e1000" in the appropriate /lib/modules/.../drivers/net directory. Based on the contents of the Makefile the "make" also invoked "depmod -a". The "make" doesn't appear to have done anything else interesting.

However, on reboot this new module is not the one being loaded (based off of strings in the dmesg log file), instead the original as distributed with Xubuntu is.

Obviously, I have to do more than the installation instructions on Intel's CD say to do...

What steps do I still need to do to get this new driver recognized in place of the original?

(it is no huge deal if the only answer I get is an honest "Don't bother" since the driver that came with Xubuntu appears to work "fine", however the Intel driver is a full Version number higher so I'd expect it to be somewhat "better" by some measure)

---

### Post by Troublegum on 2010-09-12
You have to blacklist the old driver so that it doesnt get loaded on startup. 
And you have to tell ubuntu to use the new driver. 

First, you have to use lsmod in the terminal to find out the name of the old driver module. 
Search the list for modules whose name indicate that they belong to your network card. Then blacklist that module: Open /etc/modprobe.d/blacklist.conf as root and add a line:
```
blacklist modulename
```where *modulename* is the module you want to blacklist. 

Then, tell ubuntu to load the newly compiled module. Open /etc/modules as root and add a line
```

e1000

```

You might run into problems if the old module is named e1000 too. In that case, it might help to specify the full path to the e1000 module in /etc/modules (e.g.  /lib/modules/.../drivers/net/e1000.ko).

---

### Post by buggyruss on 2010-09-12
Thanks, I'll give that a try - the modules both are named e1000 (file is e1000.ko) so I'll have to give the full pathname for the new version - BTW, that new module is in a subdirectory also called e1000 (that is /lib/modules/.../net/e1000/e1000.ko) and there is no apparent module name "e1000.ko" anywhere else in the /lib/modules tree.

---

