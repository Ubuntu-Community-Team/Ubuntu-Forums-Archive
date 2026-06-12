---
title: "todays updates killed my system"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by techno-mole on 2008-10-26
Hello, my system updated this morning, only a couple of updates, and as i cant actually do anything with my system i cant tell you what they were.
but what ever they were i cant use my pc at the moment, the updates did something to the xserver and now i cant seem to use the nvidia driver anymore, or desktop effects for that matter.

if i boot up in recovery mode and select the " try to fix xserver " option i can get the desktop to load, but it wont let me use any effects or load compiz, if i start compiz manually it doesnt do anything because im not using the nvidia driver, but if run a terminal and type " sudo nvidia-settings " it tells me im not using the driver, and i should run " nvidia-xconfig " as root, if i do this and re-start the xserver i then cant get a usable desktop.

is there a way i can find out what updates were done today so i can post a bug report on launchpad ?
cheers

forgot to mention im using the beta of intrepid (kubuntu, although thinking of going back to using gnome)

---

### Post by Yashiro on 2008-10-26
There are no 'fully working' nvidia drivers for the new Xorg yet.
When you force load the old driver you will just lock up.

Basically, no 3d or compiz until nvidia release a new driver.

---

### Post by wgrant on 2008-10-26
> **Yashiro said:**
> There are no 'fully working' nvidia drivers for the new Xorg yet.
When you force load the old driver you will just lock up.

Basically, no 3d or compiz until nvidia release a new driver.

nvidia drivers 71 and 96 do not work with the new xserver. 173 and 177 work fine!

---

### Post by techno-mole on 2008-10-26
i was using the 177.80 driver (which was giving full 3d support) but now i cant use it, what happens is that when i log in, i get the splash screen, with the little loading icons (kde 4.1) then all i get is a cursor and a black screen, and oddly the 2 karamba themes i have running, and nothing else.

the driver (177.80) was working perfectly this morning until i updated, i think the updates were something to do with the hardware abstraction layer, i think it is (HAL) but either way i now have an issue.

ive also noticed that some of the menu options are no longer there, or at least the launchers, for example the fusion-icon launcher, that is usually under system isnt there, and neither is the hardware launcher (the one you can click on, and it will tell you what drivers your running type of thing) but according to adept they are installed, from what i can gather some of these options have something to do with the hal, or the hal has something to do with them ?

maybe i will post another bug report on launchpad.

cheers

---

