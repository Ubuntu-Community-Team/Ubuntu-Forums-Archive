---
title: "The new Ubuntu desktop does nor run"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by csevcik on 2011-04-26
I'm having troubles upgrading from 10.10 to 11.04. So far I have upgraded 4 machines OK (some bugs as expected from a beta), but a 4th machine (Identical to one of the 3 mentioned above) an HP Pavillion All In One MS200 refuses to use the new Ubuntu desktop and defaults to Classic Ubuntu with a message stating that "the hardware does not support the Ubuntu mode", which works perfectly in the other identical machine. Both HP's have the same ATI driovers installed and are equally updated, the xorg.conf files seems identical too. The HPs have AMD 64 processors.

A similar message is produced by a 5th machine a Dell Precission 610 with two 2.4 MHz Xeon cores and and nVidia 173.14.30 driver and an NVIDIA GPU Quadro FX 500/FX 600 (NV34GL) agp graphic card.

I have 3 more machines to upgrade, Any suggestions on how to solve the problems with the 2nd HP and the Dell?
:confused:

---

### Post by mikewhatever on 2011-04-26
Unity is known to not work on some hardware, including older Nvidia cards. To avoid excessive frustration, those cards had been blacklisted, and will by default, fall back to Gnome2. You can override the blacklisting by adding UNITY_FORCE_START=1 to /etc/environment, but do expect problems.

---

### Post by csevcik on 2011-04-26
"Unity is known to not work on some hardware, including older Nvidia cards. To avoid excessive frustration, those cards had been blacklisted, and will by default, fall back to Gnome2. You can override the blacklisting by adding UNITY_FORCE_START=1 to /etc/environment, but do expect problems"

The nVidia in the Dell is somewhat old, but What about the identical HP's with ATI chips which are less that 1 year old? Why would Unity work only in one of them?

---

### Post by mikewhatever on 2011-04-26
I don't know about the ATI cards. Do you have the model?

---

### Post by csevcik on 2011-04-26
From Xorg.0.log I get:

Adapter ATI Radeon HD 3200 Graphics  has 2 configurable heads and 1 displays connected

Still, its the same in both machines, as far as old, from the same file I get:

Connected Display0: LVDS
Display0 EDID data
Manufacturer: HWP  Model: 4105  Serial#: 257
Year: 2009  Week: 19

---

### Post by Mark Phelps on 2011-04-26
While Ubuntu 11.04 remains in testing, you will get better and faster responses if you post your 11.04 questions to the Natty Development forum.  That is located at: Other Community Discussions --> Development & Programming --> Natty Narwhal Testing and Discussion.

Good Luck

---

