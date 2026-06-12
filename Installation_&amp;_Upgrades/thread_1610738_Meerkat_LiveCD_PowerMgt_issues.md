---
title: "Meerkat LiveCD PowerMgt issues"
date: 2010-11-01
forum: Installation &amp; Upgrades
---

### Post by suthagar on 2010-11-01
Hi all,

I'm trying to install 10.10 (x64) using live CD but after about 20 mins of operation my computer goes into sleep mode, even if I am actively using the sessions (e.g. web surfing etc)and won't wake up. The hard drive keeps working but the monitor is in power save mode and can't be woken up. 

This is most problematic when trying to do an install, as the the sleep mode kicks in even mid-install.  

So far I tried the following:

1. turned off all power management in gnome
2. used acpi=off at boot
3. switched from S1 to S3 and back again
4. uninstalled all power management packages 
5. configued power management in gnome to not go to sleep

No luck, and no change in behaviour. 

My hardware is as follows: 

GPU: 9800GTX+
CPU: Q9550 
MB: GA-X48-DQ6 (gigabyte)
MEM: 8GB (4x2GB DDR2)

When the system kicks into sleep mode, the GPU fan goes to full as well. So I assumed that there may be a graphics driver issue, but not sure how to update drivers whilst using a live CD.

I'm aware I can use text based install or the alternative install CD however, without going into too much detail these will not suffice for what I need to do. Sorry if this has been answered elsewhere, I did do a search but I may not have been using the right search words.   

I'm keen to get 10.10 up and running, grateful for any assistance from you unbuntu gurus out there.

Kind regards

S

---

### Post by P4man on 2010-11-01
When you boot from the livecd, press any key when you see the keyboard logo at the bottom, right after the bios. In that menu, select safe graphics mode (using F6 key iirc). See if that helps

TBH, I would be very careful here. It doesnt sound like the machine goes in to sleep mode, if it would, the harddrive would definately sleep. It sounds like your videocard throws the towel, possibly due to overheating? By default on 10.10 desktop effects are enabled which taxes your videocard somewhat. Are you positively sure the videocard is ok playing 3d games or something under windows?

---

### Post by suthagar on 2010-11-01
Hi P4Man,

Thank you for your response. The video card works perfectly under windows (plays starcraft, Civ V just fine) does all the 3D (aero)effects under windows 7.  Under Fedora 13 it does the Compiz effects just as expected as well. 

I'll try your suggestion and report back. But thanks for the lead. 
Is there anyway to turn off the desktop effects during a liveCD session?

Kind regards


S

---

### Post by P4man on 2010-11-01
To turn off desktop effects, go system > preferences > appearance > visual effects. Set them to none. If that solves it, then it might be an issue with the opensource nouveau drivers and *hopefully* installing the proprietary nvidia drivers will cure it.

---

