---
title: "disable touchpad in 18.10"
date: 2018-11-28
forum: Installation &amp; Upgrades
---

### Post by bob brazie on 2018-11-28
After an upgrade today. There seems to be no way to disable the touch pad in 18.10.
There was an option in the settings/devices but it seems to have disappeared after this upgrade...
Any other way to disable it? And why did this change?
Thanks in advance. Bob.

---

### Post by MoebusNet on 2018-11-28
You don't say what Desktop Environment you're using (it makes a difference), but in Lubuntu 18.04 I was able to disable tap-to-click and disable touchpad while typing by editing '~/.config/lxsession/Lubuntu/autostart' with ```
synclient MaxTapTime=0
syndaemon -d -t
``` as advised at [https://help.ubuntu.com/community/Lubuntu/Mouse#Disable_tap_to_click](https://help.ubuntu.com/community/Lubuntu/Mouse#Disable_tap_to_click)

Perhaps something similar is available for your Desktop Environment.

---

### Post by bob brazie on 2018-11-28
Sorry, I thought I clicked on the Ubuntu at the top of a new post.
Any way I am using Ubuntu 18.10. It used to have an option to d that in settings.

---

### Post by MoebusNet on 2018-11-29
I realized that I don't know enough to advise you properly how to do this; I would only be repeating Google search results. I think a little searching and cautious experimentation can fix this for you, but I can't advise a specific fix. Sorry 'bout dat!

---

### Post by bob brazie on 2018-11-29
Not to worry. Anyone else know a solution?

---

