---
title: "Two sound icons in panel"
date: 2009-07-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by maheshasolkar on 2009-07-21
After yesterday's updates, I get two sound icons in the panel. One is in the Notification area and other one is on the panel.

I believe the one on the panel is the Volume Control applet - which I want. I wonder what is the one in the Notification area for.

Anyone else see this?

In the attached image, the one on the right (next to the weather applet) is the Volume Control applet. The one on the left is in Notification are.

---

### Post by Slug71 on 2009-07-21
Yep i have it too.

---

### Post by woodbj on 2009-07-21
I have two as well

---

### Post by neferty on 2009-07-21
same here, pretty weird :)

---

### Post by forumache on 2009-07-21
Actually one of them is in the notification area, the other is on the panel. So you can remove the one in the panel.

This was introduced shortly for jaunty and postponed for karmic.

It is good :)

---

### Post by Hairy_Palms on 2009-07-21
yea theres two now, whats worse is the new sound preferences dialog sucks, doesnt let you control different microphone sockets and only seems to see one, forcing me to bust open alsamixer if i actually wanna change any volumes, great way to make a formerly useful applet useless, any way to get the old functionality back?

also whats the deal with applications specific volume controls? last time i checked, every application that uses sound had its own inbuilt volume control already.

---

### Post by scaine on 2009-07-21
Except that the one in the panel doesn't give you the option of a mixer and has a vertical volume control rather than the newer horizontal one.  Strange.

Notification one also doesn't support double-click-to-mute.  I notice, bizarrely that you need to right-click to mute that one.

Scratch the mixer comment - right click to bring up "Sound Preferences" too.

---

### Post by scaine on 2009-07-21
> **Hairy_Palms said:**
> yea theres two now, whats worse is the new sound preferences dialog sucks, doesnt let you control different microphone sockets and only seems to see one, forcing me to bust open alsamixer if i actually wanna change any volumes, great way to make a formerly useful applet useless, any way to get the old functionality back?


If you need functionality back from any given upgrade in an Alpha2 distro, you shouldn't be using it.  Stick with Jaunty - it doesn't use the PA volume control at all.

> **Hairy_Palms said:**
> 
also whats the deal with applications specific volume controls? last time i checked, every application that uses sound had its own inbuilt volume control already.

This is a PA volume control feature.  Much like the way Windows Vista does it, each app gets it's own volume.  Useful for reducing system sounds while keeping, say Movie Player nice and loud.

---

### Post by Hairy_Palms on 2009-07-21
> If you need functionality back from any given upgrade in an Alpha2 distro, you shouldn't be using it. Stick with Jaunty - it doesn't use the PA volume control at all.
As i said i have been using alsamixer for the functionality, but unfortunately i can foresee karmic being released with this new voume control unchanged, and i dont think ill be the only one with this problem, so if i dont make a point about it now nothing will change, i invite others to sign the bug report
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/402170](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/402170)

---

### Post by papangul on 2009-07-21
The system tray volume control can be turned off by unchecking "Volume Control" from System> Preferences>Startup Applications.

---

### Post by jerrylamos on 2009-07-21
Any fix for volume control ALWAYS muted instead of where it was set on last shutdown?

Thanks, Jerry

---

### Post by Hairy_Palms on 2009-07-21
go to system->admin->services and tick alsa-utils iirc.

---

### Post by BwackNinja on 2009-07-21
@jerrylamos - I've got the same problem, but only if my volume is down low, if it is higher it stays unmuted.

---

### Post by scradock on 2009-07-21
> **papangul said:**
> The system tray volume control can be turned off by unchecking "Volume Control" from System> Preferences>Startup Applications.
What "Startup Applications"? It's not there!

And it's not in the Main Menu to be added, either.......

---

### Post by Starks on 2009-07-21
I've never been fond of the fact that the Test buttons have vanished.

---

### Post by papangul on 2009-07-22
> **scradock said:**
> What "Startup Applications"? It's not there!

And it's not in the Main Menu to be added, either.......
When have you last updated?...Are you getting the volume control system tray icon (not the panel one) at all?

