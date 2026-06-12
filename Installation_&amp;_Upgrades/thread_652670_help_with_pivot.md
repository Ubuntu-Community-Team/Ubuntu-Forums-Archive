---
title: "help with pivot"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by oldsoundguy on 2007-12-29
OK folks .. have installed an nVidia card (6200) and installed the nVidia drivers.

I am using an NEC 1810 xtra view (pivot enabled) LCD monitor and have it entered into the system.

I still have a grayed out "rotate" button on the system> preferences> screen resolution screen.

What do I do to activate that button?  (and please, IF it is to go in and edit, place instructions on HOW to get there and do the deed!)  THANKS.

---

### Post by bharadwaj on 2007-12-29
i guess installing the i810switch from synaptic package manager would solve the problem

---

### Post by oldsoundguy on 2007-12-29
that just turns the display on and off, it does not PIVOT (ROTATE) the display to portrait or full page mode.

---

### Post by oldsoundguy on 2007-12-29
Nevermind .. had to use NANO as an editor and add a line to the video card "Options  "RandRRotate" "on"

---

### Post by oldsoundguy on 2007-12-29
Thought I would post the entire procedure just in case someone else needs it.

First .. this works on nVidia cards ONLY (ATI is still asleep at the switch!). (and in GNOME)

Make sure you have used System> Administration> Screens and Graphics and selected both your card (you may have to use the  legacy driver) AND your monitor. Set your resolution now. 
You will be required to re-boot to verify the settings.

THEN
Open the terminal.
sudo nano /etc/X11/xorg.config   ( **note the X is upper case** )  hit enter.
enter your password
nano will open (nano is an editor)
scroll down to the card
below the driver line type in THE WHOLE LINE:
Option         "RandRRotate" "on" (**note again the upper case letters**)
hit control O
hit enter (this will re-write xorg.config and create a back up of the old file)
hit control x (this will exit)
then control/alternate/backspace
sign in again
System>  Preferences> Screen resolution
the Rotation choice should now be usable.

---

