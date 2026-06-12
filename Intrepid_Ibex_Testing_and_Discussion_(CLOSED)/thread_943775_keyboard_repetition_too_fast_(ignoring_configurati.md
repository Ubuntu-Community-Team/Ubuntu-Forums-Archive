---
title: "keyboard repetition too fast (ignoring configuration)"
date: 2008-10-10
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by hexion on 2008-10-10
Running intrepid without problems here.
Well, just one.. the keyboard settings regarding the delay to repeat key strokes and the repetition rate is too small and fast respectively.

I tried to configure the settings (System - Preferences - Keyboard) but it won't make any difference.
I tried also creating a new xorg.conf with settings by default and same problem.

Anyone out there with this problem. It's quite annoying and a showstopper in my case.

---

### Post by yabbadabbadont on 2008-10-10
As a test, open a terminal window and use xset to configure the delay and repeat rate like so:
```
xset r rate 250 30
```
Where 250 is the delay in milliseconds and 30 is the repeat rate in characters per second.

Edit: of course, use whatever delay and repeat rate you like.  :)

---

### Post by hexion on 2008-10-10
It didn't work I'm afraid...
Any other suggestion?

Thanks

---

### Post by yabbadabbadont on 2008-10-10
You mentioned creating a new xorg.conf, but it wasn't clear to me if you added an "AutoRepeat" option to your InputDevice section for your keyboard.  Did you?  I have the following in mine:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "en_US"
        Option          "AutoRepeat"    "250 30"
EndSection

```
However, I'm using Gentoo and not Ubuntu.  That should work though, unless the version of xorg used in Intrepid Ibex no longer supports setting it there.  I know that xorg is moving towards not using the xorg.conf at all, but I would think that it should still respect it if it exists.  :?

Also, I doubt that it will work since the xset method didn't...  Have you tried switching to a different window manager to see if the problem persists?  (i.e. kde, xfce, or even fluxbox or openbox)

---

### Post by rbmorse on 2008-10-10
You can't change the delay or repeat rate from system > preferences > keyboard, but you can disable keyboard repeats entirely by unchecking the little box. I'm not sure if that's not worse than the original problem. 

Looks like a legitimate bug to me.

---

### Post by hexion on 2008-10-10
@yabbadabbadont, I tried everything with xorg.conf already  and nothing worked :(

@rbmorse, I already tried that with xset r off and it indeed works but disable keyboard repeats is not functional.

---

### Post by yabbadabbadont on 2008-10-10
I didn't think that it would (as I said ;)) since the xset method hadn't worked either.  It was worth a shot though.

Try installing another window manager and see if it still happens with it.

---

### Post by hexion on 2008-10-11
> **yabbadabbadont said:**
> I didn't think that it would (as I said ;)) since the xset method hadn't worked either.  It was worth a shot though.

Try installing another window manager and see if it still happens with it.

Of course it was worth a shot :)
I'll try installing another WM. Too bad I like only Gnome though :)

Thanks for the tips.

---

### Post by kelstertx on 2008-10-12
I'm getting the issue in PCLinuxOS 2007 under KDE, and also with KDE using Myah 3.0 (Box).  I tried Ubuntu Hardy as my first choice on the system, but it wouldn't work with the graphics system, which is an ATI on a Compaq Presario 1617CL.  Clearly this problem is not Ubuntu-specific, so hopefully it's ok to ask about it here since Ubuntu users are experiencing it too. The system is for a friend who is battling Windows viruses, and I want to show her the joys of Linux, but non-functioning keyboards aren't going to win her away from the dark side. 

The problem is just like described by others since 2005 -- quick presses about 5 seconds apart are the only way to avoid getting duplicates and triplicates of most keys typed.  

As additional debugging info, I was originally going through an IOGear KVM switchbox, but sidestepped the switchbox and hooked up another (different) keyboard directly to the system, though it was a Compaq RT-101, same as the switchbox had on it.  Same stuttering problem.  That, combined with the fact that it's a dual-boot with Windows, and the keyboard works perfectly there, eliminates concerns over connection issues with the cord, etc.

I've also noticed that the animations that signal background processing (like after launching a program and the icon "bounces") are running much faster than I've ever seen before.  That's on both of the distributions.

Any other ideas?

---

### Post by jbg7474 on 2008-10-27
Well I have sort of the opposite problem, but I suspect it's related.  My repeat rate is too slow, and System, Preferences, Keyboard settings have no effect.

Curiously, when I used xset r rate 250 30, then tested by holding a key down, I get a short blip of fast repeats, and then back to the slower rate.  If I make the rate 250 50, my short blip is even faster.  So something is happening here, but maybe it's being blocked by something else.  I dunno.  When I make the rate 500 30, my short blip disappears.  Weird.

---

### Post by aethralis on 2008-10-27
This bug report has a solution to this problem (at least works for me):
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/264196](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-evdev/+bug/264196)

---

### Post by jbg7474 on 2008-10-27
That workaround, adding:

```
Section "ServerFlags"
Option "AutoAddDevices" "off"
EndSection
```

to xorg.conf works for me, but I don't know what else it might be doing.

Edit: discovered that, unsurprisingly, it is turning off some of the new automated hardware functionality in Intrepid.  So, my mouse was no longer detected as a Microsoft Comfort Optical Mouse, but just a mouse.  So some of the buttons no longer produced events.

However, I then commented out this line from xorg.conf and restarted X, fully expecting my keyboard repeat rate to go slow again, but lo and behold, the setting stuck.  So it looks like you can set this flag, restart X, fix keyboard repeat settings, comment out flag, restart X, and all is well.

---

