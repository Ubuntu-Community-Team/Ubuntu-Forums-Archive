---
title: "Upgrading to Ubuntu 16.04 broke everything."
date: 2016-08-15
forum: Installation &amp; Upgrades
---

### Post by huike3 on 2016-08-15
With the open source driver and the banning of the proprietary rglrx driver ubuntu is basically unusable. I can only use one monitor as my other monitors are not recognized. Games cannot use hardware acceleration. Running the unity test shows the driver as the VMware driver. My sound doesn't work anymore either. I'm going to go reboot into windows now and then cry myself to sleep.

---

### Post by wildmanne39 on 2016-08-15
Do you want help with the sound issue if so please ask or we will move your post to recurring.

As for the driver issue it is being worked on it was not banned, and they think it will be ready soon, cross fingers!

---

### Post by QIII on 2016-08-15
Hello!

You mentioned the VMWare driver.  Are you running Ubuntu in a virtual machine?

By the way, I can run three monitors just fine without fglrx using the Radeon driver and tested with four on the same card with AMDGPU.  I am back to three with AMDGPU.

Not that any of that matters if you are using the virtual hardware provided by VMWare.

---

### Post by deadflowr on 2016-08-16
I'd double check that you have either the radeon or amdgpu driver actually installed:
```
dpkg -l | grep -E '(radeon|amdgpu)' | awk '{print $1,$2}'
```
then if installed, double check that fglrx did not leave any residuals behind, like an xorg.conf file 
(look in /etc/X11 for any xorg.conf files, perhaps it wasn't properly removed and is causing confusion, thus the vmware driver being used.)

These would be the first two things to look into, in my opine, opine.

---

### Post by tommysts on 2016-08-16
me too same problems can not update

---

