---
title: "Synaptics Touchpad"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TrevT93 on 2010-03-20
Hi all.  After an upgrade to Xubuntu Lucid, my touchpad is back to its aggravating behavior that I had to previously fix in HAL.  In order to stop the vertical scroll zone from taking up literally half my touchpad, I had to add the 11-x11-synaptics.fdi file to /etc/hal/fdi/policy and then modify it.  It is also located in /usr/share/hal/fdi/policy/10osvendor.

But doing this does not work in Lucid (did they really fully remove HAL, because if so, then this would suddenly make a lot of sense).

Anyone find a fix for this?  I'm almost sure you haven't, because my laptop seems to be the only one that has this weird behavior, but does anyone at least have a theory?

Any help is appreciated :) .

---

### Post by TrevT93 on 2010-03-20
Technically, I'm really not supposed to post twice in a row, but the issue I worked out: I de-commented an old section for the touchpad in my xorg.conf which was commented out by update-manager since it's supposed to be HAL controlling touchpad behavior.

But before I mark this solved, **should** I need to do this?  Is there a better way?  And can I get rid of HAL since it doesn't seem to be doing anything?

---

