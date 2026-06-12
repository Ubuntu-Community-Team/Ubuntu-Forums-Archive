---
title: "Invisibly  windows decoration with compiz"
date: 2009-02-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by eyelessfade on 2009-02-10
I now have invisibly windows decoration with compiz. It works but I have to guess where the buttons are. Anyone know what happend. I just upgraded from 8.10 so I don't know if it ever worked :) I have a nvidia 8800 card. Direct rendering works fine.




Edit:
Fixed after update 11/2-09

---

### Post by vikrant82 on 2009-02-10
I too suddenly have this. I'd not call it invisible though. Its a whitish title bar and yes, its irritating.

---

### Post by kestrel1 on 2009-02-10
Any chance of a screen shot, not sure of the effect.

---

### Post by eyelessfade on 2009-02-10
tried, but I can't get a shot of it. when I take screenshot it becomes truly invisible :/

---

### Post by vikrant82 on 2009-02-10
Where are the close/minimize/maximise buttons!!???

---

### Post by kj74 on 2009-02-10
Bug in latest metacity package, downgrade if you want those back.

---

### Post by Vaun on 2009-02-10
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/327794](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/327794)

---

### Post by dr_kabuto on 2009-02-10
Bug report filed: [https://bugs.launchpad.net/ubuntu/+bug/327793](https://bugs.launchpad.net/ubuntu/+bug/327793)

---

### Post by vikrant82 on 2009-02-10
Downgraded and locked three packages to :
metacity-common_2.25.89-0ubuntu1_all
libmetacity0_2.25.89-0ubuntu1_i386
metacity_2.25.89-0ubuntu1_i386

Subscribed to 327794. 

Thanks!

---

### Post by Vaun on 2009-02-10
Yep.  

I also needed libmetacity-dev_2.25.89-0ubuntu1_amd64 for building Compiz.  The downgrade should hold the masses.

:)

---

### Post by klange on 2009-02-10
The precise issue is an assertion failure:

```
(gtk-window-decorator:5737): metacity-CRITICAL **: meta_frame_style_draw_with_style: assertion `style_gtk->colormap == gdk_drawable_get_colormap (drawable)' failed

(gtk-window-decorator:5737): metacity-CRITICAL **: meta_frame_style_draw_with_style: assertion `style_gtk->colormap == gdk_drawable_get_colormap (drawable)' failed

(gtk-window-decorator:5737): metacity-CRITICAL **: meta_frame_style_draw_with_style: assertion `style_gtk->colormap == gdk_drawable_get_colormap (drawable)' failed
```

---

### Post by tawmas on 2009-02-10
> **WindowsSucks said:**
> The precise issue is an assertion failure:

```
(gtk-window-decorator:5737): metacity-CRITICAL **: meta_frame_style_draw_with_style: assertion `style_gtk->colormap == gdk_drawable_get_colormap (drawable)' failed

(gtk-window-decorator:5737): metacity-CRITICAL **: meta_frame_style_draw_with_style: assertion `style_gtk->colormap == gdk_drawable_get_colormap (drawable)' failed

(gtk-window-decorator:5737): metacity-CRITICAL **: meta_frame_style_draw_with_style: assertion `style_gtk->colormap == gdk_drawable_get_colormap (drawable)' failed
```

Have you noted that in the bug report?

---

### Post by Streeterer on 2009-02-10
I can confirm this bug.

---

### Post by Vaun on 2009-02-10
- Fix longstanding crasher about colormaps.

OasisGames, maybe this fix has something to do with it?

---

### Post by ace214 on 2009-02-10
Sometimes I wonder if coders actually test their code when such stuff as this happens... Perhaps it is specifically a driver issue. I'm using the Radeon driver. Anyone else?

---

### Post by ThrobbingBrain66 on 2009-02-10
Intel here.  Besides that, it's been confirmed as an issue with the most recent metacity updates.

---

### Post by klange on 2009-02-10
> **Vaun said:**
> - Fix longstanding crasher about colormaps.

