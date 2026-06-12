---
title: "Minimal CD install"
date: 2014-10-20
forum: Installation &amp; Upgrades
---

### Post by mayagrafix on 2014-10-20
For an older laptop I want a clean install of Ubuntu 14.04 "Trusty Tahr" Minimal CD with Lubuntu. When performing install I run into problems with network configuration. Is there a manual page specifically for this install procedure where I can get answers to network questions the install will ask? 

Pretty much figured SSID and WEP KEY, but other questions about network baffle me. Install program unable to connect to Internet.

---

### Post by Bucky Ball on 2014-10-21
So your install went okay but you are having issues with wireless? Did you install the lxde desktop environment? What else did you install? Network Manager? 

Did you use the minimal install ISO linked from [THIS]("https://help.ubuntu.com/community/Installation/MinimalCD") page?

Essentially, after install you should have a cursor to log in when you reboot and will be in a CLI. You are running the Ubuntu base only at that point.You then install EVERYTHING else. For a Lubuntu look that would be lxde. If you install lubuntu-desktop, don't bother with a minimal install in the first place. That is exactly the same as installing Lubuntu so just do that. Life will probably be easier if you want Lubuntu rather than Ubuntu with a clean install of Lubuntu.

If you want a minimal install, installing *ubuntu-desktop anything is not the way to go. :-k

You might find [THIS]("Older, but info still relevant while screenshots might be a bit different now: http://www.psychocats.net/ubuntu/minimal") of interest ...

PS: With a minimal install the system shouldn't be asking you any questions about networking or anything else (except what sort of machine you are wanting to set up, e.g. server, audio, video box, etc.). You are installing the base kernel.

---

