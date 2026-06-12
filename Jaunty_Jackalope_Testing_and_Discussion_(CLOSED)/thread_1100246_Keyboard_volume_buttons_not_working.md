---
title: "Keyboard volume buttons not working"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mazen on 2009-03-19
I'm using 9.04 and the keyboard shortcuts were working fine  but stoped after to an update.
when i press the volume buttons i see the notification popup but it doesn't change the sound, is there a way to edit what the buttons control?
Thanks

---

### Post by cariboo on 2009-03-19
I've asked the mods to move this to the [thread=352]Jaunty[/thread], as you will probably get better help there. It sounds like your problem is more audio related then a keyboard problem.

Jim

---

### Post by bapoumba on 2009-03-19
So moved, thanks cariboo907 :)

---

### Post by CrashTest71 on 2009-04-07
I've got the same problem.  Push the Volume up/down, or Mute, (any of my media keys) on my keyboard the on-screen notify pops up and changes state, but the actual sound volume does not change.

Am I the only one?  I can't find any bug report for it.

---

### Post by CrashTest71 on 2009-04-07
Do the keyboard media keys work for other Jaunty users?

---

### Post by eluminx on 2009-04-07
i got the same problem but when i look at my volume slide on the volume properties it seems like the slider doesn't go all the way down, but on the notification pop up it does.  In other words when i use my volume keys the slider (on the volume properties) moves, but it gets gets to about 25% low volume and then if i press the down volume one more time it mutes the audio.  But if i move the slider with the mouse once i get to that 25% and i keep moving it with the mouse the volume then starts to get lower.

Hopefully this makes sense.  One more thing, if i use my volume keys for the rest of that 75% or "loud" volume the audio is not affected at all.  So the only two options i have when using my keys is audio or mute.

---

### Post by robinl on 2009-04-07
Works fine on fine.

---

### Post by Languid Heap on 2009-04-07
> **Mazen said:**
> I'm using 9.04 and the keyboard shortcuts were working fine  but stoped after to an update.
when i press the volume buttons i see the notification popup but it doesn't change the sound, is there a way to edit what the buttons control?
Thanks

Try:

System > Preferences > Sound > Device Tab

Then at the bottom under "Default Mixer Tracks", make sure one of the tracks is highlighted (for example Master or PCM). I had the same problem and realized that somewhere along the way, I had un-selected a track in this window.

Otherwise, try:

System > Preferences > Keyboard Shortcuts

Good Luck!

---

### Post by CrashTest71 on 2009-04-07
> **Languid Heap said:**
> Try:

System > Preferences > Sound > Device Tab

Then at the bottom under "Default Mixer Tracks", make sure one of the tracks is highlighted (for example Master or PCM). I had the same problem and realized that somewhere along the way, I had un-selected a track in this window.



Cheers!  That fixed it for me.  

Changed it to the Alsa mixer device and chose the Master track.  Now Volume up/down and Mute work.

Cheers again. :D

---

