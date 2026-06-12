---
title: "X Server doesn't work after upgrade to 10.04"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by atair81 on 2010-08-19
Dear community,

I'm using ubuntu for some time now but all what I usually do is using it. So I'm not a big expert with the details.
Some days ago I tried to update my ubuntu to the new version 10.04. During the installation some errors caused by wrong references between the packeges occured.

After some searching in the internet I found two problems.
1. I have to add the "i915.modeset=1" to the boot menu (if I do so the live-CD works, otherwise not)
2. It seems to me that I have the same problem as reported on this page:
[https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/591743](https://bugs.launchpad.net/ubuntu/+source/shared-mime-info/+bug/591743)
There mathew writes that he "zapped" the glib (I assume libglib-2.0.so.0). But I don't know exactly how. I can delete the libglib-2.0.so.0 but can I also change the link? Which version of glib should be used?

After starting ubuntu everything seems to work well until the login screen occures. After logging in the new 10.04 background changes to the old brown one and hour glass pointer is displayed. The only thing I can do is shut down the computer.
Are there any reports where I could search for the problem?

Notes:

    * During start up the message "no or unsupported wmi interface" occures
    * I tried to start the X-Server via "startx" in the bash. He starts and then shut down the X-Server. But I do not see an error message responsible for that.


My Laptop:

    * Acer Extensa 2902ELCi
    * Intel Celeron M 1.3 GHz
    * Intel 852GM chipset


Hope the problem description helps. If further input is required please tell me.
Kind regards
Atair81

---