---

### Post by tekstr1der on 2009-07-22
There should only be one applet for sound available as of latest updates:

```
gnome-applets (2.27.3-0ubuntu3) karmic; urgency=low

  * debian/control.in, debian/gnome-applets.manpages, debian/rules:
    - don't build the mixer applet since the gnome-media one is used now
      (lp: #401294)
```

Also, sound output level setting is being retained between sessions for me recently. No more mute default.

---

### Post by cecilpierce on 2009-07-22
Does any body know why the alert volume is grayed out ?

---

### Post by Marat89 on 2009-07-22
I just installed the Update.
But now the gnome-media applet is just ugly compared to the on in jaunty or the second one existing before.
Horizontal alignment is better.
There is no -,+, mute or setting button, when clicking on the applet.
In my opinion the second one must be standard in ubuntu installations and this gnome-media volume applet have to be dropped. Its just double time of work to make this feature equal to the old one.
Your oppinions?

---

### Post by ELD on 2009-07-22
> **Marat89 said:**
> I just installed the Update.
But now the gnome-media applet is just ugly compared to the on in jaunty or the second one existing before.
Horizontal alignment is better.
There is no -,+, mute or setting button, when clicking on the applet.
In my opinion the second one must be standard in ubuntu installations and this gnome-media volume applet have to be dropped. Its just double time of work to make this feature equal to the old one.
Your oppinions?

Looks like a step backwards to me!!

---

### Post by wayne_cat on 2009-07-22
volume control is now a notification :-k

i think I'm getting old ... is it "cool/hip/groovy/fresh" to do it this way nowadays?

---

### Post by Marat89 on 2009-07-23
Should we fill a bug dealing with this issue?

---

### Post by Hairy_Palms on 2009-07-23
there is one 
[https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/402170](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/402170)

---

### Post by Marat89 on 2009-07-23
Thank you, seems Im not alone ;-)

---

### Post by scaine on 2009-07-24
Sebastian Bacher has commented on that bug that it may be a duplicate of [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/322909](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/322909).  It looks like it might be?  Hairy_Palms?

On a side note, I notice that the original volume applet now says "deprecetated" next to its name when trying to add it.  But when adding it, it simply shows up as a dot on the panel.  I can't actually remove the dots I have now, even using gconf-editor.  <sigh>  There are times that gnome is /extremely/ trying.

---

### Post by wayne_cat on 2009-07-24
> **scaine said:**
> 
On a side note, I notice that the original volume applet now says "deprecetated" next to its name when trying to add it.  But when adding it, it simply shows up as a dot on the panel.  I can't actually remove the dots I have now, even using gconf-editor.  <sigh>  There are times that gnome is /extremely/ trying.

the same here ... I had to delete all applet settings:

```

gconftool-2 --recursive-unset /apps/panel/applets
```to get rid of the dot (deprecated applet).

The new mixer applet is still not in the list here ... no graphical volume control at the moment.

---

### Post by scaine on 2009-07-24
> **wayne_cat said:**
> the same here ... I had to delete all applet settings:

```

gconftool-2 --recursive-unset /apps/panel/applets
```to get rid of the dot (deprecated applet).

The new mixer applet is still not in the list here ... no graphical volume control at the moment.

Phew, thanks, man.  Awesome.

When I checked the applets in gconf-editor, I found that the two I wanted to delete were applet_1 and applet_2, so I used your command :
```
gconftool-2 --recursive-unset /apps/panel/applets/applet_1
gconftool-2 --recursive-unset /apps/panel/applets/applet_2
sudo killall gnome-panel
```

And boom!  No more dots.  Thanks again.

I wonder why gconf-editor doesn't let you delete keys?  Too easy to abuse?

---

### Post by Hairy_Palms on 2009-07-25
> Sebastian Bacher has commented on that bug that it may be a duplicate of [https://bugs.launchpad.net/ubuntu/+s...ia/+bug/322909](https://bugs.launchpad.net/ubuntu/+s...ia/+bug/322909). It looks like it might be? Hairy_Palms? 
yea it is ive subscribed to the new one already,

---

