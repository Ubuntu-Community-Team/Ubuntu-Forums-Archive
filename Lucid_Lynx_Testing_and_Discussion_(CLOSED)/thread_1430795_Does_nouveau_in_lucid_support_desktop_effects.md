---
title: "Does nouveau in lucid support desktop effects?"
date: 2010-03-15
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DoeRayMe on 2010-03-15
Just wondering whether it does or not, i have an Nvidia 7900GS that i am trying out atm.

Thanks

---

### Post by Digital Hick on 2010-03-15
It does not on my machine.  Although I have to admit, it works very well otherwise.  I almost have screen tear eliminated.:popcorn:

---

### Post by Atermoon on 2010-03-15
The best you can get with nouveau right now is metacity compositing (enable it in gconf-editor > apps > metacity > global).

You can try adding the xorg-edgers ppa for 3d in nouveau but only if you know what you're doing. It seems to work pretty good for some people, sadly I'm not in that group :(

---

### Post by Digital Hick on 2010-03-15
> **Atermoon said:**
> The best you can get with nouveau right now is metacity compositing (enable it in gconf-editor > apps > metacity > global).

You can try adding the xorg-edgers ppa for 3d in nouveau but only if you know what you're doing. It seems to work pretty good for some people, sadly I'm not in that group :(

Any advice for screen tearing?:popcorn:

---

### Post by DoeRayMe on 2010-03-15
> **Atermoon said:**
> You can try adding the xorg-edgers ppa for 3d in nouveau but only if you know what you're doing. It seems to work pretty good for some people, sadly I'm not in that group :(

Got xorg-edgers ppa installed and working good, thanks for the advice :)

---

### Post by saracen on 2010-03-16
How do I install Nouveau if I already have the nvidia proprietary driver installed?  Can someone provide step-by-step instructions to remove the nvidia driver and install nouveau and get it working?  Thanks.

---

### Post by Half-Left on 2010-03-16
> **saracen said:**
> How do I install Nouveau if I already have the nvidia proprietary driver installed?  Can someone provide step-by-step instructions to remove the nvidia driver and install nouveau and get it working?  Thanks.

Just deactivate the NVIDIA driver from the Hardware Manager and it will revert back to the Nouveau driver.

---

### Post by peepingtom on 2010-03-17
Edit: Redundant/bad advice removed ;)

---

### Post by cariboo on 2010-03-17
Have a look at this [thread]("http://ubuntuforums.org/showthread.php?t=1423210") it explains how to disable the restricted driver.

---

### Post by schambee on 2010-03-17
you got desktop effects (compiz) working with nouveau and xorg-edgers ppa??? i really don´t think this is true! but if i´m wrong, could anyone tell me how to do so! i have nouveau from xorg-edgers installed! runs pretty smooth, but only in 2D!

---

### Post by Tompalaz on 2010-03-19
> **schambee said:**
> you got desktop effects (compiz) working with nouveau and xorg-edgers ppa??? i really don´t think this is true! but if i´m wrong, could anyone tell me how to do so! i have nouveau from xorg-edgers installed! runs pretty smooth, but only in 2D!

Same here. It worked perfect before I reinstalled Lucid A3 yesterday. :(

---

### Post by gnomeuser on 2010-03-19
> **Tompalaz said:**
> Same here. It worked perfect before I reinstalled Lucid A3 yesterday. :(

And me, I thought it was because the nouveau module was blacklisted but it didn't appear to make things right again. Also the ppa module isn't available for the -preempt kernel flavor which caused a little roadbump.

I am still trying to figure out what caused this.

---

### Post by Tompalaz on 2010-03-19
Maybe it's: (?) 

> 
== New in Lucid ==

Nouveau (gallium and mesa classic) support is enabled in mesa.

xserver master has been dropped from this PPA in favor of 1.7 branch, if you were previously using it please make sure you revert to the current packages so you can continue getting updates. For example sudo apt-get update && sudo apt-get install xserver-common/lucid xserver-xorg-core/lucid will be enough for most users unless xserver-xorg-dev xserver-xephyr xdmx xdmx-tools xnest xvfb xserver-xfbdev or xserver-xorg-core-dbg are also installed.

What packages would I need to install to use compiz?
Right now I have I nouveau-firware, libdrm-nouveau1, linux-backports-modules-nouveau-2.6.32-16-generic, linux-backports-modules-nouveau-lucid-generic and xserver-xorg-nouveau.

Maybe I've missed any package?

---

### Post by gnomeuser on 2010-03-19
> **Tompalaz said:**
> Maybe it's: (?) 



What packages would I need to install to use compiz?
Right now I have I nouveau-firware, libdrm-nouveau1, linux-backports-modules-nouveau-2.6.32-16-generic, linux-backports-modules-nouveau-lucid-generic and xserver-xorg-nouveau.

Maybe I've missed any package?

That has been the note for a while, even while it worked.

The change appeared for me after the nouveau module was merged in the main kernel package. I suspect it is somehow loading the built in version rather than the ppa external module.

*edit*

I would seem to be broken for a lot of people, but being a ppa and of the character it is, filing a bug would seem to be approached with caution.

---

### Post by RAOF on 2010-03-19
> **gnomeuser said:**
> ...
I would seem to be broken for a lot of people, but being a ppa and of the character it is, filing a bug would seem to be approached with caution.

Right.  It seems that 3d has broken upstream; gallium interfaces change quite rapidly, and things break.  This is why nouveau's 3d support is in xorg-edgers, not the main archive :).

Please do not file bugs about nouveau 3d failing.  It *will* do that from time to time.

---

