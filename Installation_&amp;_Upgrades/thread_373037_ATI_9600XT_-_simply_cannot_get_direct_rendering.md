---
title: "ATI 9600XT - simply cannot get direct rendering"
date: 2007-02-28
forum: Installation &amp; Upgrades
---

### Post by baobab68 on 2007-02-28
Hi all

I've been trying for 3 days now to convince Edgy to give me direct rendering on my 9600XT.

I initially built my PC about a month ago and fairly quickly got Beryl and XGL to do direct rendering, using the fglrx driver (I think I was using the latest ATI one, not the one from the Ubuntu repos). fglrx was giving me much faster framerates than the open source radeon driver.

At that stage the build was just a test to see if I liked using Linux on a day to day basis. Turns out I did like it, so I rebuilt my machine on a larger hard drive.

Since that rebuild I just cannot get direct rendering working. Beryl and XGL are alive and work "pretty well" but glxinfo returns "direct rendering: no". Totem-gstreamer plays videos pretty well but they become choppy if I maximise the window.

I've tried the Ubuntu repo version of the fglrx driver and the latest ATI one. I've installed them by following how-to's, I've installed them using the excellent "envy" script, all no good.

Anyone got suggestions as to something I've missed? I would post my xorg.conf and my startxgl.sh but I'm in the office at the moment with no access to my home PC.

bao

---

### Post by baobab68 on 2007-03-02
A followup. I fixed it. Sort of.

It seems that direct rendering isn't actually necessary to get decent framerates from Beryl and video playback apps.

Here's what I did:

- took a backup copy of my xorg.conf
- removed the fglrx using Synaptic (there are several how-to's on this subject)
- used the oft-quoted dpkg xorg reconfigure command to completely re-write my xorg.conf file
- ran the 'envy' script to download and install the latest ATI driver (Alberto - that script is an amazing contribution to the Linux community)

I now am getting excellent frame rates from Beryl and video apps. I can blur entire transparent windows when dragging them, which I never could before. And my OpenGL screensavers run like the clappers now!

One happy camper here. Sorry my above description is a little sketchy on the detail. I've been trying to get this working for days now, time to go actually *use* my system for something productive!

I've yet to try any 3D games but that's not really my focus.

I guess it boils down to "direct rendering isn't everything". I have sort of formed the opinion that you actually can't get direct rendering with an ATI card and XGL, but it doesn't seem to matter.

Woo-hooo!

bao

---

