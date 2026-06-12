---
title: "Xubuntu beta proprietary broadcom driver install fails"
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by iPiggy on 2010-03-28
So I tried a bunch of thngs, including commenting out the "b43" entry in blacklist.conf and nothing works.

Rewind.

Fresh install of Xubuntu, try to activate Broadcom wireless in the "proprietary drivers" dialogue.

After downloading and attempting to install, it fails, 

"check /var/log/jockey.log"

```

2010-03-27 12:12:49,903 WARNING: modinfo for module wl failed: ERROR: modinfo: could not find module wl

2010-03-27 12:12:49,904 WARNING: /sys/module/wl/drivers does not exist, cannot rebind wl driver
2010-03-27 12:12:49,968 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-03-27 12:12:52,295 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-03-27 12:12:52,469 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-03-27 12:12:52,518 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-03-27 12:14:10,640 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-03-27 12:14:12,268 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-03-27 12:14:13,390 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2010-03-27 12:14:15,428 DEBUG: Shutting down

```

I've tried a number of variations; uninstalling bcmwl-kernel-source via synaptic, installing via apt-get install, removing with apt-get remove... combinations of these...  nothing seems to work.

So it failed to compile the 'wl' module, for some reason - bcmwl-kernel-source is not lucid-compliant perhaps?

And what's the 'blacklisting' about?  Does bcmwl-kernel-source compile a driver named 'b43'?  Why would it be blacklisted?

---

### Post by iPiggy on 2010-03-29
Doesn't look like this is going anywhere.

Ah well, looks like Xubuntu will be confined to VirtualBox for a while, until the production release comes out.   Need to do updates via wireless.

---

### Post by pisarz on 2010-03-31
Hi,
I have same situation with dell 1320 and Broadcom Linux STA driver in 10.04, have you fix your problem ?

---

