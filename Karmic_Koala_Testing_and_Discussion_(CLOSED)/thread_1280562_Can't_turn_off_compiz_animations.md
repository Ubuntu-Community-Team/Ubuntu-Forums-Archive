---
title: "Can't turn off compiz animations"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sgage on 2009-10-02
I am running Karmic, updated as of Friday morning (EDT) 10/2. nVidia video, for what that's worth.

In general, Compiz is working fine for me. In the CompizConfig I can set everything the way I like, no problem, except...

I can't turn OFF window animations. When I click on the selection box, the checkmark goes away, and a few seconds later, it comes right back! 

I've tried everything I can think of. I've tried the Simple CompizConfig, I've tried importing a hand edited profile, etc.  No joy.

Has anyone else experienced this? Any ideas?

---

### Post by sdowney717 on 2009-10-02
install 'fusion-icon'
run it and then right click the icon, select window manager metacity.

---

### Post by screaminj3sus on 2009-10-02
> **sdowney717 said:**
> install 'fusion-icon'
run it and then right click the icon, select window manager metacity.

He wants to turn off the compiz animation plugin not compiz.

I have the same problem, when you uncheck it in ccsm it just re checks itself. This is annoying because I prefer the "minimize effect" plugin to the animations one.

---

### Post by sgage on 2009-10-02
Thank you sdowney! An odd little workaround, but it did the trick.

A bit of a strange buglet, since everything else works in CompizConfig. By switching to metacity with fusion-icon, running CCS, disabling animations, and switching back to compiz, all is well.

Thanks again!

---

### Post by sdowney717 on 2009-10-02
fusion-icon has fixed some of my issues as well. There must be a lot of builtin scripts in fusion-icon designed to fix these issues.

---

### Post by Amaranth on 2009-10-02
Actually once you start compiz again it'll load animation. We've got a list of plugins we consider essential to have a functional window manager that cannot be disabled. I didn't want to include animation since some people do like to use minimize instead but it's not possible to make it force either one so I had to choose.

---

### Post by screaminj3sus on 2009-10-02
> **Amaranth said:**
> Actually once you start compiz again it'll load animation. We've got a list of plugins we consider essential to have a functional window manager that cannot be disabled. I didn't want to include animation since some people do like to use minimize instead but it's not possible to make it force either one so I had to choose.

Than why is minimize effect even still there? Why can't the animations plug in have an option for the animation minimize effect uses? (It could be called zoom 2 or something)

---

### Post by Tibuda on 2009-10-02
I can't change the number of desktops in general options. It has something to do with those essential plugins?

---

### Post by DougieFresh4U on 2009-10-02
I am having the OPPOSITE problem. Say for instance I check the SNOW effect, it stays checked for a few seconds then the check mark disappears.

---

### Post by sgage on 2009-10-02
> **Amaranth said:**
> Actually once you start compiz again it'll load animation. We've got a list of plugins we consider essential to have a functional window manager that cannot be disabled. I didn't want to include animation since some people do like to use minimize instead but it's not possible to make it force either one so I had to choose.

Ah, I haven't rebooted since I tweaked it. 

I strongly dislike animated windows, and I don't understand why it's not configurable - it used to be. I think it's a bit strange to force it, but oh well.

---

### Post by Amaranth on 2009-10-02
> **screaminj3sus said:**
> Than why is minimize effect even still there? Why can't the animations plug in have an option for the animation minimize effect uses? (It could be called zoom 2 or something)

Actually that's planned for the compiz++ rewrite, maybe it'll even happen. For now you can always define COMPIZ_PLUGINS to something else in /etc/xdg/compiz/compiz-manager to override our set of defaults. If you just do COMPIZ_PLUGINS="" it'll change it back to the pre-karmic setup where you can disable everything.

---

### Post by Amaranth on 2009-10-02
> **danielrmt said:**
> I can't change the number of desktops in general options. It has something to do with those essential plugins?

You were never supposed to be able to change this setting, we disabled it years ago but a bug allowed it to be set again. Compiz does not really work with virtual desktops, you should use the viewport options right above that option instead.

---

### Post by Tibuda on 2009-10-02
> **Amaranth said:**
> You were never supposed to be able to change this setting, we disabled it years ago but a bug allowed it to be set again. Compiz does not really work with virtual desktops, you should use the viewport options right above that option instead.

