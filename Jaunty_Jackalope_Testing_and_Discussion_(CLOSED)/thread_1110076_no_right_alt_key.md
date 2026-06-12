---
title: "no right alt key"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by canabal on 2009-03-29
Hey all,

I upgraded to Jaunty a few days ago and have been missing the right alt key (alt_r).

When I look at the keyboard layout it is "ISO..." and I cannot figure out how to change it back.

A screenshot is attached to show what I mean.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=107987&stc=1&d=1238346752[/IMG]

Thanks in advance.

---

### Post by canabal on 2009-03-30
bump for the weekday crowd.  Probably something simple.

---

### Post by scaine on 2009-03-30
I've only got access to Intrepid right now, but this is easily changed (on Intrepid) by going to system/preferences/keyboard and choosing the "layout" tab and selecting a "keyboard model" appropriate to your keyboard/laptop.

I can check tonight how this has changed on Jaunty.

---

### Post by canabal on 2009-03-30
I originally had the generic one and switched to the dell D630 to attempt to get it working.

After switching to a bunch of others it looks like it says ISO_left on that key, but it still will not switch to alt.

---

### Post by canabal on 2009-03-31
Anyone else have ideas?

I never realised how much I used that key until it was missing.

---

### Post by scaine on 2009-03-31
Is there anything in "layout options" that might help?

---

### Post by canabal on 2009-03-31
> **scaine said:**
> Is there anything in "layout options" that might help?

Already tried that, no luck.

---

### Post by knarf on 2009-03-31
Look in *System->Preferences->Keyboard*, *Layouts* tab, press '*Layout Options*' button (bottom right) and check the value of the '*Key to choose 3d level*'. This is most likely set to '*Right Alt*' while you want it set to '*Right Alt key never chooses 3d level*'...

---

### Post by portis on 2009-03-31
> **knarf said:**
> Look in *System->Preferences->Keyboard*, *Layouts* tab, press '*Layout Options*' button (bottom right) and check the value of the '*Key to choose 3d level*'. This is most likely set to '*Right Alt*' while you want it set to '*Right Alt key never chooses 3d level*'...

It works! Great. Thanks so much.

---

### Post by canabal on 2009-03-31
Perfect, thank you.  Is this a bug I should submit a report about?

---

### Post by knarf on 2009-04-01
I don't think so, it is just a default configuration which does not suit some people. I use Right_Alt als Compose to get at the äöïëüøå&#616; and such so I'd have to reconfigure it anyway, no matter what default was chosen...

---

