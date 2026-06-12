---
title: "Panel applets appear out of order /at random/, anyone?"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mr. Picklesworth on 2009-03-13
After upgrading to the Jaunty alpha, I reverted my GNOME Panel configuration to the defaults. I frequently plug my laptop in to a large external monitor, which means rather significant changes to screen resolution mid-session. The panel *seems* to survive that.

However, every now and then I log in and the applets are totally out of order. Here's my screenshot of it having become disorderly:
[ATTACH]106284[/ATTACH]

As far as I can tell, I have done NOTHING to trigger this; it just happens. (Largely because GNOME Panel has needed to be replaced since its inception. Maybe XFCE Panel would work while we wait for Gnome Shell).

Has anyone else encountered this, and maybe sensed a pattern?

---

### Post by jfernyhough on 2009-03-13
Yup. Happens many times, though not every, when I've switched resolutions. Happened just on this log on. The only thing I did last night was play a bit of World of Goo (managed OCD on Level 3!) but this, of course, switched screen res down to 800x600 from my normal 1280x800.

I've never really thought much of it, other than it's occasionally annoying. Your post makes me think this should be fixable, though, seeing as others are having the same thing happen.

---

### Post by Naddiseo on 2009-03-13
> **Mr. Picklesworth said:**
> After upgrading to the Jaunty alpha, I reverted my GNOME Panel configuration to the defaults. I frequently plug my laptop in to a large external monitor, which means rather significant changes to screen resolution mid-session. The panel *seems* to survive that.

However, every now and then I log in and the applets are totally out of order. Here's my screenshot of it having become disorderly:
[ATTACH]106284[/ATTACH]

As far as I can tell, I have done NOTHING to trigger this; it just happens. (Largely because GNOME Panel has needed to be replaced since its inception. Maybe XFCE Panel would work while we wait for Gnome Shell).

Has anyone else encountered this, and maybe sensed a pattern?


I notice this from time-to-time as well, but I have no idea what causes it.

---

### Post by hotstovejer on 2009-03-13
Totally offtopic, but what font is that? It looks killer!

Ontopic, I've mostly only had this issue when the panel isn't extended. When it is, rarely does it happen. It's almost like panel doesn't know what to do with the new resolution.

Thanks!

Jeremy


> **Mr. Picklesworth said:**
> After upgrading to the Jaunty alpha, I reverted my GNOME Panel configuration to the defaults. I frequently plug my laptop in to a large external monitor, which means rather significant changes to screen resolution mid-session. The panel *seems* to survive that.

However, every now and then I log in and the applets are totally out of order. Here's my screenshot of it having become disorderly:
[ATTACH]106284[/ATTACH]

As far as I can tell, I have done NOTHING to trigger this; it just happens. (Largely because GNOME Panel has needed to be replaced since its inception. Maybe XFCE Panel would work while we wait for Gnome Shell).

Has anyone else encountered this, and maybe sensed a pattern?

---

### Post by Mr. Picklesworth on 2009-03-13
> **hotstovejer said:**
> Totally offtopic, but what font is that? It looks killer!

Ontopic, I've mostly only had this issue when the panel isn't extended. When it is, rarely does it happen. It's almost like panel doesn't know what to do with the new resolution.

Thanks!

Jeremy

The font is size 8 Liberation Sans. (Liberation is in the repositories), with slight hinting and subpixel smoothing.

Poking with gconf, I noticed something odd. Even though I Honestly Have Not Touched the applets, their position properties have changed from those in default_setup. (Unless you count adding some launchers to the far left of that panel as touching).

For example, here is my /apps/panel/applets/notification_area_screen_0:
locked:1
panel_right_stick:0 (!!!!!!!!!!!!!!!!!!)
position:1279

Then /apps/panel/default_setup/applets/notification_area:
locked:1
panel_right_stick:1
position:5

For reference, my laptop's screen resolution is 1280x800 while my external monitor is 1920x1200, and the panel was running on my external monitor when I took that screenshot.

So it *is* a real bug. Can anyone confirm that?

(Another oddity: Have the panels recently become undraggable? I notice that the Lock Panel option disappeared and they all seem locked. If so, that makes me happy! Dragging panels by accident is silly, especially since every useful option is in the context menu anyway)

---

### Post by Yashiro on 2009-03-15
If they are actual applets (not notification icons) make sure they're locked.

Given their data is saved via Gconf maybe your gconf deamon is crashing or your gconf data is somehow corrupt?

---

### Post by Mr. Picklesworth on 2009-03-16
Yep, since I change my screen resolution every single session, this happens continually. (It's awesome that ext monitors, even with twinview, don't need to happen at runtime any more and can be configured within my own session as a regular user, but it would be nice if it was persistent).

Observation upon studying the gconf keys a bit: Ubuntu's defaults place some applets on the right with a position of 0. It seems that the stuff at 0 changes to 1280 immediately and it all peels apart from there. I not have the right side applets starting at position 1 and I'll see what happens...

I also moved the notification area to the left, right next to the main menu, which actually feels a bit nicer with the clock and Hamster on the right. Hopefully this won't cause anything to not screw up. It may, come to think of it, since the notification area's behaviour is the most significantly screwed up; every time it gets bigger, it moves to the left... but I can't bring myself to go back!

Yashiro, as I mentioned these are the default applets with the default setup. (Within reason. I removed the launchers and the indicator applet). They are indeed locked, and gconf is entirely content; this smells like a problem with the panel. This post isn't really in search of a workaround, but a problem! I'm wondering if anyone else has bumped into this same problem and has some idea what causes it. The behaviour looks like a bug to me but I can't quite put my finger on whose fault it is.

---

### Post by olskar on 2009-03-16
I can comfirm this, it has been in at least Hardy, Intrepid and Jaunty so far :(

---

### Post by Mr. Picklesworth on 2009-03-17
Ah, we already have a bug report:
[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-panel/+bug/44082](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-panel/+bug/44082)

Gah...

---

### Post by Schmoove on 2009-03-17
Another victim here. It happens sometimes... seems quite random never managed to figure out what caused it.

---

### Post by charliehorse55 on 2009-04-12
Had this problem in intrepid, still going in Jaunty. Too Bad. Sometimes my username gets bumped to the left by like the sound and other icons.

---

### Post by FuturePilot on 2009-04-12
> **Mr. Picklesworth said:**
> 

(Another oddity: Have the panels recently become undraggable? I notice that the Lock Panel option disappeared and they all seem locked. If so, that makes me happy! Dragging panels by accident is silly, especially since every useful option is in the context menu anyway)

You have to hold down Alt while dragging them now. I'm also happy about this because I've seen panels get randomly rearranged accidentally.

---

