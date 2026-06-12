---
title: "Compiz needs to play nicely with others"
date: 2008-06-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Prosthetic Head on 2008-06-02
Compiz needs to be made to stop interfeating with other OpenGL apps if it is to be on by default IMHO.
It currently makes other OpenGL apps run slowly, show artefacts and crash on my nVidia system. It also interfears with full screen mode on some apps which arn't using OpenGL (eg wesnoth)
I'm not sure what the problem is, but i think it neeeds to be fixed.
Thanks :)

---

### Post by Ashrael on 2008-06-02
I do agree.. I think it should turn itself off when i start a 3d game, no need for desktop effects when i am gaming...
But I do not think you should post this here... compiz-fusion.org seems to be the place ;)

Greetz

---

### Post by 23meg on 2008-06-02
Keyword: DRI2.

---

### Post by Luke has no name on 2008-06-02
> **23meg said:**
> Keyword: DRI2.

Is that a replacement for Compiz? A module? Something different?

I googled a little but didn't fine a clear explanation.

OP: Yes, Compiz should not be active by default if it messes up other applications!

---

### Post by 23meg on 2008-06-02
DRI stands for [Direct Rendering Infrastructure]("http://en.wikipedia.org/wiki/Direct_Rendering_Infrastructure"), and [DRI2]("http://wiki.x.org/wiki/DRI2") is the recent rewrite of that component which fixes some (otherwise unfixable) problems with video overlays and OpenGL.

More info: [http://hoegsberg.blogspot.com/2008/03/i-just-committed-last-bit-of-dri2-work.html](http://hoegsberg.blogspot.com/2008/03/i-just-committed-last-bit-of-dri2-work.html)

---

### Post by RAOF on 2008-06-02
> **Prosthetic Head said:**
> ...
It currently makes other OpenGL apps run slowly, show artefacts and crash on my nVidia system. It also interfears with full screen mode on some apps which arn't using OpenGL (eg wesnoth)
I'm not sure what the problem is, but i think it neeeds to be fixed.
Thanks :)

I don't see these problem on my nvidia system, and I've been playing plenty of games with Compiz, both in wine and natively.  If it's not some unrelated problem it'll be a problem in the nvidia drivers.  Compiz has plenty of bugs, but it exposes many, many more driver bugs than it has itself :).

> **Ashrael said:**
> I do agree.. I think it should turn itself off when i start a 3d game, no need for desktop effects when i am gaming...
...

Welcome to the wonderful world of "unredirect fullscreen windows", aka "Don't composite fullscreen windows".  Available in System->Preferences->Advanced Desktop Effects (Core options).  I'm not sure if that's on by default now, but it used to expose a bug in gnome-screensaver's screen locking technique, so it might not be.

> **Luke has no name said:**
> Is that a replacement for Compiz? A module? Something different?
...

DRI2 is the replacement Direct Rendering Interface protocol (In simple terms: how X drivers can talk directly to the video card).  DRI2 basically makes it possible to fix all the X/driver limitations we currently have.  It's not quite the same as 'redirected direct rendering', but it's a part of the implementation.

---

### Post by | MM | on 2008-06-03
Metacity is still the best option for me in a number of cases.

Smooth scroll in both Firefox and Opera is much smoother in metacity.  In compiz its jerky.  Flash is not OpenGL hardware accellerated in Compiz while it is in metacity.  ANd Google Earth is pretty much always smooth in metacity, while in Compiz its quite spluttery.

SO yes, compiz does need to play nicer/better with some apps in some cases.  But i fear that even with Xserver changes like DRi2, we will still be waiting on gfx card vendors (nvidia in my case) to update their binary  drivers.

---

### Post by RAOF on 2008-06-03
> **| MM | said:**
> Metacity is still the best option for me in a number of cases.

Smooth scroll in both Firefox and Opera is much smoother in metacity.  In compiz its jerky.  Flash is not OpenGL hardware accellerated in Compiz while it is in metacity.  ANd Google Earth is pretty much always smooth in metacity, while in Compiz its quite spluttery.

Is flash *really* OpenGL accelerated under metacity?  If it is, it will still be accelerated under Compiz.  There is a (fairly small) unavoidable overhead involved in compositing, and Compiz effects can be pretty much arbitrarily GPU intensive, but on my nvidia card (7600go), I've never found Compiz (while not performing effects) to make a noticable performance hit in the 3D apps, mainly games, that I've run.

*Compiz* isn't playing badly with any apps.  There are/were some apps that relied on implementation details of Metacity which Compiz doesn't have, but there aren't many of them (now that Java is fixed), and they were always broken.

> **| MM | said:**
> 
SO yes, compiz does need to play nicer/better with some apps in some cases.  But i fear that even with Xserver changes like DRi2, we will still be waiting on gfx card vendors (nvidia in my case) to update their binary  drivers.

