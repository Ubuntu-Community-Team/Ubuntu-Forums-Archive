---
title: "Edgy LiveCD Xserver not working"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by eq235 on 2006-10-28
Problem with Edgy Eft Live CD: the cd won't boot up; it says that the x-server is not configured properly. I've tried various options, including 'safe mode,' as well as different resolutions, but nothing has worked. This is on an Dell Inspiron 9400 with GMA 950 and resolution of 1440x900. I really would like to get this working, so any advice is appreciated. Thanks!

---

### Post by jerrylamos on 2006-11-04
Edgy Eft xserver not working, i.e. fails to start.
blank screen with CDLive.
IBM NetVista Pentium 4 with 512MB
Intel 82845G graphics controller
Sony Multiscan 15sf monitor

At blank screen:
Ctrl-Alt-F1, cat of /var/log/Xorg.0.log:
EE: I810(0) no video Bios modes for chosen depth.
EE: screens found but none have a usable configuration.

sudo dpkg-reconfigure xserver-xorg
driver i810 (vesa gets the same results but slower)
use kernel framebuffer (yes)
set memory to 65536 as seen by Windows XP Professional on this system
select 1024x768,800x600,640x480
select dbe as well as the other options
color depth 16 (Windows XP uses 24 on this equipment, or is it 32). Edgy xserver won't run at any higher depth.

startx and gnome comes up in 648x480. Bummer. System-Preferences-Screen Resolution only shows 640x480, not the other modes shown in xorg.conf 1024x768,800x600

I'm pretty rusty on line mode commands but I could give a shot on anything else anyone would like to know or have me try.

My guess is that Edgy can't find the memory for the display adapter. Windows XP gives the memory addresses which I don't know how to get Edgy to use.

Is there a driver that matches Intel 82845G available? where?

Thanks much, I'm not about to use Edgy this way.

---

### Post by jerrylamos on 2006-11-06
Found a fix someplace in launchpad (I can't find that entry again).
The Intel 82845G chipset on a Dell machine had a Bios setting of 1024KB shared video ram.  The person posting the entry had changed it to the max 8192KB which fixed the problem.

Same fix worked with the IBM Net Vista 8303-SB2.  Hooray for the forums.

I spent about a week thrashing around with dpkg-reconfigure xserver-xorg to little avail.

If anyone's watching these forums, I'd suggest a sticky note entry for anyone with a Intel 82845G to check their bios shared video ram before even bothering to try to boot the Edgy Eft CD.

Thanks much to someone.

---

