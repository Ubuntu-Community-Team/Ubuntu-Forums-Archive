---
title: "Unusual vmware server problem with Gusty"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by laser_in_your_eye on 2007-10-23
I've compiled the source code for vmware server 1.0.4 (from vmware's website) in Gusty (32 bit) and have applied the "vwmare-any" patch ([http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/]("http://ubuntu-tutorials.com/2007/09/26/how-to-install-vmware-server-on-ubuntu-710/")).   Unlike other people posting with this problem, I can load vmware with no problems and can see my virtual machines that worked with Feisty.  When I try to start up those virtual machines now, the screen goes black as if the OS is about to load and then it just stops.  I don't get an error message at all--it just stops.  Does anyone have any suggestions on how to fix this?


For reference, I'm running a Thinkpad T61 with a fresh install of Gusty.

thanks

---

### Post by laser_in_your_eye on 2007-10-23
it looks like the problem was the virtual machine location.  i had it on my ntfs partition and apparently vmware is not compatible with ntfs-3g.

---

