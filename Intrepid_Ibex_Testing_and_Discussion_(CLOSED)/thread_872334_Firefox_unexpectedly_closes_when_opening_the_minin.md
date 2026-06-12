---
title: "Firefox unexpectedly closes when opening the mininova.org site"
date: 2008-07-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by suxenexus on 2008-07-27
I've been currently using Ubuntu Intrepid Ibex alpha 2(?).  I always check for updates.  But recently, Firefox just closes whenever I check mininova.org

Can anyone help me? :(

---

### Post by scragar on 2008-07-27
open firefox in a terminal and post feedback here(use code tags please).

---

### Post by dmizer on 2008-07-27
Moved this to Intrepid testing.  Thanks for helping out.

Close firefox, open a terminal and type:
```
firefox
```
browse to mininova and post the error message that appears in terminal after firefox crashes.

---

### Post by suxenexus on 2008-07-27
Here's what the log says:
```
(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(firefox:8189): Gdk-CRITICAL **: gdk_x11_colormap_foreign_new: assertion `xcolormap != None' failed

(firefox:8189): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Segmentation fault

```

I also remembered, it started happening when I update some Ubuntu repository.  Before firefox starts to close unexpectedly, the title bar was at first not at plain sight, then it displayed the Hardy Heron default theme (Human-clearlooks theme) instead of Intrepid Ibex default theme (New Human theme).  At that time, whenever I check mininova.org site, it would always close unexpectedly

---

### Post by ronacc on 2008-07-27
this is not intended to start a flame war , I use Firefox too but I also have Opera and mininova dosen't crash it and it has a builtin torrent client , so if you need to access mininova grab opera from their website the hardy .deb works fine with intrepid .

---

### Post by psyke83 on 2008-07-27
> **suxenexus said:**
> I've been currently using Ubuntu Intrepid Ibex alpha 2(?).  I always check for updates.  But recently, Firefox just closes whenever I check mininova.org

Can anyone help me? :(

Yes. It's very likely to be a bug in Firefox's "windowless mode", which causes crashes on many sites with flash content on the latest Flash 10 beta 2. It seems mininova.org uses some flash for advertising (which I only noticed after disabling Adblock Plus).

See my [PulseAudio howto]("http://ubuntuforums.org/showthread.php?t=866965")* and the specific post with instructions to test some patched debs [here]("http://ubuntuforums.org/showpost.php?p=5472028&postcount=33"). I'm 99% certain it will fix your issue (as I just confirmed it myself).

*This bug is not related to PulseAudio, so you're not required to follow  the howto itself (though I recommend it anyway).

---

### Post by Robertjm on 2008-07-28
I downloaded the update to FF3 last night and it seems to be crashing more than before so I'd be its not just that site.

Robert

---

### Post by BC7333 on 2008-07-28
Experiencing similar here but think the problem is being addressed already

[https://bugs.launchpad.net/ubuntu/intrepid/+source/seamonkey/+bug/218534](https://bugs.launchpad.net/ubuntu/intrepid/+source/seamonkey/+bug/218534)

---

### Post by psyke83 on 2008-07-28
> **BC7333 said:**
> Experiencing similar here but think the problem is being addressed already

[https://bugs.launchpad.net/ubuntu/intrepid/+source/seamonkey/+bug/218534](https://bugs.launchpad.net/ubuntu/intrepid/+source/seamonkey/+bug/218534)

I really doubt it - that bug is fixed already. The fix for this issue is contained in my earlier post (though 64bit users cannot use the new Flash 10 beta properly until nspluginwrapper gets updated to 1.1.0 or later).

---

### Post by rkstech on 2008-07-28
psyke83's post #6 fix has solved the problem on Ubuntu 8.04, FF3.0.1  on my sysem. ([http://ubuntuforums.org/showpost.php?p=5472028&postcount=33](http://ubuntuforums.org/showpost.php?p=5472028&postcount=33)) 

I am using flashplayer 10. This was crashing on many site randomly. 
This now fixed the problem.

Earlier I had used the flash 9 ( both from ubuntu and adobe). I had problem with the site [www.hulu.com](www.hulu.com). The problem was I was not able to escape from full screen properly when watching clips from the HD gallery. I had to restart X (ctlr+alt+bkspc).

Using the flash 10 solved the escape problem. But got into crashing problem.

With the above fix I am not seeing any crashes for last 4 hrs.

Thanks to psyke83

---

### Post by dmizer on 2008-07-29
> **rkstech said:**
> psyke83's post #6 fix has solved the problem on Ubuntu 8.04, FF3.0.1  on my sysem. ([http://ubuntuforums.org/showpost.php?p=5472028&postcount=33](http://ubuntuforums.org/showpost.php?p=5472028&postcount=33)) 

I am using flashplayer 10. This was crashing on many site randomly. 
This now fixed the problem.

Earlier I had used the flash 9 ( both from ubuntu and adobe). I had problem with the site [www.hulu.com](www.hulu.com). The problem was I was not able to escape from full screen properly when watching clips from the HD gallery. I had to restart X (ctlr+alt+bkspc).

Using the flash 10 solved the escape problem. But got into crashing problem.

With the above fix I am not seeing any crashes for last 4 hrs.

Thanks to psyke83

Please remember to thank psyke83 by clicking on the [img]http://ubuntuforums.org/images/buttons/post_thanks.gif[/img] icon appearing below post #6 :)

---

### Post by iGama on 2008-07-30
Thanks for the tip :)

---

