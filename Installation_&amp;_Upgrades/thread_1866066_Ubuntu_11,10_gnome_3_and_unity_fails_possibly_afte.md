---
title: "Ubuntu 11,10 gnome 3 and unity fails possibly after resent update."
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by odror on 2011-10-20
Without  any warning, possibly because of recent update. unity and gnome 3 fails. In both cases I get a limited useless top bar. The side bar is missing and all the unity or gnome 3 features are missing. On the other hand kde works fine.

In the past I had a similar issue, which was resolved when I deleted the /etc/X11/xorg.conf  This correction did not work today.

Any Ideas how to fix or debug this problem

Thanks

---

### Post by lovinglinux on 2011-10-20
Log with Unity 2D and delete **~/.compiz-1/session/** and **~/.config/compiz-1/compizconfig/config**.

You probably should be able to use Unity 3D after that. It works for me every time I get that weird top panel.

---

### Post by odror on 2011-10-20
> **lovinglinux said:**
> Log with Unity 2D and delete **~/.compiz-1/session/** and **~/.config/compiz-1/compizconfig/config**.

You probably should be able to use Unity 3D after that. It works for me every time I get that weird top panel.

I did that. Unity is fixed, but gnome 3 was not fixed. Are there any gnome3 files that I need to delete.

Thanks

---

### Post by lovinglinux on 2011-10-21
> **odror said:**
> I did that. Unity is fixed, but gnome 3 was not fixed. Are there any gnome3 files that I need to delete.

Thanks

I am not using Gnome Shell, so I would just be guessing and could recommend deleting files that are not really necessary.

---

### Post by demonboy on 2011-10-22
This sounds like the same problem I have and will attempt this solution in a moment. Do we know if that has been flagged up as a bug yet?

---

### Post by Xanthomryr on 2011-10-22
> **lovinglinux said:**
> Log with Unity 2D and delete **~/.compiz-1/session/** and **~/.config/compiz-1/compizconfig/config**.

You probably should be able to use Unity 3D after that. It works for me every time I get that weird top panel.

Thx, that fixed it for me.

---

### Post by ShodanjoDM on 2011-10-22
> **odror said:**
> I did that. Unity is fixed, but gnome 3 was not fixed. Are there any gnome3 files that I need to delete.

Thanks

I assume you're talking about gnome-shell?

Got similar problem, I managed to fix it by removing/renaming .gconf/ folder, log out and log back in. Hope that helps.

---

### Post by odror on 2011-10-24
> **ShodanjoDM said:**
> I assume you're talking about gnome-shell?

Got similar problem, I managed to fix it by removing/renaming .gconf/ folder, log out and log back in. Hope that helps.

I tried it. It did not help.

---

### Post by technophreak2000 on 2011-10-27
I am having this same issue with Gnome 3. I cannot remove that *@!#$*!!  bar. I deleted all the folders mentioned in this thread, and that infernal bar is still there. It's kinda annoying because I changed my gnome3 theme, and right behind the gnome bar (which is now transparent), I can still see the letters "File Edit View Go Bookmarks Help".

---

### Post by BlinkinCat on 2011-10-30
Hi, 
If you are still having problems with the top bar on Gnome 3, it may be because you have a proprietary driver installed.
I had similar troubles and did a search on "ask ubuntu" and found a solution was to uninstall driver. Now am running without, and am having very pleasing results on Unity, Fallback and Gnome 3
Best of luck - :)

---

### Post by odror on 2011-10-30
> **BlinkinCat said:**
> Hi, 
If you are still having problems with the top bar on Gnome 3, it may be because you have a proprietary driver installed.
I had similar troubles and did a search on "ask ubuntu" and found a solution was to uninstall driver. Now am running without, and am having very pleasing results on Unity, Fallback and Gnome 3
Best of luck - :)
I need that driver. It has mpeg4 support and best 3d support

---

### Post by BlinkinCat on 2011-10-30
> **odror said:**
> I need that driver. It has mpeg4 support and best 3d support

Sorry I could not help - :(

---

### Post by technophreak2000 on 2011-10-31
Hey thanks man. I gave the drivers a try and that still didn't work for me.
I'm guessing the solution you were referring to was at:
[http://askubuntu.com/questions/66345/removing-second-unity-nautilus-bar-behind-gnome-3-top-bar](http://askubuntu.com/questions/66345/removing-second-unity-nautilus-bar-behind-gnome-3-top-bar)

At that same page, I tried the solution which required gnome-tweak-tool turning off the file manager handling the desktop, and that worked like a charm!:)

The only thing is that my desktop icons go away as a result from this. Scuff.

---

### Post by odror on 2011-10-31
> **technophreak2000 said:**
> Hey thanks man. I gave the drivers a try and that still didn't work for me.
I'm guessing the solution you were referring to was at:
[http://askubuntu.com/questions/66345/removing-second-unity-nautilus-bar-behind-gnome-3-top-bar](http://askubuntu.com/questions/66345/removing-second-unity-nautilus-bar-behind-gnome-3-top-bar)

At that same page, I tried the solution which required gnome-tweak-tool turning off the file manager handling the desktop, and that worked like a charm!:)

The only thing is that my desktop icons go away as a result from this. Scuff.
I have not tried it, but aren't "appmenu-gtk" and "appmenu-gtk3" needed by gnome3. My issue is not that unity does not work, but that gnome 3 does not work.

---

### Post by cbowman57 on 2011-10-31
Here's a shot in the dark, have you tried adding **export CLUTTER_VBLANK=none** to your ~/.profile ?

You can try it from the terminal to see if you notice an improvement.

---

### Post by odror on 2011-10-31
OK the problem is solved for now. The latest upgrade to gnome-shell solved the problem.

---

