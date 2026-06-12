---
title: "Ubuntu upgrade 12.04 to 14.4 lightdm/gdm login fails"
date: 2014-08-28
forum: Installation &amp; Upgrades
---

### Post by jvcastle on 2014-08-28
So I've looked at the forums, and have tried most every thing I see, but can't get Ubuntu into graphics mode after upgrading from 12.04 to 14.04 on this machine (Upgrades on 3 others worked without a hitch).  I'm pretty sure its related to the dual Intel+Nvidia graphics.  Comments like "do a fresh install" aren'nt helpful.

This is a Dell XPS with Intel Graphics as well as a NVIDIA 540.  Nothing is plugged into the NVIDIA card (uses the HDMI port) - only using the laptop screen at the moment.  Using the 3.13 kernel

Plain boot brings up the centered "Ubuntu 14.04 screen with the moving dots but goes no further. Booting with "nomodeset" doesn't seem to change anything.   It never gets further, no networking, can't login remotely etc.  Power button is only option for a halt.

Oddly, if I bring it up in text mode (boot parmameter "quiet splash" replaced with "text") everything comes up to the command line fine.  At that point if I "sudo service lightdm start" I get a perfect graphical login screen at full (.i.e 1024x1280) resolution.  THEN after logging in, THREE "System Problem Detected" windows pop up - if I click on "Report a Problem" 3 times, I am left with the initial splash screen with the "ubuntu 14.04 LTER" in the lower left corner.  I am able to do a remote login.  I don't know where the "Problem reports" are stored - that might help...

Pertinant dmesg ilines include
init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory
init: gdm main process (936) killed by TERM signal
init: plymouth-stop pre-start process (1182) terminated with status 1

Is this a driver problem?  An X11 config problem?  

Where to from here?


Update:  After trying a ton of things, there didn't seem to be an easy way to fix this, and to save time (since I was able to bring the system up to command line), I "simply logged in, connected an external drive and copied all my apps and configuration files - and did an install from scratch.  One would think that an upgrade from a working system would result in a working system...

---

### Post by leonardo-rigutini on 2014-10-23
Hallo,
I have the same problem.. I upgraded from 12.04 to 14.04 and when restarted the screen goes black at login.
The dmesg output is:
...
[   30.133474] type=1400 audit(1414059141.942:17): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=829 comm="apparmor_parser"
[   30.623553] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory
...
[ 2041.099488] init: lightdm main process (1185) terminated with status 1
[ 2042.207793] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory

The output of lshw -c display is:

*-display               
       description: VGA compatible controller
       product: RV516/M64 [Mobility Radeon X2300]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-d7ffffff ioport:8800(size=256) memory:fd7f0000-fd7fffff memory:fd7c0000-fd7dffff

I tried to reinstall unity, xserver-xorg-video-radeon... nothing to do!!

suggestions?

---

### Post by Forbees on 2014-10-23
i'll be honest with you... i've been using ubuntu since 7.10 and on the many machines i've put it in i've never been able to upgrade without doing a clean install... something has always gone wrong for me. now i know this isn't the case with other people... but i just gave up letting it upgrade itself.... besides, a clean install always runs nicer

hopefully someone more knowledgeable comes by and gives you a real answer. even though i've been using ubuntu so long i'm no expert lol i still ask for help with everything :-p

---

