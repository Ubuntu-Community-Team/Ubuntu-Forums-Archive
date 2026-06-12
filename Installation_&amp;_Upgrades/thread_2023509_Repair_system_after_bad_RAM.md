---
title: "Repair system after bad RAM?"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by tars_ac on 2012-07-12
All,

I recently found out that one of my four sticks of RAM had an error (that was not present when I first installed the sticks a month or two ago.  During that time I've done quite a bit of installing and updating of packages and I'm quite worried that I have several corrupt package (especially as I'm getting numerous crash reports from system packages...).  Luckily my data is safe as it was backed up and for various reasons I haven't changed that much since then.

Does anyone know of a way to just re-download and reinstall the currently installed packages without having to go through the hassle of reinstalling the OS?  Looking to avoid reconfiguring everything as it took me a while to get everything where I can deal with it after upgrading to 12.04.

Thanks!

---

### Post by papibe on 2012-07-12
Hi tars_ac.

You need to generate a list of your current packages and then 'reload' them on your new installation.

There are 2 options:
[LIST]
[*]Using synaptic, or
[*]Using command line commands.
[/LIST]
[Here]("http://ubuntuforums.org/showthread.php?t=1057608") are both explained (see post #8 for the second one).

I'll be doing this myself since I'll be installing 12.04 on my 10.04 desktop (any time now).

Since synaptic is no longer installed by default, command liners seem like a good option.

Hope it helps.
Regards.

---

### Post by jmfal on 2012-07-12
You can try rebooting into the recovery kernal and  do dpkg -fix broken packages,

but I'm pretty sure it won't do it in one shot, may take  few tries, 

And not sure if all will be fixed.

---

### Post by tars_ac on 2012-08-09
Thought I'd update this in case someone else had the same problem.  I ended up reinstalling the packages, but I was still seeing crashes, so I decided to do a fresh install of 12.04 again since I figured it didn't work.  I've seen fewer crashes since, but it turns out that some of the crashes were due to known Ubuntu bugs in Unity.  So, not sure if it was worth reinstalling or not.

---

