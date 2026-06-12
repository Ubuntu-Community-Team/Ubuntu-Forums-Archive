---
title: "Keyboard shortcuts not being saved."
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Longinus00 on 2009-09-18
I'm trying to assign keyboard shortcuts for switching workspaces and I'm finding that they're not being saved after log out. Another problem I'm having is that there's only 2 workspaces listed in the gnome keyboard shortcut editor even though I have 4 set up in the workspace switcher. I've tried setting the shortcuts via the compizconfig setting manager but they don't get saved either. Assigning them manually via gconf-editor doesn't save them between logouts either. Anybody else have this problem?

---

### Post by FatalChaos on 2009-09-19
I'm having this same problem and can't figure out the cause, but it doesn't seem to be for every shortcut. Mine won't save for open a terminal, but it will save for hide every window and focus on desktop.

---

### Post by MKdx on 2009-09-19
I had this issue as well for about a week.

This might be related:
[https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/432633](https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/432633)

The workaround on LP could be what did it for me, as I didn't update that day... but it sounds flaky, as you only have to choose "None" once and reboot, regardless of what you set the effects option later to.

---

### Post by Longinus00 on 2009-09-19
I've noticed that keyboard shortcuts in compiz for switching desktops (via the desktop cube shortcuts) also don't get saved between logouts. I'm guessing that something is opening the keyboard settings at login and not letting go of the file handle until gdm logs out. Thus all the saves that happen to the file while you're logged in get reverted. Since this doesn't seem to happen if no compositing is enabled, perhaps it's a bug in compiz?

---

### Post by MKdx on 2009-09-20
It could very well be a compiz issue.

Here's another LP entry today:
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/433424](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/433424)

But I'm wondering why it doesn't seem to affect that many people - not here and not in LP. It seems like some specific combination is what triggers the behavior.

---

### Post by Longinus00 on 2009-09-21
Just got done talking with Travis Watkins and I think he figured out what was wrong.

[https://bugs.edge.launchpad.net/ubuntu/karmic/+source/gnome-session/+bug/430981/comments/14](https://bugs.edge.launchpad.net/ubuntu/karmic/+source/gnome-session/+bug/430981/comments/14)

Hopefully this means we'll see a patch in the not too distant future.

---

### Post by Amaranth on 2009-09-21
It's really rather obvious what happened after you bash your head into a wall a couple times. ;)

Thanks again Longinus for the assistance.

---

