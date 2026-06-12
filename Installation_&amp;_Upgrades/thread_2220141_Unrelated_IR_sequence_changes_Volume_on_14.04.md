---
title: "Unrelated IR sequence changes Volume on 14.04"
date: 2014-04-26
forum: Installation &amp; Upgrades
---

### Post by kmand on 2014-04-26
I just upgraded from 12.04 to 14.04. I use an IR remote to control a media player program with lirc. It worked fine on 12.04 and still works fine on 14.04. The problem is that one of the sequences has started changing the volume. None of these IR codes map to anything used for volume by lirc.

 Its not related to lirc or the media player, because I can shut down lircd and the media player and the sequence still causes the desktop volume control to popup with each press lowering the volume on the slider.

There must be some other service reading the IR on 14.04. How can I disable it? 

By the way this is on an old Mac mini using its internal ir receiver.

---

### Post by kmand on 2014-04-28
I figured out a workaround, by using xmodmap to remap the keycode with keysym XF86AudioLowerVolume. This effects all the keyboards not just the IR device I use with lirc. I can live with that.

The better way would apparently be to disable the Xinput from the IR device. I tried that but it had no effect.

---

### Post by kmand on 2014-04-28
duplicate, sorry.

---

