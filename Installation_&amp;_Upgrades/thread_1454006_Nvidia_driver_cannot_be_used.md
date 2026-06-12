---
title: "Nvidia driver cannot be used"
date: 2010-04-14
forum: Installation &amp; Upgrades
---

### Post by kornelix on 2010-04-14
A few days ago I installed 10.04 Lucid beta-2 and it came up OK. I then chose the recommended Nvidia driver "version current", which caused my system to come up in low graphics mode. I removed the driver and the system came up with no X11. I gave up.

Yesterday I installed again, hoping that newer updates would fix the problem. The boot is now OK with no proprietary driver activated and all updates installed as of now (April 14, 05:30 GMT).

The Hardware Drivers dialog shows two choices: Nvidia version 173 and "version current (recommended)". Both of these show the status "this driver is activated but not currently in use". The only option offered is the button "remove". 

So what am I supposed to do with this brilliant screen?

---

### Post by cryptotheslow on 2010-04-14
You could try the sudo nvidia-xconfig command in a terminal to write a new xorg.conf file which will contain the correct device entries (although I had to manually edit my display refresh rates and resolution due to having an old unrecognised monitor).

---

### Post by kornelix on 2010-04-14
xorg.conf seems to be obsolete. at least the newest Ubuntu no longer has it.

---

### Post by kornelix on 2010-04-14
Solved, somewhat.

I removed both drivers using the Hardware Drivers dialog.
I rebooted - all OK and Hardware Drivers says both drivers are not activated.
I activated the "recommended" driver using the Hardware Drivers dialog.
I rebooted - all OK and Hardware Drivers now says it is activated and in use.
Tried compiz (selected "normal" visual effects) and it works, so far.

So the driver works, if by accident you do the right black magic to get it installed.

---

### Post by cryptotheslow on 2010-04-14
It is quite common for the xorg.conf file not to exist - most cards and devices are auto-detected on startup these days.

I have absolutely no knowledge at all of 10.04 so it could very well have been deprecated entirely for all I know. I'm hoping not as I have to edit mine manually to cater for my antiquated and unrecognised screen.

I was going to recommend grabbing the most up to date drivers from the NVidia site as there are a lot of fixes and improvements, but I have just read that the installer fails on 10.04 at the moment. Hopefully that will be addressed by NVidia by the time lucid releases.

Anyways - glad you got it working.

---

