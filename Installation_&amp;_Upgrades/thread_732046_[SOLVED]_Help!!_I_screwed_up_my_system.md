---
title: "[SOLVED] Help!! I screwed up my system"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by cmbcne on 2008-03-22
Newbie Alert!

I've been running Gutsy Kubuntu for a few weeks.  I know just enough to be dangerous :wink:

A week or so ago I installed KDE4 to check it out, but I ran out of time to devote to playing with it so this week I removed it.  I had also - somehow - managed to install the whole "Edutainment" group of apps.  I removed them as well.  Somewhere in all of this, I removed KDE3 as well.  Yikes!  

Luckily, I noticed the removal during the same session because I got an error at one point saying something couldn't be removed because it was in use (or words to that effect).

I attempted to re-install all the KDE parts before rebooting ( I think I got it all).  Upon reboot, however, the initialization process (all the white writing on black screen showing all the things being started) ended at:
*  Running local boot scripts (/etc/rc.local)

It just sat there, so I typed "startx" and the GUI load began, but put me through the same questions as on the first start (Time Zone, Preferences, etc), but finally loaded what seemed like the desktop I had before this mess happened.

Now, when I reboot, it still stops at the same place and I have to type "startx" to get it to load.

I need to know how to fix it.  I know the above isn't enough by itself to help you diagnose, so please respond and I'll reply with the condition of any files you think might be involved.

---

### Post by forestpixie on 2008-03-22
not sure if this will helpbut you could try reinstalling kubuntu desktop

sudo aptitude install kubuntu-desktop

But I know little about the ins and outs of kubuntu

---

### Post by cmbcne on 2008-03-23
> **forestpixie said:**
> not sure if this will help but you could try reinstalling kubuntu desktop

sudo aptitude install kubuntu-desktop

But I know little about the ins and outs of kubuntu

Thanks for the reply.  Would reinstalling the kubuntu desktop also reactivate the automatic loading of X11 as well?  Right now I'm stuck at a CLI and have to type "startx" to get X and KDE to start.  When I log out I have to do a "sudo shutdown now" command to turn off the 'puter.  

All the pieces seem to be there, it's just the automatic loading that's not working.

---

### Post by cmbcne on 2008-03-24
Hi, forestpixie (fascinating nym)

I got busy and only tried your suggestion last night.  Voila -- it worked!!

Thanks for the idea.  You da man (or gal, as the case may be) <grin>

---

### Post by forestpixie on 2008-03-24
Definitely a man - glad it helped :)

---