Thank you. Why this option is visible then?

I want to tweak it because tint2 don't recognize viewports. See [http://code.google.com/p/tint2/wiki/FAQ#Tint2_doesn%27t_work_on_compiz_correctly?](http://code.google.com/p/tint2/wiki/FAQ#Tint2_doesn%27t_work_on_compiz_correctly?).

---

### Post by Amaranth on 2009-10-02
It's still visible because...oops? :) I guess we could just hide it. Compiz completely fails when using virtual desktops. You lose your panels and such on any virtual desktop except the first one.

---

### Post by ions on 2009-10-10
> **DougieFresh4U said:**
> I am having the OPPOSITE problem. Say for instance I check the SNOW effect, it stays checked for a few seconds then the check mark disappears.

I have this problem as well.

---

### Post by KhaaL on 2009-10-10
> **ions said:**
> I have this problem as well.

I'm also affected. tried with both flat-file and gconf backend to no avail.

---

### Post by Amaranth on 2009-10-10
Snow and some other plugins (in compiz-fusion-plugins-unsupported) are not compatible with the compiz we have in karmic. This package is actually being removed from Ubuntu as we never should have had it, it came from Debian.

---

### Post by Tibuda on 2009-10-10
That's what I call "unsupported"! :lolflag:

---

### Post by KhaaL on 2009-10-11
i did uninstall the unsupported package, but some settings are still untouchable. A small example, i'm trying to reassign the initiate resize window mousebutton from alt+mousebutton2 to alt+mousebutton3. I do that, it looks like its registering the new setting but i still have to use alt+mousebutton2 to resize windows. Going back to resize window plugin in ccsm, it reverts back to alt+mousebutton2...

---

### Post by DougieFresh4U on 2009-10-11
> **sgage said:**
> .

I can't turn OFF window animations. When I click on the selection box, the checkmark goes away, and a few seconds later, it comes right back! 

```
[B]Amaranth
This is funny as when I try to select an animation (snow) a check mark appears in the box and then goes away after a few seconds  :confused:
Snow and some other plugins (in compiz-fusion-plugins-unsupported) are not compatible with the compiz we have in karmic. This package is actually being removed from Ubuntu as we never should have had it, it came from Debian.[/B]
```
It (snow) was working for a couple of days

---

### Post by nathanbosch on 2009-10-22
> **Amaranth said:**
> Actually once you start compiz again it'll load animation. We've got a list of plugins we consider essential to have a functional window manager that cannot be disabled. I didn't want to include animation since some people do like to use minimize instead but it's not possible to make it force either one so I had to choose.

Why are animations considered essential?

---

### Post by Amaranth on 2009-10-22
Because we want the minimize effect so users know where windows are going. If you're wondering why we don't force wall in that case so users can use multiple workspaces it's because a lot of people use cube but almost no one uses minimize (and this plugin won't even be in 0.9).

In any case, just add COMPIZ_PLUGINS="" to /etc/xdg/compiz/compiz-manager or ~/.config/compiz/compiz-manager and then you can enable/disable any plugin you want.

---

### Post by nathanbosch on 2009-10-23
> **Amaranth said:**
> Because we want the minimize effect so users know where windows are going. If you're wondering why we don't force wall in that case so users can use multiple workspaces it's because a lot of people use cube but almost no one uses minimize (and this plugin won't even be in 0.9).

In any case, just add COMPIZ_PLUGINS="" to /etc/xdg/compiz/compiz-manager or ~/.config/compiz/compiz-manager and then you can enable/disable any plugin you want.

As this probably isn't be best place for a discussion on whether animations should be forced by default could you point me towards the right location to voice my opinions on this idea?

---

### Post by Aikon- on 2009-10-24
> **nathanbosch said:**
> As this probably isn't be best place for a discussion on whether animations should be forced by default could you point me towards the right location to voice my opinions on this idea?

I would also be interested in voicing my opinion on this.. There were quite a few usability issues I noticed coming from 9.04 to 9.10 RC today, and one of the big ones is that my windows are no longer acting the way I want them to; instead, they are acting like crappy versions of Windows Aero windows.

-Aikon

---

