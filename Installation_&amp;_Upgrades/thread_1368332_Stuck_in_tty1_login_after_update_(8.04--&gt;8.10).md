---
title: "Stuck in tty1 login after update (8.04--&gt;8.10)"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by mrmagpie on 2009-12-30
Just ran in to a very strange issue while upgrading to 8.10 on my Dell Studio XPS. I ran the update from the Update Manager. The process went smoothly, but after the automatic reboot I ended up in the tty1 login. I have absolutely no idea what I'm supposed to do to get back to my regular interface, or what any of it means. I ran the exact same process on my (much older) Inspiron 8600 a little while back and there were no problems at all - certainly nothing like this. Does anyone know what I should do? :confused:

I'm not sure if any of this is related at all, but I just installed Ubuntu for the first time on that system this morning, and I noticed that the screen resolution was quite small. After resizing it to something more appropriate, however, the orange coloration on my desktop turned green, I was no longer able to run Normal Visual Effects on the desktop, and when I ran the Hardware Test the graphics portion failed.

---

### Post by mrmagpie on 2009-12-30
The output from my system as it boots looks something like this:

Loading, please wait...
19+0 records in
19+0 records out
kinit: trying to resume from /dev/disk/by-uuid/b22a70f4-1bc1-457c-b711-473e1e5c31e5
kinit: No resume image, doing normal boot...

Ubuntu 8.10 [user] tty1


It seems like this might have something to do with an error that takes place when a graphics card is installed on 8.10. Considering the issues with graphics I was having prior to the update, could this be the problem? (I run an ATI Mobility RADEON HD 4670 - 1GB)

Edit: Starting/Re-Starting GNOME Display Manager has no effect.
Edit2: Attempting to edit xorg.conf with gedit results in "(gedit:5763) Gtk-WARNING **: cannot open display:"

---

### Post by mrmagpie on 2009-12-30
Bump.

Any ideas on anything I could try? I've been reading up on random threads all the way back from 7.10 that seem to deal with something like the same problem, but it's difficult to know which of these suggestions I should be following, since I don't really understand what's happening.

---

