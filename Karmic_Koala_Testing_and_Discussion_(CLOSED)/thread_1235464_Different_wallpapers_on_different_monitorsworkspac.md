---
title: "Different wallpapers on different monitors/workspace"
date: 2009-08-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Rackstar on 2009-08-09
Hey,

This has been an [idea in brainstorm]("http://brainstorm.ubuntu.com/idea/93/") for quite a while. It's "in development" since 11 may 2008.

Sorry if I'm asking the wrong people, but does anybody know how the progress in this is going?

It didn't got into Intrepid, didn't got into Jaunty, hopefully Karmic?

(I know it's a GNOME issue)

Ruben

---

### Post by caryb on 2009-08-09
Works flawlessly on Kubuntu/Nvidia combination :guitar:


Cary

---

### Post by Rackstar on 2009-08-09
Yea, maybe I'll go over to the dark side...

Although I've always been a GNOME lover, but KDE 4.3 just looks more polished. Maybe I'll wait for Karmic.

---

### Post by Martje_001 on 2009-08-09
Gnome developers reject all patches regarding this, unfortunately. I have no idea why, though.

---

### Post by phenest on 2009-08-09
Some one by the name of James Sharpe was developing this as his own project, to submit to Gnome. To date, it looks like they don't like the way he's doing it (or something like that).

I don't see this being in Karmic.

---

### Post by ranch hand on 2009-08-12
I had an app that put a different wallpaper on each workspace in Hardy, that was the last version it worked in.  Forget the name, got it from GetDeb.  Worked pretty slick and was nice to have.  I look for it every oncein a while hoping it has been updated to the newer releases.

---

### Post by Tibuda on 2009-08-12
You can use the compiz wallpaper plugin if you disable the desktop icons in gconf-editor (/apps/nautilus/preferences/show_desktop).

---

### Post by ranch hand on 2009-08-12
The app I have on Hardy is Wallpapoz.  Still works.

---

### Post by JohnJackson on 2009-08-12
I just saw this, might be useful.

[Multi Backgrounds Daemon]("http://www.gnomefiles.org/app.php?soft_id=2249")

---

### Post by malachi1990 on 2009-08-14
Another option is E17. The advanced view on the wallpaper control allows you to set up wallpapers by virtual desktop or by monitor (or both). 

Though it's techinically pre-alpha, I haven't had a crash in a while.

The repo (for jaunty, but I'm on Karmic too, and haven't had any issues) is: deb [http://packages.enlightenment.org/ubuntu](http://packages.enlightenment.org/ubuntu) jaunty main extras

(found at: [http://packages.enlightenment.org/windows/](http://packages.enlightenment.org/windows/) )

Last time I tried out mutter (the GNOME 3 window manager) it had this functionality as well, though it may have been via a third party app.

---

### Post by realzippy on 2009-08-14
> **ranch hand said:**
> The app I have on Hardy is Wallpapoz.  Still works.

..just tried it under 8.10/compiz.
Works,but unfortunetly when rotating cube the new wallpaper is set after cube rotated,so you cannot see different wallpapers on the cube...
any ideas?

---

### Post by ranch hand on 2009-08-14
> **realzippy said:**
> ..just tried it under 8.10/compiz.
Works,but unfortunetly when rotating cube the new wallpaper is set after cube rotated,so you cannot see different wallpapers on the cube...
any ideas?
Can't help you there, my ATI card is not capable of running compiz at all.

I had (and have) 6 work stations.  Name each, assign wallpaper.  The only thing that I had a problem with wasremembering to turn it on every time I booted up.  It displayed the wallpaper for the workstation that you shut down under.

---

### Post by Tibuda on 2009-08-14
> **realzippy said:**
> ..just tried it under 8.10/compiz.
Works,but unfortunetly when rotating cube the new wallpaper is set after cube rotated,so you cannot see different wallpapers on the cube...
any ideas?

The compiz wallpaper plugin works with the cube.

---

### Post by Rackstar on 2009-08-14
Sorry for the late response!

Thanks for all the suggestions. I use Compiz, so it will bother me if the wallpapers change too late.

But the main feature that I want, is to get seperate (or duplicate) wallpapers for my laptop and my external screen. (And don't stretch it across both screens). Is that possible?

---

### Post by cszikszoy on 2009-08-14
I really don't understand why gnome has such a resistance to this.  This is one of the things I miss the most about windows.  I've got tons of great dual monitor backgrounds but don't have much use for them in gnome.  I didn't know KDE or e17 could do this, I guess I'll have to give those a try.

---

### Post by realzippy on 2009-08-15
> **danielrmt said:**
> The compiz wallpaper plugin works with the cube.

think works only without desktop icons......?

---

### Post by Tibuda on 2009-08-15
> **realzippy said:**
> think works only without desktop icons......?

Yes, this is because compiz will replace nautilus to draw the wallpaper. You can display your icons using the [FolderView Screenlet]("http://www.gnome-look.org/content/show.php/Folderview+Screenlet?content=102890"), like that KDE Plasma. I don't know how stable is that screenlet, but you can try it.

---

### Post by inportb on 2009-08-15
> **malachi1990 said:**
> The repo (for jaunty, but I'm on Karmic too, and haven't had any issues) is: deb [http://packages.enlightenment.org/ubuntu](http://packages.enlightenment.org/ubuntu) jaunty main extras

Thanks for the hint; I've been looking for a good repository since the last one I used went down.

And yes, KDE does this ;p

---

### Post by mister_playboy on 2009-09-26
> **danielrmt said:**
> You can use the compiz wallpaper plugin if you disable the desktop icons in gconf-editor (/apps/nautilus/preferences/show_desktop).

I'd like to try it out but I'm a bit confused about what needs to be done... could someone explain?  I don't see an option about this in nautilus's preferences, and I have no "apps" folder in the root directory. :confused:

---

### Post by Martje_001 on 2009-09-26
Execute 'gconf-editor' in a terminal or with *alt + f2*. Good luck.

---

