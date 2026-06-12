---
title: "Please help me set up this frustrating laptop"
date: 2006-06-25
forum: Installation &amp; Upgrades
---

### Post by intent on 2006-06-25
I've been frustrated with my girlfriend's Averatec 6200 series laptop ever since she got it (before I met her), because it would constantly overheat, among other problems. 

I got her a laptop cooler, but nothing else can be done about the overheating (and the laptop's non-refundable). Today I decided to install Ubuntu on it so it's more secure and she can't mess anything up, and I'm using the advanced install CD (I didn't have a copy of the Live CD with me). During install it would crash with a kernel panic, so I used the noapic and nolapic parameters, and the install went well.

However, when it boots up, it would be stuck at "Saving VESA state" forever. I tried using recover mode, but it would crash as well. I know about editing "/etc/default/acpi-support" from "SAVE_VBE_STATE=true" to "SAVE_VBE_STATE=false," but I don't know how to do this without being able to boot into GNOME. Can somebody please give me some pointers with setting up linux on this horrible creation?

---

### Post by dmizer on 2006-06-25
if you can't even get a command line, the only thing i can come up with off the top of my head is by using a live distro of some kind, like ubuntu live or knoppix or the like.

that way you have read/write access to your install, but you don't have to be booted into the system to make the changes you need.  but VESA has to do with video, so you might try reloading with vga instead.

do you have a cli?  if so, you can just edit the file with nano:
```
sudo nano /etc/default/acpi-support
```
ctrl x to quit, and "y" to save.

---

### Post by intent on 2006-06-26
[QUOTE=dmizer]if you can't even get a command line, the only thing i can come up with off the top of my head is by using a live distro of some kind, like ubuntu live or knoppix or the like.

that way you have read/write access to your install, but you don't have to be booted into the system to make the changes you need.  but VESA has to do with video, so you might try reloading with vga instead.

do you have a cli?  if so, you can just edit the file with nano:
```
sudo nano /etc/default/acpi-support
```
ctrl x to quit, and "y" to save.[/QUOTE]

I've also tried a live distro (only had the older Ubuntu LiveCD with me), but it said the hard drive was inaccessable and I couldn't enable it. I'm not too good with the whole Linux command line or mounting thing.

How would I go about "reloading with vga?"

EDIT: I figured out what a cli is :) Command line.

Also, I managed to use nano and change SAVE_VBE_STATE, but now, after the graphical boot screen is over, I get a non-blinking cursor on a black background.

I tried adding VGA=771, but now it blinks a few times and then hangs again. I also can't go into a terminal with Ctrl-Alt-F1.

---

### Post by intent on 2006-06-26
Any more help? I'm still stuck here...:(

---

