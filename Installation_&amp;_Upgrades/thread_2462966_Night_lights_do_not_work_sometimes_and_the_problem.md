---
title: "Night lights do not work sometimes and the problem persists until booted again."
date: 2021-05-31
forum: Installation &amp; Upgrades
---

### Post by EngineerStrange on 2021-05-31
I am having a bug of night light not working after boot sometimes, occurred twice so far. What can I do?  I suspect that it is after any of the recent updates as I have never encountered it in my life earlier. I am in Ubuntu 20.04.1.

---

### Post by corradoventu on 2021-05-31
If you don't describe your problem nobody can help.

---

### Post by ajgreeny on 2021-05-31
I don't use gnome and do not know night-light but I presume it must have some way to edit the settings or preferences for your system.

Assuming I am correct about this tell us what those settings are and we may be able to help more.

---

### Post by dddman on 2021-05-31
Try manually setting the time

[ATTACH=CONFIG]288586[/ATTACH]

you may like this
[https://extensions.gnome.org/extension/1276/night-light-slider/](https://extensions.gnome.org/extension/1276/night-light-slider/)

---

### Post by grahammechanical on 2021-05-31
Here are the settings;

A Night light slider from Off to ON
Schedule: Sunset to Sunrise or Manual schedule
Times:   Where we can set a From time and a To time.
Colour Temperature: Less warm - More warm. 

The default setting gives distinct orange colour to the screen. Moving the range to Less warm lightens up the orange colour. Moving the range to More warm will surely make the orange colour deeper. It is like viewing the screen through a sand storm.

I have only activated the thing 5 minutes ago and already I am falling asleep! Mind you it is almost midnight in the UK. I am going to switch over to watching the news channel. The news is scary enough to wake anybody up.

Regards

---

### Post by Dennis N on 2021-05-31
Sunset to Sunrise schedule requires Location Services (uses geoclue) to be ON. Check the on/off times in Display > Night Light next time it fails to come on and see if the correct times have been obtained for your location. If this happens only rarely, Location Services may be occasionally failing to get the right times on startup. So see if that's the case or not.

---

