---
title: "Hardy Installation Gripes"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by djrobthaman on 2008-04-29
Dammit.  Why do I have to mount all my hard drives whenever I reboot (maybe even log out and back in... haven't tried that one yet).

This morning I woke up and the system was completely frozen after being powered on all night.  I moved the mouse pressed some keys and all that happened was that after about 5 mins the screensaver came up.  Not an animated screensaver mind you, a still frame that obviously would be played along with many others in some sort of moving picture.

Then, after rebooting this morning then going to work, I come bake 10 minutes ago and turning on the monitor reveals a full on terminal session.  No gui, no error message given (not that I noticed anyway).  It was prompting me to log on.  I typed my name, pressed enter and a line break was created but there was no other prompt.  So I could keep typing and typing but I was never asked for my password.

I'm sorry.  I realize I'm ranting and blowing off steam but please, can somebody help me to figure out what went wrong with hardy and how to set it right.

---

### Post by lemming465 on 2008-05-05
The rant is OK, but there aren't enough details to let anyone help much.

If you have nvidia video, the current nvidia + Xorg + kernel situation on hardy may be unstable.  Either revert to the nv driver, or to 7.10, or hope it gets debugged soon.

The missing mounts is a little more mysterious, but you aren't the only having the problem.  Compare the contents of /etc/fstab to the output of *sudo blkid* and see if there are any mismatches in devices, UUID's, or labels.  You don't say whether or not this was a fresh install or an upgrade; upgrades have to cope with the change in IDE disk device names from hd to sd.

---

### Post by Pumalite on 2008-05-05
Check your screensaver. Sliders must be all the way to the right in Power Management.

---

### Post by fixitdude on 2008-05-06
> **Pumalite said:**
> Check your screensaver. Sliders must be all the way to the right in Power Management.I agree. Sounds like you need to change some settings for power management and also disable any sleep modes (check BIOS settings also) until you can figure what is causing the problem.

Also, CPUs can be shut down due to over temp, see if you can figure out what the CPU temp is with one of the utilities. If it's high there may be something running you don't want on. That would be in services, and ksysguard or "top" or "ps x" in a console may show you something taking a lot of CPU.

---

### Post by djrobthaman on 2008-05-07
Hello there,

So far I've solved the hard drives not mounting (they weren't in my fstab).  So now I have hds mounting on boot (although they are still shown in the places menu as external, anyone know how to fix that?)

I haven't been able to reproduce the terminal situation, but I still get freezes fairly regularly.  Actually it's happened twice today (though it's usually something like once every 3/4 days).

And on another note, my screensaver does not display properly.  When it displays, it plays in what looks like jerky slow motion.  Almost as if there's something that's maxing out the CPU.

Compiz has also been extremely unstable.  I'm using the default package that comes in the hardy repos, so I'm not sure what that's about.  That crashes constantly.  Is this just a version issue, cuz I've noticed it is much more up to date than what was shipped with gutsy (though I had a very stable third party version of compiz 7 running on gutsy).

Also fixitdude, could you recommend a monitoring programme.  I tried xsensor but it returns this error

```

Error opening config file: /etc/sensors.conf
Use -c option to specify location of lm_sensors configuration file.

```

PS  Sorry I posted without specs.  Here they are:

Video:
ATI 100-714600 Radeon X1300 256MB DDR PCI Express x16 All-In-Wonder 2006 Edition Video Card

Memory:
G.SKILL Extreme Series 1GB 240-Pin DDR2 SDRAM DDR2 533 (PC2 4200) Desktop Memory Model F2-4200PHU1-1GBLA

Keyboard/Mouse:
IOGEAR GKM541R 2-Tone USB RF Wireless Standard Multimedia Keyboard/Mouse Combo

Motherboard:
Foxconn 925XE7AA-8EKRS2 LGA 775 Intel 925XE ATX Intel Motherboard

Hard Drives:
Seagate Barracuda 7200.10 (Perpendicular Recording) ST3320620A 320GB 7200 RPM IDE Ultra ATA100 Hard Drive (X2)

Western Digital Caviar SE WD2000JB 7200 RPM Ultra ATA100 200GB

Also a 100GB disk I salvaged from a Dell machine

CPU:
Intel Pentium 4 541 Prescott 3.2GHz LGA 775 Processor Model BX80547PG3200EK

---

### Post by djrobthaman on 2008-05-07
Also, I have 11 processes that say they're each using 17179869180gb of memory

firefox
amarok
gnome-panel
nautilus
python
pidgin
gnome-system-monitor
avant
fast-user-switch-applet
emerald
kio_uiserver[kdeinit]

That's either not right or not good.  Either way, anybody know what I can do about that?

---

### Post by lordawesome on 2008-05-08
At least you guys could install hardy. I have a HP DV2225NR. The disk gets to about 82% and just hangs while installing. The screen says "Configuring APT" and it also says "Scanning CD". Well, the disc doesnt spin up unless you open/close the lid, or unplug/plug in the power. And even then, it doesnt read the disc. Oh, it also wouldn't boot correctly (or even get that far during install) if I have the power cord plugged in. Im sure it is probably a power management thing I can disable before installation, but I would not bother as I know of other people having issues with Hardy Heroin. true, they did get the issues fixed (video problems, firefox crashing, etc), but it was too much hassle than it was worth. I just dont feel like dealing with it at this time. Hopefully some patches will get out there, and I can attempt an upgrade from gutsy... Maybe Ill have some better luck.

---

### Post by lemming465 on 2008-05-09
Memory is a slight fuzzy concept, since some of it is shared, or not allocated, or swapped out.  Resident working set is a first approximation of what an active program is using.  If things look wonky, first reboot, and if they go wonky again, post a screen snapshort from "top" after giving the "M" command to sort by memory usage.

---

### Post by djrobthaman on 2008-05-09
> Memory is a slight fuzzy concept, since some of it is shared, or not allocated, or swapped out. Resident working set is a first approximation of what an active program is using. If things look wonky, first reboot, and if they go wonky again, post a screen snapshort from "top" after giving the "M" command to sort by memory usage.

Here's a screenshot

---

### Post by lemming465 on 2008-05-10
That's got to be a bug in gnome-system-mo; I don't believe it.  For a different view, let's open a terminal window (Application -> Accessories -> Terminal).  At the command prompt type "top".  After it refreshes, press "M" (capital M).  Let's see what that looks like.  On my system it (1 GiB RAM) it looks like this with two users logged in:

---

### Post by djrobthaman on 2008-05-10
You're right.  Something's off about system monitor.

---

