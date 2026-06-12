---
title: "No Wallpaper after Upgrade"
date: 2008-06-03
forum: Installation &amp; Upgrades
---

### Post by TenPlus1 on 2008-06-03
I jsut finished running an upgrade for 113 items (3rd june 2008) and everything downloaded and installed without a problem, then I reboot my system and No Wallpaper!

I dunno why this happened but just-in-case I re-intalled Nautilus and Nautilus-Data and reboot again, still nothing!  The desktop colours and gradients work fine, just no wallpaper...

Any ideas ???

---

### Post by ChameleonDave on 2008-06-03
I don't know why the wallpaper went.  More importantly, are you able to put it back?  It's only a problem if you are unable to.

---

### Post by TenPlus1 on 2008-06-03
Lol, if I was able to put it back then their wouldnt be a problem...

As it stands Ubuntu will not let me put a wallpaper on my screen at all, only desktop colours and gradients...

---

### Post by Pablo Pablovski on 2008-06-03
Might be a dumb question (if so, sorry), but Is the disk from where the image is loaded actually mounted ok? If not, that's your problem - or, rather, fixing it so it does mount is the problem!

---

### Post by TenPlus1 on 2008-06-03
Yeah, wallpaper file is on my /home drive and it's mounted ok...  Just for some reason I cannot use jpg/gif/png for wallpaper...  Only happened after today's update and dunno why...

---

### Post by TenPlus1 on 2008-06-03
OK, I got my wallpaper working again but I had to manually edit the gnome settings through the configuration editor and turn on (again) Draw Desktop and type in the name of my .jpg file...

The Appearance program seems to be botched and taked up 80% of my processor and isn't working properly for wallpapers...

---

### Post by sweetnsourbkr on 2008-06-03
I still have my wallpaper after the upgrade ( June 3 ) but I can't seem to be able to change them on the Background utility.  Looks like a bug.

I can add, but I can't select wallpapers from the table.  I'm using the fglrx ati driver.

---

### Post by t-tbone on 2008-06-04
Same story here.  I applied a week's worth of updates and rebooted.  Now my desktop wallpaper is gone and I can't apply a new one.  All of the images are just as they were in my Documents folder with full read permissions.  I get no contextual menu when right clicking the desktop and I can't apply a background image in the control panel.  ATI driver in use here.

It also did away with my Terminal profile and put me back at default.

Trent

---

### Post by t-tbone on 2008-06-05
Found this:

[https://bugs.launchpad.net/ubuntu/hardy/+source/nautilus/+bug/236778](https://bugs.launchpad.net/ubuntu/hardy/+source/nautilus/+bug/236778)

---

