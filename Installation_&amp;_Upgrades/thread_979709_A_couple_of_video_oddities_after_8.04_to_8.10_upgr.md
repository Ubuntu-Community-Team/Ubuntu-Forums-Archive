---
title: "A couple of video oddities after 8.04 to 8.10 upgrade"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by Peter Bell on 2008-11-12
As posted in the poll thread, the 8.04 to 8.10 upgrade process ran perfectly.  However, I have a couple of problems with video (I am using an old Viewsonic LCD, via DVI):

1) In 8.04 I had been using a 'Left rotated' screen at 1280x1024.  For some reason, 8.10 won't allow me to select Left or Right rotation at this resolution - only 'Normal' and 'Upside down' are offered.  If I select a lower resolution (1024x768), then the left and right options are offered.  However, my old screen won't work at lower res (I had to find another lcd in order to recover my system).

2) The other oddity is with the screensaver (I use Sky rocket).  In 8.04 this ran very smoothly, with rocket trajectories and star bursts being displayed in detail.  With 8.10, I'm getting a very jerky display which only updates about once a second.

I wonder whether these two problems are related in some way - perhaps the correct video driver isn't being used.  However, I'm not sufficiently knowledgable in Linux to know whet the driver should be, how to check what is installed, and how to change it.

---

### Post by Peter Bell on 2008-11-12
Okay, a little bit of investigation reveals that my machine is using the GMA945 video core, integrated into the Intel i945GM.

So, should I expect the two problems I am experiencing with the 8.10 upgrade?

I guess, more importantly, how do I return to the performance/features which I enjoyed under 8.04?

Can anyone help me?

---

### Post by Peter Bell on 2009-03-12
After much fiddling, on and off, I have solved the issues I had with i945 video after the 8.04 to 8.10 upgrade.

The things which I believe had an influence were:

1) I obtained the 'Intel' driver from [http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu](http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu)

2) I ensured that the i810 driver was removed from the system: 'sudo apt-get remove i810' (or something like that).

3) I reverted to the default content for /etc/X11/xorg.conf: sudo dpkg-reconfigure -phigh xserver-xorg

This brought me back to a full performance video, as I had come to expect under 8.04.  This is most clearly demonstrable by observing the Skyrocket screensaver.  It now updates at several frames a second, whereas I had been seeing frame updates of less than one a second.  Also, I can once again rotate the screen by 90 degrees.

Following the changes, I selectively re-introduced customisation into xorg.conf.

Anyway, for all I had read about video performance issues in 8.10, and how these could not be overcome because it was tied in to XAA -> EXA changes, and XAA was simply no longer usable with 8.10, it seems to me that this may not be the real issue.  Having said that, I'm not sure what acceleration technology I'm now using (perhaps UXA???)!

---

