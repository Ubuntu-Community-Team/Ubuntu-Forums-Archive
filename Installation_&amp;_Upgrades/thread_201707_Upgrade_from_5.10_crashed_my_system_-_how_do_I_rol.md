---
title: "Upgrade from 5.10 crashed my system - how do I rollback to 5.10?"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by pracslipkerm on 2006-06-22
I just tried to upgrade my secondary PC to 6.06 and it has crashed! 
It boots to the GUI Login screen but will only login as failsafe terminal (nothing else lasts - they return...
```
GLib-GObject-WARNING **: IA_g_object_get_varlist: object class 'GnomeProgram' has no property named 'goption-context'
Bonobo-ERROR **: file bonobo-ui-init-gtk.c: line 87 (init_info != NULL)
aborting...
```

I have tried changing the repositories in /etc/apt/sources.list around to clean dapper and clean breezy and doing an update, -f install and dist-upgrade but they all fall over after trying to login.
The initial upgrade failed at..
```
coreutils_5.93-5ubuntu4_i386.deb
pre installation script error exit status 2
dpkg error code (1) 
```
I am fairly new at all this and would really be very thankful for any help - I am lost as to what to do next???](*,) 
Cheers
Steve Griffiths

---

### Post by rcarring on 2006-06-22
Can you boot to a commandline?

Hit Esc when you see the grub loading message and choose safe recovery.

This should let you boot the system and leave you in as "root".

From there you may be able to use apt to fix your system.

---

### Post by pracslipkerm on 2006-06-23
I am able to get to the command line. How do I use apt-get to roll back to 5.10? When I change the sources.list to breezy it just says that there are 0 packages to update etc. 
Thanks in advance
Steve - soooo out of my depth - Griffiths

---

### Post by pracslipkerm on 2006-06-25
I found that during the installation there was an error while trying to overwrite a file. I deleted this file and tried again and low and behold it worked!
I am now up and running on Dapper minus sound and usb - off to search the forums....
Thanks for the help guys!
Steve - slowly getting to know my way around linux - Griffiths :-)

---

