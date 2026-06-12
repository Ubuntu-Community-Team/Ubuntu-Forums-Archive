---
title: "VMWare is gone after upgrading to Hardy Heron"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by runesvend on 2008-04-28
Last Friday I upgraded Ubuntu to version 8.04, and a couple of days after I needed to use VMWare Server which usually is in my Applications->System Tools menu, but after upgrading Ubuntu it is gone!

I've tried using *find* to find anything that matches "vmware". It finds some files but I'm not sure which one to use to recreate the link in my Applications menu, or if the program is gone. I've attached the results from *find*. What can I do to restore VMWare?

Thanks in advance.

---

### Post by elaiel on 2008-04-28
If you have been using VMWare-Server it is probably gone after an upgrade. This is not an Hardy specific issue and happend after every major ubuntu upgrade.
There are 2 possible strategies for you.
1 - wait until the hardy specific .deb file is released (takes probably a couple weeks) or
2 - try to install it yourself - see [http://wiki.archlinux.org/index.php/Installing_VMware#vmware_and_kernel_2.6.24_compile_modules_problem ]("http://wiki.archlinux.org/index.php/Installing_VMware#vmware_and_kernel_2.6.24_compile_modules_problem") for hints.

I would recommend you wait until you can install it via apt.

---

### Post by MasterSander on 2008-04-28
My vmware was also deleted. It asked me during upgrade: "Do you want to delete these unneeded packages?" And vmware was one of those, so like elaiel says vmware hasn't made an update for hardy yet, so just wait a while.

---

### Post by runesvend on 2008-04-29
OK. Thanks for your replies. I guess I'll wait until the deb file is released. As the linked page says, it's an "ugly hack" so I think I'll wait :)

But shouldn't I clean up all the vmware-specific files like these:

> 
/etc/init.d/vmware-server
/etc/xinetd.d/vmware-authd
/etc/rc6.d/K20vmware-server
/etc/pam.d/vmware-authd
/etc/vmware
/etc/rc5.d/S20vmware-server
/etc/rc3.d/S20vmware-server
/etc/rc1.d/K20vmware-server
/etc/rc0.d/K20vmware-server
/etc/rc4.d/S20vmware-server
/etc/rc2.d/S20vmware-server
/usr/bin/vmware-config.pl.old.0


Since VMWare is now gone it should be safe to delete these right? I'd rather not clog up my system with scripts to non-exisiting programs.

---

