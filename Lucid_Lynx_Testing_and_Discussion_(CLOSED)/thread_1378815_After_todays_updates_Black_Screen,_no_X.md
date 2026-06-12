---
title: "After todays updates: Black Screen, no X"
date: 2010-01-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by VMC on 2010-01-11
I feared this at some point. I have a Intel i865 integrated video.

I think the problems lays here, at xserver core:

$ aptitude show xserver-xorg-core
Package: xserver-xorg-core
State: installed
Automatically installed: no
Version: 2:1.7.3.902-1ubuntu**[COLOR="red"]4[/COLOR]**

My Kubuntu 10.04 had updates as well with the same Xorg updates to beo applied. I didn't update Kubuntu. Here's Kubuntu xserver core:
$ aptitude show xserver-xorg-core
Package: xserver-xorg-core               
State: installed                         
Automatically installed: no              
Version: 2:1.7.3.902-1ubuntu**[COLOR="Red"]2[/COLOR]**

I can boot ok only with a "**nomodeset**". I haven't had to do this since Jaunty days.

Anyone else with i865 or similar Intel chip having difficulties?

Thanks.

---

### Post by Starks on 2010-01-12
Same here, but I think my X got thrashed by xorg-edgers and a faulty pre-removal script.

---

### Post by Eddie Hung on 2010-01-12
A me three here. Tried downgrading using my cached debs (downgraded xserver-common and core, and some other mesa stuff that was also upgraded at the same time; also tried going back down to the -9 kernel) but I still see graphics corruption in X, followed by an eventual crash unless I VT-switch to shell.
Intel DG45FC with X4500HD on AMD64 here.

Eddie

---

### Post by collinp on 2010-01-12
Open a terminal, have a look at /var/log/Xorg.0.log using your text editor of choice after you boot, and see if you see any funky errors.

---

### Post by Eddie Hung on 2010-01-12
No errors under Xorg, but there was an error under dmesg. 
Even when re-using the -9 kernel which was working before the upgrade today, I see this:

> 
[drm:i915_hangcheck_elapsed] *ERROR* Hangcheck timer elapsed... GPU hung
[drm:i915_hangcheck_elapsed] *ERROR* i915_wait_request returns -5 (awaiting 32 at 31)


Contrary to the first post, X does work for me, but there's corruption on the top edge and after a minute of use, then crashes.

Adding nomodeset to the kernel command line seems to have temp-fixed it for me.

Eddie

---

### Post by DragonlordP on 2010-01-12
Similar problems here, on an MSI Wind U100+: I had the top edge corruption yesterday, today the image occasionally "jumps" a few cm to the left and it's also gone black 3 times so far (closed the lid to suspend to fix it).

---

### Post by DragonlordP on 2010-01-12
Just went white, this is so much fun :D

---

### Post by VMC on 2010-01-12
Todays updates fixed my problem on i856. Namely xserver-xorg-core:

$ aptitude show xserver-xorg-core
Package: xserver-xorg-core
State: installed
Automatically installed: no
Version: 2:1.7.3.902-1ubuntu**5**

---

### Post by KrazyPenguin on 2010-01-12
> **VMC said:**
> I feared this at some point. I have a Intel i865 integrated video.

I think the problems lays here, at xserver core:

$ aptitude show xserver-xorg-core
Package: xserver-xorg-core
State: installed
Automatically installed: no
Version: 2:1.7.3.902-1ubuntu**[COLOR="red"]4[/COLOR]**

My Kubuntu 10.04 had updates as well with the same Xorg updates to beo applied. I didn't update Kubuntu. Here's Kubuntu xserver core:
$ aptitude show xserver-xorg-core
Package: xserver-xorg-core               
State: installed                         
Automatically installed: no              
Version: 2:1.7.3.902-1ubuntu**[COLOR="Red"]2[/COLOR]**

I can boot ok only with a "**nomodeset**". I haven't had to do this since Jaunty days.

Anyone else with i865 or similar Intel chip having difficulties?

Thanks.

Yes adding "nomodeset" worked for me.
Today's updates fixed the problem, i removed nomodeset and rebooted and everything was fine.
Thanks for the tip!!!!
;-)

---

### Post by Ibidem on 2010-01-12
I had that problem with a 945 chip (I updated a few minutes before the problem was posted), and same as everyone else, today's update fixed it.
The troublemaker may have been x11-common or xserver-xorg-core.  I think I'll try to save the latest versions locally & check cache for the old ones.
Sounds like it was X itself, not a driver issue.
Ibidem

---

### Post by dagrump on 2010-01-12
Well I'd love to try "nomodeset" but I can't get to the menu for some reason.
Holding down the space bar doesn't get there. Has that changed since Karmic? 
At first I was concerned it was a hardware issue but a live disk works fine. My backlight is turning off as soon as the white ubunutu symbol & text disappear. This is a laptop with intel 945 chipset, there should be a fairly large menu as it has been steadily upgraded from KK alpha 5 or at least that is the lastest 32 bit disk I've located.
This is the first hiccup this little beast has shown.

---

### Post by Ibidem on 2010-01-12
I thought it was escape to get to the GRUB menu? I use a multiboot setup, so haven't had to use that in ages.
(the menu shows by default)
BTW, I'm using the same chipset (945) with no trouble--right now.
Ibidem

---

### Post by ranch hand on 2010-01-12
Try the shift key.  It is the one that works.

---

### Post by dagrump on 2010-01-13
Thanks, Ranch hand that worked. I'll try "nomodeset" when I get home tonight. Maybe I can keep this old install going a bit longer.

Edit: Scratch that she is updating now. I needed some coffee in my system any way, & she can update while I shower.

---

### Post by jerrylamos on 2010-01-13
i845G with Lucid 2.6.32-10 boots to black screen unless at grub I do down arrow, e, end, nomodeset, Crl-x.

Then runs a few minutes with Gnome, then FREEZE. ssh doesn't even work.  Dead altogether.

With LXDE runs tens of minutes then FREEZE.  ssh doesn't even work.  Dead altogether.

Culprit from /var/log/Xorg.0.log is:

 2.634776] (II) LoadModule: "evdev"
[    2.635818] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    2.636237] (II) Module evdev: vendor="X.Org Foundation"
	compiled for 1.7.2, module version = 2.3.2
	Module class: X.Org XInput Driver
	ABI class: X.Org XInput driver, version 7.0

Namely intel driver 2.3.2. which just came in on a deadly update.

How do I back level xorg intel driver to one that works, example karmic level?

Thanks much, jerry

---

### Post by VMC on 2010-01-13
> **jerrylamos said:**
> ...How do I back level xorg intel driver to one that works, example karmic level?
Thanks much, jerryI was wondering that myself when the next update came and it fixed my i865.

I know you know about the [RevertingIntelDriver]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4"), but maybe you can apply to the last current Intel driver. Just seach for that deb file. I noticed that the above link is still very active.

---

### Post by ranch hand on 2010-01-13
With the number of x updates we have been getting I would just hold on and see if it got straight with updates.

---

### Post by Sef on 2010-01-13
>  		With the number of x updates we have been getting I would just hold on and see if it got straight with updates. 	

I had the same problem, so I went into recovery mode and then to fix broken packages.   That worked for me.

---

