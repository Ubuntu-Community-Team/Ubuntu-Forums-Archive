---
title: "Starting hotplug subsystem frozen"
date: 2005-11-06
forum: Installation &amp; Upgrades
---

### Post by annag on 2005-11-06
sorry if my question has been already discussed elsewhere but I've deeply searched for it and not found any practical solution to my problem: during reboot the system hungs up saying "starting hotplug subsyem" and nothing else happens. If I start in recoovery mode I see a message saying something like "... PCMCIA ... unable to apply power ..." (but the scroll is very fast so maybe that's wrong) and after that a continous scrolling with this phrase "azx_get_response timeout" with no way to stop it unless a full switch-off of the system (a notebook Packard Bell Easynote W3420). 

cheers, annag

---

### Post by annag on 2005-11-07
is there any guy with the same problem, as described in previous post ?

---

### Post by gyrev on 2005-11-12
Hi

I have an EasyNote W3281, and I'm still fighting to make it work.

up to now, here are the issues I've found:

1- the "azx_get_response timeout" seems to be caused by the sound chipset, you have to blacklist it, then reconfigure alsa. but to blacklist it, you have to boot with a live cd, I choosed Knoppix 4.0. now, see problem 2

2- it looks like there is a problem with the integrated Lan chipset so have to boot knoppix with "knoppix nodhcp"
then mount hdx where you have installed ubuntu, and add **snd-hda-intel** at the end of /etc/hotplug/blacklist
by the way, you can change /etc/X11/xorg.cong so that your X server can start: replace driver "ati" by driver "vesa" in the section "device"

now you can reboot on ubuntu. acpi causes problems so you have to remove it (with synaptic for example)

yet I still don't know how to access my lan... still stfw !!!

---

### Post by gyrev on 2005-11-22
OK, so just in case someone has a problem with his PackardBell EasyNote W3281, or any of the W serie I suppose, you will find [here]("http://doc.ubuntu-fr.org/materiel/liste_portables/packard_bell/easynote_w3281") a how-to to configure it. it's in french, but here's a short summary:

1- boot on knoppix to add snd-hda-intel to /etc/hotplug/blacklist
2- before installing ATI drivers, change Driver "ATI" to "vesa" in xorg.conf
3- compile 2.6.14.2 kernel, but check that ULI562x will be built as a module
4- install ATI drivers from ATI website
5- install synaptics drivers (for the touchpad)
6- compile RT2500 drivers for wifi (if they're not in the kernel)
7- still unsure: the realtek drivers installation for alsa... working on it...

keep tuned!

---

