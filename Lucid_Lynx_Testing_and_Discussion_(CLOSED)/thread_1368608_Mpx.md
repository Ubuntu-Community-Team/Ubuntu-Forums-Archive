---
title: "Mpx?"
date: 2009-12-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by rednus on 2009-12-30
Anybody tried the new MPX feature? Any good? Any useful?

---

### Post by ranch hand on 2009-12-30
Oh for heavens sake, what in flinderation is this Mpx "feature"?

Where does all this stuff I have never heard of come from?

---

### Post by lisati on 2009-12-30
> **ranch hand said:**
> Oh for heavens sake, what in flinderation is this Mpx "feature"?

Where does all this stuff I have never heard of come from?

MPX? My first thought was "multiplex"......

---

### Post by cariboo on 2009-12-30
Multi-point Xserver?

---

### Post by Eclipse. on 2009-12-30
Multi Pointer X.

[http://en.wikipedia.org/wiki/Multi-Pointer_X](http://en.wikipedia.org/wiki/Multi-Pointer_X)

---

### Post by BwackNinja on 2009-12-31
[http://alec.mooo.com/mpx.php](http://alec.mooo.com/mpx.php)

Those instructions should work, I'll probably try them myself.

---

### Post by JohnJackson on 2010-01-01
Well it's cool but a bit pointless at the moment

---

### Post by rednus on 2010-01-01
> **cariboo907 said:**
> Multi-point Xserver?

yeah...

---

### Post by Eclipse. on 2010-01-01
> **JohnJackson said:**
> Well it's cool but a bit pointless at the moment

Actually its the complete opposite of pointless, its badly needed for anything touchscreen related.

---

### Post by SuperSonic4 on 2010-01-01
> **Eclipse. said:**
> Actually its the complete opposite of pointless, its badly needed for anything touchscreen related.

And how many computers are touchscreen?

---

### Post by ScislaC on 2010-01-01
> **SuperSonic4 said:**
> And how many computers are touchscreen?

I think the better question is "Which way are things trending?"

---

### Post by SuperSonic4 on 2010-01-01
> **ScislaC said:**
> I think the better question is "Which way are things trending?"

Perhaps but that's not what I referred to. I was referring to Eclipse's second post

---

### Post by bobince on 2010-01-01
I've had a quick play with MPX using two USB mice to run two pointers in Lucid &#945;1. This isn't a wholly theoretical test for me as I would like to be able to drag an on-screen volume channel fader whilst operating another channel's control.

The multiple pointers work, but there's not such a lot you can do with it at the moment. Every application I tried got confused and did *something* wrong when I tried to combine dragging with any other operation. Even the window manager and GNOME Panel misbehaved. Many controls simply wouldn't respond to interaction from the second mouse at all.

It's going to be a long slog fixing Gtk, Qt, GNOME, KDE, XUL and other apps until multiple-pointer interaction is really reliable.

---

### Post by BwackNinja on 2010-01-01
> **bobince said:**
> I've had a quick play with MPX using two USB mice to run two pointers in Lucid &#945;1. This isn't a wholly theoretical test for me as I would like to be able to drag an on-screen volume channel fader whilst operating another channel's control.

The multiple pointers work, but there's not such a lot you can do with it at the moment. Every application I tried got confused and did *something* wrong when I tried to combine dragging with any other operation. Even the window manager and GNOME Panel misbehaved. Many controls simply wouldn't respond to interaction from the second mouse at all.

It's going to be a long slog fixing Gtk, Qt, GNOME, KDE, XUL and other apps until multiple-pointer interaction is really reliable.

[http://live.gnome.org/GTK%2B/MPX](http://live.gnome.org/GTK%2B/MPX)
[http://qt.nokia.com/doc/4.6/qt4-6-intro.html#multi-touch-and-gestures](http://qt.nokia.com/doc/4.6/qt4-6-intro.html#multi-touch-and-gestures)

As for xulrunner applications and other apps that don't directly use gtk or qt4 for their interfaces, I'm not sure when they'll be ready, if they aren't already.

---

### Post by schmidtbag on 2010-02-16
you should all keep in mind that mpx is not intended for touch screens, it just works with them.  also, not much attention was brought to it when it was implemented in xorg and xserver because of the fact that most DEs don't work well with it.  peter hutterer (the guy who made it) has some DE that works very well with mpx.  i've never tried it but it would fix the problems that some of you may be getting

---

### Post by Mr. Picklesworth on 2010-02-16
> **bobince said:**
> I've had a quick play with MPX using two USB mice to run two pointers in Lucid &#945;1. This isn't a wholly theoretical test for me as I would like to be able to drag an on-screen volume channel fader whilst operating another channel's control.

The multiple pointers work, but there's not such a lot you can do with it at the moment. Every application I tried got confused and did *something* wrong when I tried to combine dragging with any other operation. Even the window manager and GNOME Panel misbehaved. Many controls simply wouldn't respond to interaction from the second mouse at all.

It's going to be a long slog fixing Gtk, Qt, GNOME, KDE, XUL and other apps until multiple-pointer interaction is really reliable.

Support is gradually making its way down the stack. The window manager (Metacity, at least) is happy with MPX now.

Instead of using two pointers in one app, try manipulating two different applications. If you bind a keyboard to each pointer, you'll find that they can be manipulated at the same time very easily. Granted, that's a far cry from being user friendly at this point, but a few tweaks here and there and we have a pretty nifty multi-user feature.

My killer feature here would be the ability to operate a drawing tablet while changing tools with the mouse in GIMP, without prior configuration.

As schmidtbag says, this is indeed not so much a multi touch screen thing, but it could be great for legacy application support with multi touch, at least maintaining the ability to use multiple fingers even if the applications don't respond in very interesting ways. It's best thought of as an elegant cleaning for xinput, since the one pointer limit was arbitrary and ugly. The best is yet to come.

For example, there's [vinput]("http://gitorious.org/vinput/pages/Home") and this:
[http://www.youtube.com/watch?v=wbkO_Uos7Oc](http://www.youtube.com/watch?v=wbkO_Uos7Oc) :)
(Although it's unclear to me whether WOG actually uses vinput + MPX, or something uglier).

---

