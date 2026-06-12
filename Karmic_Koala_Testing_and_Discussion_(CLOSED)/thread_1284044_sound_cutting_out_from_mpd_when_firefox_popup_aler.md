---
title: "sound cutting out from mpd when firefox popup alert happnes"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sonicb00m on 2009-10-06
I noticed that firefox is playing a stupid sound everytime it alerts me of something (the login sound to be precise).

Now it's stopping mpd from playing and I have to restart the mpd server ever time.

How do i reconfigure this intrusive stupidness the developers keep insisting on that is apparently "for my benefit".

---

### Post by sonicb00m on 2009-10-06
looks like mpd isn't running through pulse even though it's set to "pulse" on it's output.

Can't run paprefs to set networking settings for pulse either.

---

### Post by sonicb00m on 2009-10-06
reboot fixed the paprefs problem and now mpd is working with pulse ok

---

### Post by Karaden on 2009-10-07
Did you manage to find out how to stop the sound from playing when the alerts happen? I'd rather like to get rid of it too.

---

### Post by sonicb00m on 2009-10-07
the problem is that mpd was not actually running through pulse properly. i went to paprefs and checked the boxes about access to the local network and not requiring authentication. then when i checked the applications running through pulse mpd appeared with a volume slider. After this i had no further problem and the sounds mixed.

---

### Post by Karaden on 2009-10-07
Cheers for the reply! Ah, so Firefox is still playing the noise, it's just not interfering with mpd any more?

I'd still like to find out how to stop the noise from playing at all, though. It's not interfering with anything for me, it's just irritating.

---

### Post by sonicb00m on 2009-10-08
yeah it bugs me too. if you find out post it here!

---

### Post by phetre on 2009-10-08
Glad to meet another MPD user! Try changing or muting the alert in the Sound preferences panel (of GNOME, that is--not Firefox).

System/Preferences/Sound: Sound Effects/Alert Volume

---

