---
title: "Broken gstreamer affects all gstreamer apps"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by 0xdeadc0de on 2008-10-22
After some updates last night nothing that relies on gstreamer works properly. Totem, rhythmbox, gmusicbrowser, and others I'm sure. They all fail with error. I don't know if it's related but the volume control applet in gnome crashes every time it starts as well now.

```

ERROR: Caught a segmentation fault while loading plugin file:
/usr/lib/gstreamer-0.10/libgstlibvideo.so

Please either:
- remove it and restart.
- run with --gst-disable-segtrap and debug.
Error re-scanning registry , child terminated by signal
Run 'rhythmbox --help' to see a full list of available command line options.

```


Anyone else getting this?



Temporary solution: remove or move libgstlibvideo.so (I removed it, reinstalled gstreamer packages, it reinstalled the file, all still crashed so I removed it again, they work now but I'm assuming with missing functionality)

---

### Post by plun on 2008-10-22
Yup, this bug discussed within another thread

[https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448](https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448)


No reaction yet and this bug is rather critical.

Complete messes up a Gnome desktop.

---

### Post by bakermiller on 2008-10-22
Hi, sorry for my two bits, but i don't think this above bug is related to this thread. I had this same problem as first post yesterday after making an update to GStreamer (libgstreamer0.10-0). Afterwards, nothing sound related worked. The panel volume-control was blanked-out with a red cross and my sound card was no longer recognized in the gui "sound" in system>>preferences, and no sound whatsoever came out of my machine.

I got it to work, but i was too frustrated, so i reverted back to a previous backup. Sorry i can't help much more, just saying it's more than just Libvisual.so...

Now auto-Update is asking me to update this GStreamer and I really don't want to go through this again.....so i'll wait it out a few days....

---

### Post by plun on 2008-10-22
In this case it is this bug. The bug is also confirmed and classified with high importance .

Users now upgrading to this bug will see a complete mess when
Gnome-settings-daemon halts.   

[https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448](https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448)

---

### Post by bobnutfield on 2008-10-22
I can certainly confirm that todays updates (it's been two or three days since I updated), have completely borked gnome-settings manager.  Volume control is gone (though sound works), sound settings manager is gone, most panel appelts are gone, and the Ubuntu firefox theme is gone.  This has really created a mess on my laptop.  I read the bug report which instructs to remove libvisual, but that has not worked for me.

If a future update doesn't fix this mess, it's reinstall time.

---

### Post by alphacrucis2 on 2008-10-22
> **bobnutfield said:**
> I can certainly confirm that todays updates (it's been two or three days since I updated), have completely borked gnome-settings manager.  Volume control is gone (though sound works), sound settings manager is gone, most panel appelts are gone, and the Ubuntu firefox theme is gone.  This has really created a mess on my laptop.  I read the bug report which instructs to remove libvisual, but that has not worked for me.

If a future update doesn't fix this mess, it's reinstall time.

Could this be why Cheese has stopped working for me? VLC still good.

---

### Post by nanog on 2008-10-22
Its fixed if you used the ppa referenced here:

[https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448](https://bugs.launchpad.net/ubuntu/+source/libvisual-plugins/+bug/287448)

---

