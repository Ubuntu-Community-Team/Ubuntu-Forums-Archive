---
title: "Kernel Upgrade Problems?"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by rhetor53 on 2008-07-27
I'm a pretty experience linux user (mostly fedora but going back to redhat 4.0).  Much of my configuration experience has to do with fedora, and I'm feeling lost fixing some of the recent problems I have with a recent ubuntu upgrade.  I've been using Ubuntu about 3 months on a laptop, and just a couple weeks ago, I switched to ubuntu for my home media server.  This computer runs mythtv (backend and frontend) and stores my audio collection.  I also stream radio from it.  I'm running ubuntu 8.04.1 with the nvidia glx drivers.  Other than that, it's a fully updated generic ubuntu box.

This last week, in the standard upgrades, I got a kernel update--2.4.26-20.  Immediately after the update, all my audio players stopped streaming audio.  Totem won't play locally stored playlists, giving a permissions error.  Totem is also configured as the plugin for firefox for m3u.  When I click on one of those, the player dims and I have to force quit. Both Amarok and Rhythmbox stopped working, as well.  I then rebooted the machine, and the whole reboot just hung on the "starting up" message.  No interface, just that message.  Wow!

So I was able to get to the grub menu and revert to kernel 2.6.24-19, but I still can't get audio players to work.  Audio works fine playing local mp3's, but both local and linked radio stations fail.

Questions:

1.  In ubuntu, how can I permanently revert to the older kernel?  If I just comment out the latest kernel in menu.lst, will that fix it?

2.  Any idea what's going on with my media players?  Neither totem nor rhythmbox will read my audio streams.  I can't even start Amarok.  It just fails to start with no error messsage.  (As a sidelight, I can't find trusty xmms anywhere for ubuntu. Only xmms2.  Am I missing something?)

3.  What the heck, overall, is going on here?  Is it the kernel that's hosed my system?  If so, why doesn't reverting to the old kernel fix it.

I'm sorry to lump all this into one message, but it seems all these problems started with the recent upgrade.  Everything worked great until two days ago.  Any help much appreciated!!

stumped

---

### Post by sdennie on 2008-07-27
If you've already gotten the -20 kernel, it means that you had the proposed repository enabled (It's not enabled by default).  This is essentially a beta testing repository so, though it's not common, things from proposed can break the machine.

I'm not sure how to fix your problems but, to avoid future problems from the proposed repository, you may want to disable it in System->Administration->Software Sources.

---

### Post by undecim on 2008-07-27
I've been having even worse problems with the upgrade. I'm running Hardy 64 bit and. My X server won't even work with the -20 kernel.

to answer your questions:

1: In you /boot/grub/menu.lst, there should be a line that says "default 0" change the 0 to a 2 and that will tell grub to load the third menu option (which should be your -19 kernel) by default.

2: I have no idea. Like I said before, my X server doesn't even work properly. I can only assume that the -20 kernel has some Audio/Video changes that are messing these things up

3: Like vor said, the -20 kernel is in the proposed repository, and although that means we get to try out cool updates sooner than most, we also run into problems with this.

For now, I'm just sticking with the -19 kernel.

---

### Post by zvacet on 2008-07-28
@ **undecim**

Boot in 2.6.24-19 and then go to the system>admin>software sources and uncheck proposed as **vor** adviced.After that go to the synaptic and in search box type **linux-image.** Find and delete 2.6.24-20.You should be fine after that.

---

