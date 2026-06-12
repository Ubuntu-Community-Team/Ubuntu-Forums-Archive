---
title: "Dapper broke vmware"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by Othersider on 2006-06-03
Hi,

I was running Breezy Badger til today, when I decided to upgrade to Dapper Drake using the update manager.

It went well, but after a reboot, I opened vmplayer and it gives me an error after I select my virtual machine and closes:

> 
Could not open /dev/vmmon:
No such file or directory.
Please make sure that the kernel module `vmmon' is loaded.


This was on an installation done by using the perl files.  Thinking that perhaps I had done something wrong, I uninstalled vmware and installed again using Dapper's Add/Remove programs.  Same problem continues.

I encounter these errors in configuration:
> 
Starting VMware services:
   Virtual machine monitor                                            failed
   Virtual ethernet                                                   failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

invoke-rc.d: initscript vmware-player, action "start" failed.
dpkg: error processing vmware-player (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-player


Any ideas?

Thanks in advance.

---

### Post by Dillinger on 2006-06-03
You have to rerun the vmware configuration script.  

```
sudo vmware-config.pl
``` and follow the instructions and you're good to go

---