As a sweeping over-generalisation, nVidia doesn't care about X infrastructure, they use their own.  They don't need DRI2 (they already do redirected direct rendering), they aren't going to support xrandr12 (it doesn't support dual-card as well as TwinView, although I prefer the way xrandr handles one-card-two-screens), and they don't use Mesa at all, so they aren't affected by gallium.

---

### Post by plun on 2008-06-04
> **RAOF said:**
> Is flash *really* OpenGL accelerated under metacity?  If it is, it will still be accelerated under Compiz.  There is a (fairly small) unavoidable overhead involved in compositing, and Compiz effects can be pretty much arbitrarily GPU intensive, but on my nvidia card (7600go), I've never found Compiz (while not performing effects) to make a noticable performance hit in the 3D apps, mainly games, that I've run.



Well Adobes Flash is accelerated...

[http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html](http://blogs.adobe.com/penguin.swf/2008/05/flash_uses_the_gpu.html)

> Also, for fullscreen OpenGL acceleration, the Flash Player requires that the client glx vendor string be something besides "SGI". Official drivers from, e.g., ATI and Nvidia hopefully do not have "SGI" in this field (check the 'glxinfo' command, for this string and for the extensions listed above). We have this logic in place to detect whether software rendering is in place and fall back on our own software fullscreen in that case. There are more robust ways to detect software rendering but we have seen crash problems on a number of distributions, possibly with outdated libraries.

Another important note: Compiz and GPU-accelerated Flash on Linux do not mix. The Flash Player still works if you have Compiz as your window manager; **you just won't be able to make use of GPU-accelerated features**. This is a shame since Compiz is coming with the basic installation of various Linux distributions. Unfortunately, things get unstable when trying to do GPU acceleration in SWFs running under Compiz.


Adobes Flash 10 and latest nVidia drivers plays full **_HD_** Flash content.

But... I must switch to Metacity and that isn't a problem if you
have a switcher in the systray, **fusion-icon** is enough.

Nema Problema....   :)

---

### Post by | MM | on 2008-06-04
> **plun said:**
> Well Adobes Flash is accelerated...

But... I must switch to Metacity and that isn't a problem if you
have a switcher in the systray, **fusion-icon** is enough.

Nema Problema....   :)

Yea i pretty much do the same... 

compiz is nice, i dont hate on it.  Its the simple things i like about compiz, the way windows just glide when you move them, and dropshadows, and fade in/out.  But when it comes to using my PC without fuss metacity is still the best wm i think.

---

### Post by RAOF on 2008-06-04
> **plun said:**
> ...
Adobes Flash 10 and latest nVidia drivers plays full **_HD_** Flash content.

But... I must switch to Metacity and that isn't a problem if you
have a switcher in the systray, **fusion-icon** is enough.

Nema Problema....   :)

Ah, right.  Thanks for the link.  So, they turn off their OpenGL acceleration under Compiz because the current drivers suck.  Fair enough.

---

### Post by plun on 2008-06-05
> **RAOF said:**
> Ah, right.  Thanks for the link.  So, they turn off their OpenGL acceleration under Compiz because the current drivers suck.  Fair enough.

Yup...

But it is just a tragic mess with this situation.


Maybe to file a bug to Compiz  ?    (or compiz-fusion)


I can see within my country that this mess just kills Linux and Ubuntu, really bad reputation for the moment because of this and other messed up functions which just hits newbies   .:(


Flash installs seems also to be broken in FF3...


"Waiting for a miracle ? "....  next dist > next year > next decade... :)
Sad...:(

---

### Post by RAOF on 2008-06-05
> **plun said:**
> Yup...

But it is just a tragic mess with this situation.


Maybe to file a bug to Compiz  ?    (or compiz-fusion)

...

It's not a Compiz bug.  It's a bunch of driver bugs, which happen to only be exposed by Compiz (and almost certainly KWin4 using t_f_p, too).  In fact, turning on Metacity's composite manager might be enough to expose these bugs.

---

### Post by plun on 2008-06-05
> **RAOF said:**
> It's not a Compiz bug.  It's a bunch of driver bugs, which happen to only be exposed by Compiz (and almost certainly KWin4 using t_f_p, too).  In fact, turning on Metacity's composite manager might be enough to expose these bugs.

Well, MarkS sits in the board of Linuxfoundation.

Adobe joined Linuxfoundation.

So perhaps it must be possible for open source devs to talk
with Adobes devs....

Adobes devs maybe then can talk with nVidia devs and AMD/ATIs about latest Gpus

"Bless this mess"....:(

---

### Post by MaX on 2008-06-06
No, it will be OS Devs bosses talking to Adobe's dev's bosses talking to NVIDIA/ATI bosses...

---

