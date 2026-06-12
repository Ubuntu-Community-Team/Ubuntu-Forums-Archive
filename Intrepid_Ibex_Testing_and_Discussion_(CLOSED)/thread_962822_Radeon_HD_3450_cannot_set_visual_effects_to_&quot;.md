---
title: "Radeon HD 3450 cannot set visual effects to &quot;extra&quot; setting."
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by 73ckn797 on 2008-10-29
System has Radeon HD 3450 video card (this is my son's box). Ibex does load has good resolution. In System/Accessories/Appearance/Visual Effects, I cannot set it to "extra" mode. I would like to have desktop effects but driver installed on installation of Intrepid RC does not support this. I do not see any additional driver specifically for this video card. This is after installation updates have been applied. Install performed 10/29/2008.

Also, the login screen comes up but text entered for user and password is very small and almost illegible. Default login screen otherwise appears normal.

Suggestions?

edit: I just may have to exercise my "Dad" options and purchase a Nvidia card.

---

### Post by RAOF on 2008-10-29
Have you installed the restricted drivers for your card?  The default open-source drivers don't do 3d (needed for desktop-effects) on your card, so you'll need to go to System->Administration->Hardware Drivers and enable the restricted "fglrx" driver before desktop-effects will work.

---

### Post by 73ckn797 on 2008-10-29
> **RAOF said:**
> Have you installed the restricted drivers for your card?  The default open-source drivers don't do 3d (needed for desktop-effects) on your card, so you'll need to go to System->Administration->Hardware Drivers and enable the restricted "fglrx" driver before desktop-effects will work.


Initially there were no restricted drivers listed there. I did use Synaptic and tried one there but it did not specifically list the HD 3450. Upon reboot the system started popping up comment panels with choices but, again as mentioned about logon, the text was very small and illegible. I had to boot through recovery mode to even get back into the system. Then in the driver section there is another restricted driver listed but that caused the same boot problem. Otherwise I do have a good basic video driver but just cannot get any effects working.

If my son did not do some gaming I would have him completely converted to Ubuntu. After a recent XP re-install he got a trojan from a download and now wants to install Ubuntu and use virtual Box. I have that on my system with XP installed. My system uses a Nvidia card and has not had the driver problems that the ATI has. That is the "Dad" option I refer to also.

I will be looking further into things tomorrow.

Thanks.

---

