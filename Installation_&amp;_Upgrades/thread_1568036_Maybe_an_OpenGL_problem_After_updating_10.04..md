---
title: "Maybe an OpenGL problem? After updating 10.04."
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by peptobismal on 2010-09-04
Okay, now, I have looked for answers to these questions, but alas have found no luck. First specifications:

AMD Athlon II X4 630 (2.8Ghz)
OC-Z 4GB DDR2-800
Gigabyte MA78LM-S2H (Using on-board Radeon)
My harddrive is a little bit older SATA 160Gig... probably going to end up imaging it over to a new one when I get the money for it.

Okay, so after I did the NEWEST update to 10.04, which after running so many distro's before I don't know why I even upgraded all the way up like I did with this one. So, dumb of me to do, but no going back now.

I booted it back up and got the "Low graphics mode" error. Everything was running smoothly before the upgrade. (This upgrade included the "wget" package and some other updates to miscellaneous stuff.)

I have tried to do everything I have found on forums from earlier versions and so forth. I have ran the commands in the terminal to make sure that all my drivers are still seen as there and they are. It's gotta be something really simple, but I dunno.

I was giving up on it and going to not worry about it, but some games and Blender 3D also seem to not want to run. Photoshop CS2 still runs and everything else, but yeah... I am not big on limitations of the programs I can use. The aesthetically pleasing window things I can do with out. I don't know if this is a problem with something that got upgraded or what... I might try to uninstall Blender and do it over again, but not too sure. It does not really feel like a program based problem as there are other 3D programs that will not open. Maybe it's an OpenGL problem?

---

### Post by clrg on 2010-09-04
Has your graphics driver been updated? You mentioned additional miscellaneous packages.

---

### Post by peptobismal on 2010-09-04
I don't believe so... I mean from what I could tell it was just random program updates nothing major... that wouldn't have been under the other stuff would it have? I got all my programs to open now, just a restart. Now it's just the low graphic acceleration on games makes it impossible to even have any fun playing these FPS's in my downtime, because of all the choppiness and stuff. I am guessing I am getting like 20 FPS or lower?

EDIT: Oh also, I can NOT boot from the newest version of the kernel I have to drop down one to get my computer to run properly. Any ideas?

---

### Post by peptobismal on 2010-09-05
Okay, here's what I did earlier... I uninstalled the driver and re-installed, but when it's done it gives an error about "InstallArchives() failed"

I just deleted my /usr/share/ati and am re-installing the driver... It seems to have installed... I am going to reboot and see what's going on.

---

### Post by clrg on 2010-09-05
I don't know about ATI drivers, I have a nVidia card. I need to recompile the driver every time I get a kernel update, maybe this will solve the problem for you too. Try booting from the newest kernel and get to a terminal. Then try to reinstall your driver from there (or if the GUI works, of course there's no need for the terminal).

---

### Post by peptobismal on 2010-09-05
Sorry, I didn't respond last night and I had gotten it fixed.

I did the following:

sudo rm -r /home/jeff/.ati *I believe that was the folder... Double check me on the folder name.

> Then went to Hardware Drivers and used that to re-install the driver...

* You will still get the low graphics mode thing.

Then you go to synaptic and search for everything with fgl in it and download all the fglrx files that have stars next to them as they are your accelerators and so forth.

---

