---
title: "classic ubuntu desktop broken"
date: 2011-05-22
forum: Installation &amp; Upgrades
---

### Post by rtimai on 2011-05-22
My Unity desktop (running Compiz) is working fine, but I lost my ability to log into Ubuntu Classic (running Metacity.)

Everything was working fine until I decided to install additional themes in Natty 11.04. I wanted to install Gnome themes because their conservative look appealed to me, so I installed several Gnome theme packages using Synaptic Package Manager which listed them in an organized way.

As close as I can remember what I did:
Shortly afterwards I noticed an "Adwaita" theme in the Appearance applet, but which displayed an error, "This theme will not display properly because the Adwaita theme is not installed." I could find no Adwaita theme package to install. Selecting the Adwaita theme in Appearances caused the Remove button to be grayed out -- so I couldn't remove it. 

Researching the Adwaita name, I learned that it was the default theme for Gnome3 -- which I didn't intend to use. Using "locate" I found only two "libadwaita" files under /usr/lib/, with an .xml and .so extension, which I "sudo rm'd" and followed instructions to delete the phantom Adwaita theme by running gksudo gnome-appearance-properties.

Shortly after that I found that logging into Classic Ubuntu displayed a "hybrid" desktop with both metacity and compiz elements for a few seconds, then gnome-panel disappeared leaving the Unity launcher and panel. 

It seems Gnome3 themes may have had something to do with this, breaking some systems by overwriting some window settings and breaking dependencies. This bug posting may provide a clue: 

[https://bugs.launchpad.net/ubuntu/+source/gsettings-desktop-schemas/+bug/734563](https://bugs.launchpad.net/ubuntu/+source/gsettings-desktop-schemas/+bug/734563)

WORD OF WARNING, don't try to remove any phantom Adwaita themes!
Wait for a fix.

---

### Post by rtimai on 2011-05-22
Hey, what do you know, I found that if I select Ubuntu (Safe Mode) on login, I get the Classic Ubuntu desktop! Exactly as I arranged it, but probably with video acceleration disabled. I don't get the "You are running with reduced video capability..." announcement. Does this provide a clue for fixing the Gnome3/Advaita theme-related problem? If anyone has an idea, I would be more than glad to listen.

---

### Post by rtimai on 2011-05-22
I guess this is a one-man thread. I found my fix. I had used Ubuntu-Tweak to back up all my settings while my Unity installation was still fresh. I restored my Gnome settings, and was once again able to log into Classic Ubuntu. 

Thank you Ubuntu-tweak Team!!!! This is a problem that seemed to have no solution but a new clean install. A configuration backup saved the day! Maybe more like six months (till Oneiric.)

---

