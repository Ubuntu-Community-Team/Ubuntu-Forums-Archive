---
title: "[SOLVED] ATI/AMD Proprietary FGLRX driver &amp;amp; tvtime"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by smolty on 2008-11-01
Just upgraded to Ibex from Hardy where everything ran fine, specifically desktop effects (with AWN) and tvtime. Since the upgrade to Ibex the only way to get desktop effects is to install the ATI/AMD proprietary driver. Only problem is that this then stops tvtime from running, if I deactivate the driver through 'Hardware Drivers' then tvtime works again. Terminal gives me the error message: 

> Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/smolty/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

The website it quotes doesn't appear to be too up to date, as in last modified 2005!! Plus bit of a noob so haven't tried anything from there.
Just seems strange that everything worked so perfectly on Hardy plus tvtime is working on Ibex until the driver install.  I guess the solution in an alternative drive to the proprietary one but i dont seem to be able to find anything. 

Any help would be massively appreciated!!!!!!!!!

---

### Post by Petez4 on 2008-11-17
To make TvTime work you need to set the way ATI overlays video.
Run the command:
  sudo aticonfig --overlay-type=Xv
And restart. XVIDEO should work now so that you don't get the "No XVIDEO port" error.

---

### Post by Daverobb on 2009-08-04
Saw this post and wondered if anyone would be monitoring it --  

did as above but received this message about the overlay support:

```
sudo aticonfig --overlay-type=Xv
[sudo] password for dave: 
No layout section was found in the file: '/etc/X11/xorg.conf'.
Please run 'aticonfig --initial' first or modify your configurationfile manually and run aticonfig again.
aticonfig: parsing the command-line failed.
dave@dave:~$ sudo aticonfig --initial
Found fglrx primary device section
 Unable to find any supported Screen sections
dave@dave:~$ sudo aticonfig --initial
Found fglrx primary device section
 Unable to find any supported Screen sections

```

---

### Post by smolty on 2009-08-04
I can't remember how I sorted my system out originally, I think I just got rid of desktop effects. What I do know is that 9.04 Jaunty doesn't seem to have any of the same problems. Not sure what distribution you are running but it might be worth looking at Ubuntu 9.04 if you aren't already running it.

---

### Post by Mark Phelps on 2009-08-05
Didn't catch which video chip/card you're using, but if you upgrade to 9.04 and you're using an ATI chip/card, unless you're using one of the newer HD 3x or HD 4x chips/cards, you won't be able to use fglrx.  AMD/ATI dropped support for the "older" cards ending with Catalyst 9.3, the newer drivers won't support the older cards, and the older drivers (9.3 and prior) won't work in 9.04.  You'll be stuck using the open source driver.

If you DO upgrade and you have one of these older chips/cards, don't try to force an fglrx installation.  If you do, you'll hose up your video bigtime.

---

### Post by vento1996 on 2009-11-08
Thanks to this topic i solved my problem with no reaction on lid close of my dell studio 1537 with installing radeonhd package from synaptic and latest driver from ati official site.
You are great! =)

---

