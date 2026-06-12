---
title: "Removing Evolution"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by Foster Grant on 2008-04-23
Not really an installation or an upgrade, but removal is the flip side of that coin so I figured this would be the best place to ask.

The short version is this: I'm a longtime Thunderbird/Lightning user. I tried Evolution for a week and found that it's not as much to my liking as Thunderbird/Lightning and I don't need the groupware tools. I'd like to take Evolution out, but when I try to remove some of the extra Evolution pieces I'm told I can't do it without removing [COLOR="Red"]gnome-desktop[/COLOR]. For obvious reasons, this sounds like a bad idea.

How much of Evolution (and which components in particular) can I safely remove without corrupting my Gutsy/GNOME installation?

Thanks in advance. :)

---

### Post by justin whitaker on 2008-04-24
> **Foster Grant said:**
> Not really an installation or an upgrade, but removal is the flip side of that coin so I figured this would be the best place to ask.

The short version is this: I'm a longtime Thunderbird/Lightning user. I tried Evolution for a week and found that it's not as much to my liking as Thunderbird/Lightning and I don't need the groupware tools. I'd like to take Evolution out, but when I try to remove some of the extra Evolution pieces I'm told I can't do it without removing [COLOR="Red"]gnome-desktop[/COLOR]. For obvious reasons, this sounds like a bad idea.

How much of Evolution (and which components in particular) can I safely remove without corrupting my Gutsy/GNOME installation?

Thanks in advance. :)

Is it trying to dump GNOME-Desktop-Data, or GNOME Desktop Environment?

---

### Post by Foster Grant on 2008-04-24
I apologize; bad error code. (I was working from memory; damn senility setting in! :D )

Attempting to remove [COLOR="Red"]evolution-webcal[/COLOR] makes Synaptic offer to remove [COLOR="Red"]ubuntu-desktop[/COLOR].

---

### Post by Ghostlove on 2008-04-26
Use Synaptic Package Manager to remove Evolution. It's one of the first things I remove after a fresh install and this hasn't failed yet. :)

---

### Post by CREEPING DEATH on 2008-04-26
It's just removing a metapackage, not Ubuntu or Gnome.  It's OK to do!

CD

---

