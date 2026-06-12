---
title: "psad error while installing things"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by milenixloerdi on 2009-11-24
Hi guys. Everytime I try to install something now from the "Application" menu programs, I get an error - here's how it looks:

> Setting up psad (2.1.5-1) ... 
Starting Port Scan Attack Detector: psad 
[*] Could not find mail, edit /etc/psad/psad.conf at /usr/sbin/psad line 9566. 
 * Unable to start the daemon. 
invoke-rc.d: initscript psad, action "start" failed. 
dpkg: error processing psad (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up libao2 (0.8.8-5ubuntu1) ... 
 
Setting up libnautilus-burn4 (2.25.3-0ubuntu3) ... 
 
Setting up cdrdao (1:1.2.2-18ubuntu3) ... 
Setting up nautilus-cd-burner (2.25.3-0ubuntu3) ... 
 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 psad 
Can soemone please tell me how to fix this "psad" error - I have no idea what it is and it appeared to start happening after the last update.

--------------------------------------

I uninstalled psad from Synaptic Package Manager - this seems to work, but I hope I have not violated my original linux firewall with this action.

---

