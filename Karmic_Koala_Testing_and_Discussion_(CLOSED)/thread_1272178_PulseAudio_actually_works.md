---
title: "PulseAudio actually works?"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SuicideSmurf on 2009-09-21
Wow, didn't expect this but everything works smoothly in Alpha 6 on the sound side.

Better late than never! :popcorn:

---

### Post by gagnon88 on 2009-09-21
Same here, much improvement on the Pulseaudio side.

---

### Post by caish5 on 2009-09-21
5.1? i haven't had that since hardy!

---

### Post by Visceral Monkey on 2009-09-21
Alas, my 5.1 with x-fi is stuttery and scratchy for some reason :(

---

### Post by lswb on 2009-09-21
> **SuicideSmurf said:**
> Wow, didn't expect this but everything works smoothly in Alpha 6 on the sound side.

Better late than never! :popcorn:

It's only alpha, not too late to screw it up yet!

---

### Post by VMC on 2009-09-22
Mine has never stopped working. But each time someone brings this topic up it reminds to turn on some music - which I'm listening to right, just so I can be reassured that it still works.

I suppose it depends on your hardware, of course.

---

### Post by trulan on 2009-09-22
Same here, mine has never quit working.  The closest to that was when it would always mute when you closed a window.  Now that was fun!

---

### Post by oasick on 2009-09-22
I have a very distorted sound and I can't adjust the volume...

---

### Post by Tibuda on 2009-09-22
> **VMC said:**
> Mine has never stopped working. But each time someone brings this topic up it reminds to turn on some music - which I'm listening to right, just so I can be reassured that it still works.

I suppose it depends on your hardware, of course.

Yes, I suppose it is hardware-related. Never had any issue with sound since Gutsy.

---

### Post by knarf on 2009-09-22
On systems which do not support SSE2 but do support SSE/MMX there currently seems to be a bug in the volume/mixer code which causes distorted sound on anything but maximum volume: [#428619]("https://launchpad.net/bugs/428619"). I made a [patch]("http://launchpadlibrarian.net/32144505/revert_svolume_mmx_to_known_good_version.patch") which fixes this for < SSE2 systems. As I do not have anything available which does support SSE2 I can not test whether this patch also fixes the reported problem on one of those.

---

