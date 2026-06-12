---
title: "where's the kde air theme gone :O"
date: 2009-06-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by inportb on 2009-06-19
I've been staying up-to-date with a staging theme called *air* from KDE's SVN ([http://websvn.kde.org/trunk/playground/base/plasma/desktoptheme/air/](http://websvn.kde.org/trunk/playground/base/plasma/desktoptheme/air/)); but when I went to pull down more updates just now I discovered that it's disappeared :mad:

So like... has anyone a clue as to where it's gone? It'd be great if this awesome theme has transitioned from the playground into KDE proper, but I'd still like to know where it is ;)

Thanks.

---

### Post by David Wedelich on 2009-06-19
[http://www.notmart.org/index.php/Graphics/AIR:_it%27s_official]("http://www.notmart.org/index.php/Graphics/AIR:_it%27s_official")

It's moved out of playground, so it's now in:
[http://websvn.kde.org/trunk/KDE/kdebase/runtime/desktoptheme]("http://websvn.kde.org/trunk/KDE/kdebase/runtime/desktoptheme/")

---

### Post by vishalrao on 2009-06-20
Which means it should show up in the next KDE 4.3 pre-release (beta3?) :)

---

### Post by inportb on 2009-06-20
Oh, this is great news. Thanks for the link; now I am updating from svn://anonsvn.kde.org/home/kde/trunk/KDE/kdebase/runtime/desktoptheme/air :p

---

### Post by ruik on 2009-06-20
> **inportb said:**
> Oh, this is great news. Thanks for the link; now I am updating from svn://anonsvn.kde.org/home/kde/trunk/KDE/kdebase/runtime/desktoptheme/air :p

So how does one do that? :) I want some... air too.

---

### Post by inportb on 2009-06-20
> **ruik said:**
> So how does one do that? :) I want some... air too.

(assuming you have subversion installed)

For the first time:
```
cd ~/.kde/share/apps/desktoptheme
svn checkout svn://anonsvn.kde.org/home/kde/trunk/KDE/kdebase/runtime/desktoptheme/air air
```

To update:
```
cd ~/.kde/share/apps/desktoptheme/air
svn update
```

To select the theme... right-click the desktop > Desktop Settings > Desktop Theme = Air > OK

---

### Post by ruik on 2009-06-20
Great, thanks!

---

### Post by PRGUY85 on 2009-06-20
Any pics on it currently?

---

### Post by taavikko on 2009-06-21
> **PRGUY85 said:**
> Any pics on it currently?

This is my screenshot: [[IMG]http://www.aijaa.com/img/t/00105/4392176.t.png[/IMG]](http://www.aijaa.com/v.php?i=4392176.png)

But I prefer [http://www.youtube.com/watch?v=4VqY6hLosCo](http://www.youtube.com/watch?v=4VqY6hLosCo) BLACK themes

:lolflag:

---

### Post by inportb on 2009-06-21
Noooo not the BLACK; it's out there to get me! I could hear its cries, bleating against the background of BLACKness... I could feel the liquid aura of the BLACK, flowing sticky and thick... and oh God, look, the bottomless depths of your eyes, so full of BLACK, devoid of hope... ARRRGH

I'm not sure about the air wallpaper though... switched to the one with the fronds. What's it called? Ah yes, *Curls on Green*.

---

### Post by PRGUY85 on 2009-06-21
> **taavikko said:**
> This is my screenshot: [[IMG]http://www.aijaa.com/img/t/00105/4392176.t.png[/IMG]](http://www.aijaa.com/v.php?i=4392176.png)

But I prefer [http://www.youtube.com/watch?v=4VqY6hLosCo](http://www.youtube.com/watch?v=4VqY6hLosCo) BLACK themes

:lolflag:

Well, it looks like Oxygen but with transparent bars...thought there would be an improvement on title bars.

---

### Post by MacUntu on 2009-06-21
> **PRGUY85 said:**
> Well, it looks like Oxygen but with transparent bars...thought there would be an improvement on title bars.

AFAIK windows decoration has nothing to do with the theme.

---

### Post by PRGUY85 on 2009-06-21
> **MacUntu said:**
> AFAIK windows decoration has nothing to do with the theme.

True, yet regular users which is what all desktops and user systems are made for or shoot for, see the title bars as a big part of the desktop's theme.  Just thought Air would be different based on a concept screenshot they posted for KDE 4.3 a while back.

---

### Post by inportb on 2009-06-21
Well, I haven't heard of a new style to match the plasma theme, so... I guess we'll be using Oxygen for now =p

---

