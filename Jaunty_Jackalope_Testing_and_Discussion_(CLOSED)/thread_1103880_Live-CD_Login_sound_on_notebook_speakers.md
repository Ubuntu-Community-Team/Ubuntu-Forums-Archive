---
title: "Live-CD: Login sound on notebook speakers"
date: 2009-03-23
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2009-03-23
Am I the only one that gets shocked everytime when using the Live-CD (or after a fresh install) and hearing the 100% volume login sound? My notebook speakers suck (as most notebook speakers do) so this loud login sound isn't very pleasant.

---

### Post by phenest on 2009-03-23
This is set in /etc/init.d/alsa-utils. If you unpack the live CD iso and alter this file, the rebuild the iso, et voila! It's set in the function sanify_levels_on_card().

I think this is worth mentioning to the Ubuntu devs to turn it down for us laptop users. Maybe to set the volume at the boot screen? Or just lower the volume by default?

---

### Post by MacUntu on 2009-03-23
So you think it's worth opening a bug report (for alsa-utils then)?

Edit: Ah, already there - [https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/45739](https://bugs.launchpad.net/ubuntu/+source/alsa-utils/+bug/45739)

Didn't no about the nosound kernel parameter. :)

---

