---
title: "Upgrade to 18.04: error on libvirt-daemon-system"
date: 2018-05-18
forum: Installation &amp; Upgrades
---

### Post by mathieu-tarral on 2018-05-18
Hi !

I just upgraded my system to Ubuntu 18.04,
and after a couple of apt-get install -f (the initial upgrade process ended with errors)
i have libvirt-demon-system package which seems to be broken:

```
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up libvirt-daemon-system (4.0.0-1ubuntu8) ...
Enabling libvirt default network
virtlockd.service is a disabled or a static unit, not starting it.
insserv: script libvirtd: service libvirtd already provided!
insserv: script libvirtd: service libvirtd already provided!
insserv: exiting now!
update-rc.d: error: insserv rejected the script header
dpkg: error processing package libvirt-daemon-system (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 libvirt-daemon-system
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Now this: 
update-rc.d: error: insserv rejected the script header

means that the rc script is wrong ??
Do you have the same problem ?

Thanks !

---

### Post by dino99 on 2018-05-18
Was you using some ppas previously ? are you able to install  and use 'synaptic' ? Maybe install and run (gtkorphan' to cleanup the system.

---

