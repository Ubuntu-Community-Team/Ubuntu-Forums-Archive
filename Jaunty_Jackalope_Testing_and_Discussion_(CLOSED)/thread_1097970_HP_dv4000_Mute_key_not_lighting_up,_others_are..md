---
title: "HP dv4000 Mute key not lighting up, others are."
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by kyleabaker on 2009-03-16
I've had this problem for a long time now over several versions of Ubuntu (back to Hardy).

My HP dv4000 has blue lights on the following keys: Power, DVD, Music, Volume Down, Mute Toggle, Volume Up

All of the blue lights have worked fine for all of them except for the Mute Toggle button. I suspect it is because this is the only key with a light that has a reason to turn on and off.

The Mute key works as expected with Ubuntu, but the light does not turn on and off. I was wondering if anyone had any idea of where I could look to get this fixed or a file that is in control of this behavior?

Hoping to get this little annoyance fixed. Thanks in advanced.

---

### Post by crimsun on 2009-03-16
Please file a bug affecting the `linux' source package, and attach output from running [http://www.alsa-project.org/alsa-info.sh](http://www.alsa-project.org/alsa-info.sh) on your local machine.

---

### Post by kyleabaker on 2009-03-28
@crimsun
It's been reported several times and I'm not interested in putting the work on a group that isn't interested in fixing it or who don't have time for it. I'd rather take a look at it myself if I can get pointed towards the correct files. I think it's related to the key map more than alsa. I could be wrong, but it is the actual key that's not lighting up when mute is on.

@anyone
Anyone know what files I need to take a look at to try to get the mute light to toggle on and off with mute?

---

