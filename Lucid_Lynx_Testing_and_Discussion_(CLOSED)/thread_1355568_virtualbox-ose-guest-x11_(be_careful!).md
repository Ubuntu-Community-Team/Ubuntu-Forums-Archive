---
title: "virtualbox-ose-guest-x11 (be careful!)"
date: 2009-12-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ankspo71 on 2009-12-15
Hi,
Lucid Alpha 1  (sorry I accidentally said Karmic LOL)

Package:
virtualbox-ose-guest-x11 (3.0.8-dfsg-1ubuntu1)

wants to **remove** ubuntu-desktop, xorg, xserver-xorg, xsever-xorg-core, and related files according to synaptic package manager.

Just a note, 'apt-cache show' does not show this information, but I am not about to try apt-get to see if it does or not. I think I'll pass on installing any VirtualBox packages this time.

Be careful while testing everyone. :(
James

---

### Post by ankspo71 on 2009-12-15
I reported this at
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/496901](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/496901)

Update: 12/17/09
The bug I reported has been merged with 
[https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/495935](https://bugs.launchpad.net/ubuntu/+source/virtualbox-ose/+bug/495935)

This affects 32bit and 64bit - Ubuntu 9.10 alpha 1

---

### Post by SevenMachines on 2009-12-15
The problem is,

virtualbox-ose-guest-x11 
Provides: xserver-xorg-video-5, xserver-xorg-input-4

but in the new xorg,
xserver-xorg-core
Conflicts: xserver-xorg-video-5, xserver-xorg-input-4

---

### Post by ankspo71 on 2009-12-15
Hi,

It is still a problem, right?

Btw, [https://launchpad.net/~sevenmachines/+archive/nvidia](https://launchpad.net/~sevenmachines/+archive/nvidia) 
Is that you?
If it is, thanks for the nvidia 195 driver for Lucid.
It's working great for me :D

---

### Post by SevenMachines on 2009-12-15
nvidia also suffers from the xserver-xorg-video-5 conflict with xserver-xorg-core. the 195 ppa version just generates this dependency automatically to -6 on rebuild. with no quality control checks!

---

### Post by xebian on 2009-12-15
> **ankspo71 said:**
> Hi,
Lucid Alpha 1  (sorry I accidentally said Karmic LOL)

Package:
virtualbox-ose-guest-x11 (3.0.8-dfsg-1ubuntu1)

wants to **remove** ubuntu-desktop, xorg, xserver-xorg, xsever-xorg-core, and related files according to synaptic package manager.

Just a note, 'apt-cache show' does not show this information, but I am not about to try apt-get to see if it does or not. I think I'll pass on installing any VirtualBox packages this time.

Be careful while testing everyone. :(
James

The current VirtualBox release is 3.1.  The previous release was 3.0.12 FYI.  3.0.8 is old.

---

### Post by ankspo71 on 2009-12-15
> **xebian said:**
> The current VirtualBox release is 3.1.  The previous release was 3.0.12 FYI.  3.0.8 is old.

Thanks,
3.1 is definitely newer so later today I might try to compile it from source (it's funner like that) :D

---

