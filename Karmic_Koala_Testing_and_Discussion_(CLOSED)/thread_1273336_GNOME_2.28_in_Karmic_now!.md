---
title: "GNOME 2.28 in Karmic now!"
date: 2009-09-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gjoellee on 2009-09-23
I just wanted to tell that GNOME 2.28 is in Karmic now (you might need to update to get it). A lot of crash fixes has been done, and I am just waiting for the official release of GNOME sometime later today...

---

### Post by Starks on 2009-09-23
We've essentially had 2.28 ever since the 2.27 code started landing.

---

### Post by gjoellee on 2009-09-23
> **Starks said:**
> We've essentially had 2.28 ever since the 2.27 code started landing.

FAIL? :confused:

---

### Post by gjoellee on 2009-09-23
> **Starks said:**
> We've essentially had 2.28 ever since the 2.27 code started landing.

Oh...maybe I misunderstood :P

I know that 2.27 is the development for 2.28, but I mean that 2.28 stable is out on Karmic!

---

### Post by Regenweald on 2009-09-23
Yup, about 2 days now. I got it over three sets of updates :)

---

### Post by froggyswamp on 2009-09-23
But they didn't fix the Alt+F2 with transparent panel issue, right? Bad. Also, since Hardy one can't change the  keyboard layout with both Alt keys anymore, which was handy, but no one cares..

---

### Post by cyberkilla on 2009-09-23
> **froggyswamp said:**
> But they didn't fix the Alt+F2 with transparent panel issue, right? Bad. Also, since Hardy one can't change the  keyboard layout with both Alt keys anymore, which was handy, but no one cares..

Still no change? I've resorted to quite an interesting trick..

I use the Compiz Fusion "Widget Layer" and set the rules to include Gnome-Panel. The panel is then hidden, until I press F12. It's great, because I think it's an eyesore. You can still call up the menu with ALT+F1, anywhere your mouse cursor is - feels like EnlightenmentWM:D

I use *stalonetray* with the settings:
```
stalonetray -geometry 104x48-4-4 --skip-taskbar --sticky --tint-level 0 --tint-color black -t --skip-taskbar --window-type dock --grow-gravity W --icon-gravity SE --ignore-icon-resize TRUE --respect-icon-hints false --max-height 48 --icon-size 24 -i 24 &
```

Very off-topic, but here's a screenshot:) I also use GNOME-Do/Docky on autohide. Nice and minimalist.
To put the notification icons on the bottom-right of the screen. Much better! I then use Emerald with the "Radial" theme, with the Glossy GTK theme. It makes GNOME look so much more up-to-date.

---

### Post by Schendje on 2009-09-23
> **cyberkilla said:**
> Compiz Widget Layer

Offtopic, but thanks for pointing out the Widget layer. Great toy to play with! :D

---

### Post by CoreyB. on 2009-09-23
Here are the release notes:

[http://library.gnome.org/misc/release-notes/2.28/]("http://library.gnome.org/misc/release-notes/2.28/")

---

### Post by cyberkilla on 2009-09-23
> **Schendje said:**
> Offtopic, but thanks for pointing out the Widget layer. Great toy to play with! :D

No problem:)

> **CoreyB. said:**
> Here are the release notes:

[http://library.gnome.org/misc/release-notes/2.28/]("http://library.gnome.org/misc/release-notes/2.28/")

Thanks for that. I had been looking for the release notes myself.
Strange, but bluetooth doesn't work for me in Karmic. It used to, but now it just pegs the CPU to 100%.

---

### Post by mikedep333 on 2009-09-23
While yes, it is nice to say that we have Gnome 2.28 instead of 2.27.9x, keep in mind that this is a minimal difference. The last 2.27.9x version was the release candidate for 2.28. The only technical difference is that a moderate amount of bugs were fixed. There are still a great number of bugs present in Karmic's integration of Gnome regardless; so don't expect a stable desktop experience yet.

For example, I noticed one bug fixed (it no longer prompts you for a username/password to browse certain workgroups, perhaps the ones with Windows 7 homegroups on them.) Yet I have experienced other bugs still (totem is often unstable, in fact, it just froze on me as I was typing this, lol.)

So congratulations to Gnome on releasing their final version, but we must wait for Ubuntu to have a stable Gnome desktop.

---

### Post by Nullack on 2009-09-23
Im dissapointed with the release version

Totem now has the annoying habit of not remembering my preference to having no sidebar.

The bug with gnome system log viewer complaining about btmp.log on each run was not fixed.

It reflects the general lack of quality that FOSS projects are sadly showing these days. More and more FOSS projects are being released with more bugs that dont get fixed than years past.

---

### Post by talkingwires on 2009-09-24
> **Starks said:**
> We've essentially had 2.28 ever since the 2.27 code started landing.Heh, yeah. If you've been dist-upgrading regularly, you've been running Gnome 2.28 for three days before the official launch. Not that much has changed. I think the Gnome developers were mostly working on ripping out outdated systems for this release in preparation for 2.30/3.0.

I almost wish they'd had the guts to start almost from scratch like the KDE team did. But on the other hand, look where KDE4 stands over a year after their broken initial release. Sure, most apps now have been ported over and it's starting to come together, but that first year was *really* rocky. It reminds me of Drupal's development (if anybody else follows it) where they're soliciting pledges that crucial modules *will* be ready the day of the next version's release.

---

### Post by nutmac on 2009-09-24
Is 2.28 fully landed yet? Epiphany is still gecko flavored 2.26.1 (special webkit version is stuck at 2.27.92) and it is missing new 2.28 features like Time Tracker.

---

### Post by nortexoid on 2009-09-25
So will Karmic ship with 2.28 when it's released later this month?

---

### Post by VMC on 2009-09-25
> **nortexoid said:**
> So will Karmic ship with 2.28 when it's released later this month?

It's already there, System>About Gnome=2.28.0

---

### Post by nortexoid on 2009-09-25
> **VMC said:**
> It's already there, System>About Gnome=2.28.0

I just looked at the Alpha6 release page and it says it's using the development version 2.27.91.

---

### Post by aamukahvi on 2009-09-25
> **nortexoid said:**
> I just looked at the Alpha6 release page and it says it's using the development version 2.27.91.

That's because Alpha 6 was released before Gnome 2.28.

---

### Post by hanzomon4 on 2009-09-25
Not all of it is there

---

