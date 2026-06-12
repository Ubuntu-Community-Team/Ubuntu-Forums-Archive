---
title: "After UPDATE ureadahead error and no WIFI"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by KA8WTK on 2011-01-21
I just finished taking a normal Update Manager update. On re-start I get a ureadahead error on boot and my prevoiously working Netgear WG111v3 wireless usb dongle does not power up and Wicad reports "no wireless networks available". Funny, I am sitting next to one.
The driver is still installed, but iwconfig does not show the wireless adapter.
Is this a bug in the update?
(small voice saying HELP!)

Bill

This is also posted under Networking as I am not sure if this is network or update issue.

---

### Post by KA8WTK on 2011-01-22
I seem to have found the problem. The last update gave me a new real time kernel (2.6.33-7rt) that does not have ndiswrapper.ko in it. I reverted to the previous rt kernel and WIFI is back in business without the ureadahead error.
Now, to figure out how to get ndiswrapper.ko in the new kernel........

---

