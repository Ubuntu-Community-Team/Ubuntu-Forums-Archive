---
title: "Dosbox sound issues in Karmic"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Cihl on 2009-10-25
Hi everybody.

I think i've searched all of the forums here, and i'm having no luck so far. So i just went ahead and registered, just so i can ask myself. :)
I'm willing to report bugs if necessary, but i want to know first if i'm not doing something wrong.

Since upgrading to Karmic i've noticed that sound/music in Dosbox games doesn't behave correctly on my system. I'm hearing very annoying artifacts, like false notes (usually higher) and blips every second or so. This is common to all programs i try in Dosbox.

This problem was not here in any other version of Ubuntu.
I'm using the Ubuntu-supplied 0.73 version of Dosbox.
I changed nothing about  Pulseaudio, ALSA/OSS or anything, except turn off powersave on the sound card to eliminate loud popping sounds from the subwoofer.
Sound in any other application works just fine.

Nothing i try in Dosbox seems to help, like adjusting the cycles or trying other types of soundcards. I've tried playing with the sound settings dialog, but it doesn't make any difference.

I tried MIDI sound through Timidity too. That didn't have any artifacts, but i've actually gotten that to work only once. (but that's for another thread)

Does this sound familiar to anyone?
I'm not a Linux newbie or anything, but i could sure use some help with this one.
I'll provide any kind of information you might need to help resolve this issue.

Thanks in advance.

---

### Post by Longinus00 on 2009-10-25
I have the exact same problem on my laptop running karmic. That is an intel laptop so is running whatever intel soundchip. On my desktop with a sound blaster audigy 2 zs, I have normal sound.

I also want to add that using previous versions of dosbox (0.72) doesn't seem to have any affect.

---

### Post by rCXer on 2009-10-25
Don't have karmic but changing the sound mixer's rate might help using [these instructions](http://ubuntuforums.org/showpost.php?p=7728677&postcount=3).  Try lowering it to 11025 and if that doesn't work try raising it to 44100.

> 
I'm willing to report bugs if necessary, but i want to know first if i'm not doing something wrong.

This was already reported as [a bug](https://bugs.launchpad.net/ubuntu/+source/dosbox/+bug/429373) and we'd be glad to have your comments there if you fix it 8) Thanks!

---

### Post by Cihl on 2009-10-27
Well, the "workaround" from the bug, which means setting the sample rate to 44100, works. :-) Well. Sorta. Kinda. I think 48000 is a little better still in my situation. But it's not completely gone.
I tried compiling Dosbox myself, to see if that makes any difference. But that one just segfaults on startup. Maybe i'll try playing with the configure-flags later.

I guess i'll just have to wait what happens with that bug. Hope it gets fixed before the final release of Karmic.

---