OasisGames, maybe this fix has something to do with it?
The issue is undoubtedly [revision 4092](http://svn.gnome.org/viewvc/metacity?view=revision&revision=4092).

---

### Post by Vaun on 2009-02-10
I just mentioned this on the compiz dev channel.  I'm looking through the 7144 lines of code in gtk-window-decorator.c to see something, but I don't know  enough to figure this out.  Maybe crdlb will have some luck.

---

### Post by meborc on 2009-02-11
> **ace214 said:**
> Sometimes I wonder if coders actually test their code when such stuff as this happens... Perhaps it is specifically a driver issue. I'm using the Radeon driver. Anyone else?

yeah... a simple test could have shown the mistake... but i guess they can't test everything, or we would be a few years back in the development... and that's what we are - to test, right :)

nvidia 8600M GT with 180 driver... same issue

---

### Post by cabernet54 on 2009-02-11
I have solved this issue with emerald windows theme.
:guitar:

---

### Post by klim8 on 2009-02-11
Latest updates solved the problem

---

### Post by biasquez on 2009-02-11
which update? problem isn't solved for me.

---

### Post by ThrobbingBrain66 on 2009-02-11
> **biasquez said:**
> which update? problem isn't solved for me.

Fixed here too.  Have you restarted yet? Logging in and out may work too.

---

### Post by klange on 2009-02-11
> **ThrobbingBrain66 said:**
> Fixed here too.  Have you restarted yet? Logging in and out may work too.

Nothing on the Metacity side would have fixed this, and our fix hasn't gone out to the branch Ubuntu is using yet - so unless they beat us to it, the problem being fixed is illogical. (As I don't use Compiz/gtk-window-decorator from Ubuntu's repos, I wouldn't actually know - can someone check the revision log on compiz*?)

**e**: Fix just went out to compiz-legacy / compiz-0.8.0

---

### Post by scaine on 2009-02-11
Sorry - it's late here, so I haven't read the bug report yet, but I can confirm that I had this yesterday (Tuesday 10th) on my Intel based laptop, but as of today (Wednesday 11th), my main Nvidia 6800 based PC is fine.

So, it's either Radeon/Intel specific and doesn't affect Nvidia, or today's updates have fixed the issue.

I'll post again tomorrow.  It's nearly 1am here and I'm gonna get me some shut-eye...

---

### Post by Vaun on 2009-02-11
OasisGames,

mvo pulled crdlb's patch earlier this morning and pushed a git snapshot of the compiz 0.8 branch.  The fix is in.

compiz (1:0.7.9+git20090211-0ubuntu1) jaunty; urgency=low

  * build from the 0.8 git branch
    - fixes focus problem (LP: #274407)
    - fixes problem with latest libmetacity decoration (LP: #327793)
    - enable new gnomecompat plugin by default
  * debian/patches:
   - updated 013-add-cursor-theme-support.patch
   - updated 018_use_metacity_settings.patch
   - updated 029_default_options
   - updated 035_ignore_workspaces
   - updated 037_fullscreen_stacking_fixes.patch (mostly merged upstream
     just the move plugin changes remain)
   - dropped 027_default_to_gnome_terminal
   - dropped 040_resolve-animation-fade-conflict_from_upstream.patch
   - dropped 047_no_display_compiz_desktop.patch
   - dropped 048_from_git_fix_placement.patch
   - dropped 050-scale-keybinding-toggle.patch
   - dropped 051-new-kde4-plasma-api.patch

 -- Michael Vogt < [email]michael.vogt@ubuntu.com[/email]>   Tue, 10 Feb 2009 10:39:03 +0100

---

### Post by DouglasAWh on 2009-02-13
So, the last update was a day ago, but I am still having this issue.  Where does it stand at this point?

---

### Post by hype on 2009-02-14
Same for me.

Justed realised playing a video file instantly crashes compiz, and its 100% reproduceable.
Only problem is that it also happens if i disable "video" plugin.

If not, simply clicking on a minimize button from any window will cause compiz to seg fault.

---

### Post by scaine on 2009-02-14
Fine here now too, although stupidly, I installed Shiki-Colours theme from gnome-look at around the same time, so I'm not absolutely sure what's fixed the issue.

Compiz video playback is fine here too.

---

### Post by DouglasAWh on 2009-02-15
This appears to be fixed for me too!  Now I need to fix that audio input that works in 8.10...

---

