---
title: "Can't uninstall xorg-driver-fglrx"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by insert_name_here on 2007-12-21
I'm trying to uninstall xorg-driver-fglrx.

However, when using either the Synaptic GUI or with aptitude on the command line, I get an error message: 

> merrillj@merrillj-laptop:~$ sudo aptitude remove xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages will be REMOVED:
  xorg-driver-fglrx 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 27.0MB will be freed.
Writing extended state information... Done
(Reading database ... 119592 files and directories currently installed.)
Removing xorg-driver-fglrx ...
[B]dpkg-divert: rename involves overwriting `/etc/xdg/compiz/compiz-manager' with
  different file `/etc/xdg/compiz/compiz-manager.ubuntu', not allowed
dpkg: error processing xorg-driver-fglrx (--remove):
 subprocess post-removal script returned error exit status 2[/B]
Errors were encountered while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      


---

### Post by insert_name_here on 2007-12-21
Oh hey look.

Manually deleting the /etc/xdg/compiz/compiz-manager.ubuntu fixes it, although it probably erased my settings.  Oh well.

---

### Post by BLTicklemonster on 2008-01-06
Dude, thanks. I have been trying to get a pci nvidia card to work on this emachines t3508 for days now, and just today got to where I could even try to reconfigure xorg. 

Now my sound doesn't work at all, but I'm sure there's a fix for that, too.

Thanks again!

---

