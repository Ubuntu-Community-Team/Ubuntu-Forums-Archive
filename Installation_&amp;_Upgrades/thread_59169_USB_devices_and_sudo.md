---
title: "USB devices and sudo"
date: 2005-08-23
forum: Installation &amp; Upgrades
---

### Post by simoncullen on 2005-08-23
Okay, one problem down...

When I first installed it was detecting my external USB harddisk (ntfs) and my digital camera SD card.  That's no longer working.  However, my USB mouse is still okay.  I've tried turning off the harddisk, rebooting, etc., but it just wont work.  I've tried to mount the device with the -t tag (mount -t ntfs /dev/sda) but it complains that I'm not root.  I tried to use sudo but it complains that I'm not a sudoer.  I can't edit the file /etc/suders either!  It's really frustrating not having a root account.  

I also can't use the user management system (under, system, administration, users and groups.  it asks for my password and then quits.)  I might need to reinstall because I think I've messed this up and I can fix it with out root access!

Anyway, any help is appreciated!
Simon

---

### Post by odin on 2005-08-23
I'm not sure about your problem if you really need to be root(as I can see) then just type this:

sudo passwd root

enter your existing password
enter your password for root
confirm your password for root


and when you finish doing what you need just type " sudo passwd -l root" to disable it.

Hope this can help you a bit.

---

