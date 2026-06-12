---
title: "Re: Ubuntu Karmic Koala - white screen after login - possible fix"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by deusdiabolus on 2009-10-18
I felt I should post this because it will possibly help someone else.  

My system is a Dell Dimension 4600 with an Intel Pentium 4 2.66 GHz CPU and onboard video and audio, FSOR.

I installed the beta of Karmic Koala this morning (10/17) and when the system rebooted and I logged in, the screen went white and all I had was a cursor.  I tried rebooting, and I also tried recovery mode, and there was a listed fix here involving going into xorg.conf from a terminal and changing the display mode, but I didn't make any headway with these.

What I ultimately remembered was that you can load GNOME in failsafe mode at the login screen, so I tried that - and it worked.  Once the desktop loaded, I went into Compiz (because there was some information on Launchpad that suggested this might be the culprit) and disabled a few of the workaround options and also the Opacity, Saturation and Brightness option.  I also disabled xflux (a third-party app that adjusts the color temperature of your display based on the time of day) in the startup options.  When I logged out and logged back in, everything was still visible (there is a notable transparency problem, but it's mostly ignorable for now).

Hopefully this will help someone else.

---

### Post by zoli4290 on 2009-10-18
The source of the issue may be a PPA Intel driver. Try what is written in [http://ubuntuforums.org/showthread.php?p=8123326](http://ubuntuforums.org/showthread.php?p=8123326) .

---

### Post by deusdiabolus on 2009-10-23
I used Synaptic to uninstall xserver-xorg-intel-driver-2.4 and then installed xserver-xorg-intel-driver (2-2.9.0-1ubuntu2).  I also used the instructions in [this thread]("http://ubuntuforums.org/showthread.php?t=83973") to setup my display resolution (for whatever reason, the display settings initially refused to go higher than 1152x864 without me manually editing xorg.conf to specify 1600x900). Everything is nice and sharp now, but I'm still experiencing the issue with third-party plugins (such as Screenlets and Rainlendar) not having transparency ability (I don't have this issue with anything  such as the taskbars and drive icons on the desktop).  Anything third-party that would normally involve a transparent background appears with a blacked-out space where the transparency would be (including OSDs for things like Audacious).  I'm not sure what else to try - I'm guessing I'll stumble across it by accident before long, but I'm still hoping for more suggestions (I did add Driver - "Intel" to my xorg.conf in the appropriate place to see if that would do anything, but I don't think it has).

---

### Post by darius.k on 2009-10-25
Just wanted to report back. Had the same problem.
Removing the xserver-xorg-video-intel package and deleting my /etc/X11/xorg.conf file worked for me.

---

