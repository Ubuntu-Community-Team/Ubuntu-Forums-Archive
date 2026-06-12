---
title: "sudo apt-get remove --purge compiz"
date: 2009-02-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-02-08
GOODBYE compiz!

Following todays fresh install, my gnome session would hang on compiz after installing the NVIDIA drivers. That was the final straw. Killing the process and purging it from my system was truly satisfying.

Compiz wont ever work right until proper 3d memory management is implemented as a framework and implemented into video drivers. I was tired of turning off compiz each time I went into a full screen 3d opengl mode.

And besides, what did it ever really do? It was all lame bling thats what. I got carried away with it too, but in time, I realised it did not actually improve my interaction with the system........it just added grief me with bugs and a non complete solution.

Its nice that 180.27 has been added to the repos but for some reason I had to manually enable to driver after instillation in the hardware drivers app.

---

### Post by yeats on 2009-02-08
I removed compiz from my Kubuntu Intrepid installation - just because it was eating resources for a neglible benefit (especially when added to the already buggy KDE 4.1).  Of course I later reinstalled Kubuntu Hardy Heron, and *that* was the moment when I sighed in relief! :-)

---

### Post by klange on 2009-02-08
It saddens me to hear you guys say that...

---

### Post by Jay_Bee on 2009-02-08
I understand your frustration but those are mostly video driver/X.Org problems and unfortunately Compiz makes them painfully visible.
I am hoping for a year now that they will fix it, and now things are finally starting to move at least with Intel and hopefully with others soon to follow.
I think it's not fair to call Compiz "lame bling", it has some very good and useful features, it advanced the Linux desktop and it allowed the development of new applications.
Compiz allowed Linux to compete with Vista and OS X on the "bling" front too. It allowed users to have compositing before KDE4 and Metacity Compositor.
Come on guys, there's no need for mean comments, if you don't like it don't use it.

---

### Post by bpl07 on 2009-02-08
There are other ways to turn off compiz than to remove it completely.  I change the default window manager to metacity in gconf-editor (desktop > apps > window manager > current and default set to /usr/bin/metacity).  I then install fusion-icon and use it to turn compiz on every once and a while to see how things are coming, then use it to switch back to metacity for daily use.  You can even use metacity as a compositor (another gconf key) so that you can keep stuff like AWN or Gnome Do Docky.

I feel like I do better service as a tester to at least try the stuff as it develops rather than completely remove it.  Just my two cents.

---

### Post by Nullack on 2009-02-08
While I understand the point about testing (and its a good one), I think a more important issue is quality of releases. Half baked solutions should not be implemented by default. When the required solutions for a new technology dont exist, its time for experimentation, not premature implementation.

Windows and OSX dont have a half baked composting capability. To claim that Linux somehow met those competitors on the composting front is to simply ignore how it fails. It'll be a good day when compiz is fully cooked with gpu memory management and related drivers, but we dont have a full solution like in other systems.

Instead of helping me interact with the system, right now compiz harasses the user with bugs and its missing components mandates users to do even more work with interaction to turn it off when it needs it.

:)

---

### Post by cl333r on 2009-02-08
> Windows and OSX dont have a half baked composting capability.
Afaik it's all about buggy drivers. On Linux, as I understood from what developers say, the video drivers are like 10x times buggier than for windows and mac. And since they are proprietary there's nothing much one can do. Fortunately things are changing for ATI but that's another story.

---

