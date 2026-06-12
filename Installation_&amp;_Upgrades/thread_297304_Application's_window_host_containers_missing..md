---
title: "Application's window host containers missing."
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by g_rael on 2006-11-10
Have been upgraded to edgy since it came out.
Running a GeForce FX 5200 Nvidia with DVI, SVGA and SVideo outputs.
Managed to finally get the SVGA AND the TV outputs running, and then managed to drop the TV, but send out on the DVI (seperate picture)
All with modification of the xorg.conf file.

My problem began during fiddling in an attempt to get another card going, and to run even more outputs. couldn't get it working, and then had to get back my twin monitor (DVI+SVGA) working config.

During the process, at some stage I think I ctrl/z zapped something that I thought had hung while I had X shutting down via the ctrl/alt/backspace X shutdown command.

Now, whenever I go into X, either of my screens only show application windows top left alligned, and in place of the top ubuntu "applications~places~system" task bar.

What do I edit, or reinstall to get it back ?
Also, my workspace icons at bottom right have vanished.

Windows with the oblique parallel "stretch" lines at bottom right still respond to mouse drag size changes, but the normal edge resize sense is missing. I get application mouse icons within the application if programmed, but at the transition to clean desktop, there is no resize icon, not will the window resize.

Because the windows overwrite the top left title bar to the width of the application, I lose my normal ubuntu task bar icons at the top.

Any hints please ?:confused:

---

### Post by g_rael on 2006-11-10
Further, Don't know what this means, but I also have these symptoms:

My other (non admin) logins have the proper window container, i.e. rezizable, minimise, maximise, close buttons in their frames.

Also, my admin login doesn't bring up the ubuntu login/logout noises, my other logins do !

What am I missing ?

---

### Post by g_rael on 2006-11-18
Finally found out how to purge my bad session entry:

Delete your:
   /home/"user"/.gnome2/session
text file.

hold ctrl and alt down, press backspace.
log in to your normal gnome session.

grrr ! it is actually in the Ubuntu help section that's loaded with the install !:-#

---

