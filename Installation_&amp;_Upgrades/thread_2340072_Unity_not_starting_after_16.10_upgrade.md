---
title: "Unity not starting after 16.10 upgrade"
date: 2016-10-15
forum: Installation &amp; Upgrades
---

### Post by Gridwalker on 2016-10-15
I appear to be stuck in a login loop, as Unity does not seem to be starting.

After upgrading to 16.10, I booted into the LightDM login screen and found that any attempt to log in caused a screen of garbled text to flash up for a moment before dropping me back into LightDM. Same response with the guest login. I have been through all of the fixes suggested for similar problems with previous releases, but so far none of them work.

These "fixes" include (but are not limited to) :
Reinstalling lightdm
Switching lightdm for gdm
Reinstalling nvidia-current
Changing owner of .Xauthority
Logging into alternate desktop environments (gnome & unity 8 both fail)

I can usually power on my desktop and leave it on the login screen whilst I stream media to my tablet via the Plex server I have installed. Testing has revealed that this service has also stopped working, so it looks like there is more to this than a simple login fault.

Cat ~/.xsession-errors reports a fatal error due to missing resources on X server ":0" ... I am running a dual monitor setup and my second monitor stopped working after the upgrade, which made me suspicious. I tried trashing the latest version of xorg.conf, just to see if it was looking for a resource that it couldn't initialise. No luck.

Journalctl -xe reports that unity-panel-service is failing to load a backing service, and other lines in the report suggest that BAMF has failed. There are frequent references to unity failing due to dependency issues, but these messages are not specific and attempting to fix broken backages through the GRUB recovery mode reports that there are no problems. Unfortunately, I am having to type this from my phone, so it is hard to give additional detail.

All of this is just shooting in the dark though. Does anyone have a clue what is causing this?

My Boot Info Summary can be found here : [http://paste.ubuntu.com/23329398/](http://paste.ubuntu.com/23329398/)

---

### Post by Gridwalker on 2016-10-16
Bump ... I have some fairly urgent university assignments to do, so I am a little desperate.

Does nobody have any suggestions?

---

### Post by howefield on 2016-10-16
I'd probably try purging the nvidia drivers to get the system using the nouveau driver and see if that boots/logs in.

If it didn't I'd reinstall, only because of the "fairly urgent university assignments" on the basis that 18 hours after your initial post you're no further forward and less than an hour would normally take care of a new install ;)

---

### Post by Gridwalker on 2016-10-16
I have tried purging Nvidia drivers, but no joy. 

Unfortunately, reconfiguring my system as it was will prove to be a bit more work than a 1 hour reinstall (otherwise I wouldn't be bothering with this) ... I would really rather try to find a fix first.

---

### Post by Gridwalker on 2016-10-19
I gave up and chose to reinstall ... as I suspected, the 16.10 installation media fails to load.

The last time I had to do a clean install, I had to go back to 15.04 and then upgrade from there. I am having to do the same now ... this is going to take a long time.

Please mark this as fixed, but I consider it a complete failure  If this happens the next time I upgrade (and this is far from my first failed upgrade over the years) then I am switching distros.

---

