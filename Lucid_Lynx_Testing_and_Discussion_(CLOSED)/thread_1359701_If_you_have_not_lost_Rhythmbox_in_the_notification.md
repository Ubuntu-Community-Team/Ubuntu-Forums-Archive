---
title: "If you have not lost Rhythmbox in the notification area"
date: 2009-12-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-12-20
do not update rhythmbox just yet.  I did on thre of my OS' before I got smart and tried not marking that one in synaptic.

I am right up to date, the ...-9 kernel and all.  Both icons still there.  So the problem, if you are filling a bug, is with rhythm box.

---

### Post by Amaranth on 2009-12-20
Do you have the indicator applet enabled? (that's the icon of an envelope)

From what I can tell the KDE-like status indicator support is being added to that so it will eventually take over from the old notification applet for showing most icons.

---

### Post by ranch hand on 2009-12-20
You know, I am not sure.

I am on my night time production OS right now (StonerEdition1.0 9.04 respin and no you don't need to be a "stoner" to use a well made OS with great is strange art work).

I know I took that thing off some installs as it irritated me sitting there but I don't know if Lounge Lizard  was one of them.

I do know that I didn't remove it from at least 2 of my 4 current installs and they are both missing the applet that you use to "quit" rhythmbox with.  I updated rhythmbox on those.

I will get back to you tomorrow and tell you.

Right now it is about time to hit the sack here in Big Sky country.  I am whipped.

---

### Post by VMC on 2009-12-20
> **Amaranth said:**
> Do you have the indicator applet enabled? (that's the icon of an envelope)

From what I can tell the KDE-like status indicator support is being added to that so it will eventually take over from the old notification applet for showing most icons.

I have that indicator applet with the envelope and when I run Rhythmbox, my notification area for RB is a small black square. Now, at least something is there. Before RB would just leave like a puff of smoke.

---

### Post by zekopeko on 2009-12-20
> **VMC said:**
> I have that indicator applet with the envelope and when I run Rhythmbox, my notification area for RB is a small black square. Now, at least something is there. Before RB would just leave like a puff of smoke.

The application indicators are a different beast all together.
They have nothing to do with messaging menu (envelope thingy).

[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators)

---

### Post by ranch hand on 2009-12-20
Now that I am back over here I can tell you that I do not have the "envelope thingy", I didn't like it.

---

### Post by phillw on 2009-12-20
> **zekopeko said:**
> The application indicators are a different beast all together.
They have nothing to do with messaging menu (envelope thingy).

[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators)

Thanks for that - I know understand a bit more why ossec was doing it's nut with > Rule: 1002 fired (level 2) -> "Unknown problem somewhere in the system."
Portion of the log(s):

Dec 2 09:26:07 localhost dbus-daemon: Rejected send message, 3 matched rules; type="method_call", sender=":1.51" (uid=1001 pid=2890 comm="/usr/lib/indicator-
messages/indicator-messages-ser") interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.132" (uid=0 pid=2237 comm="/usr/lib/NetworkManager/nm-dhcp-client.action))

It was a reported bug in dbus, now solved. I have read and fully understand & support what they're wanting to achieve.
A do like having my RythmBox applet in my top bar - but haven't got as far as working out how to add / remove items that i'd like there -- Far too busy playing with other stuff ;-)

Phill.

Oh, and for any of you with old Mac G3's running in dual boot with ubuntu .... --> I'm over here --> [http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)   :lolflag:

---

### Post by phenest on 2009-12-21
There is a plug-in for RB called 'Status Icon'. I kinda thought that maybe it was for showing a notification icon. It's enabled by default, but when I unchecked it and checked it again, RB quits. Could it be the plug-in that's causing the problem?

---

