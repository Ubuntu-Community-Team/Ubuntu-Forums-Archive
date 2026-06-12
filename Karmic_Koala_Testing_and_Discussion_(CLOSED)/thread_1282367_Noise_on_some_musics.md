---
title: "Noise on some musics"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 013raptor on 2009-10-04
Some musics are reproduced with a lot of noise (in all the players) but in windows they're perfect. what's is going on?

---

### Post by phetre on 2009-10-04
Hi raptor013. You're using the testing version of Ubuntu, Karmic Koala, right? If so, let's try to figure out what the problem is.

1. Does the system play back sound correctly, or is it just the music players? To test this, go to Preferences/Sound, and click on a couple of the sound effects in the lower part of the window. If they play correctly, then your sound system is set up correctly. If not, there is a problem with PulseAudio or with the sound card itself.

2. What file format is the music in? Can you hear the music at all, or is it just noise? Note that "protected" wmv and m4a files (such as those purchased from iTunes and some other online music stores) are not supported in Linux, and probably never will be.

---

### Post by 013raptor on 2009-10-04
Just the musics, and it seems to me it's only the in .mp3, the ones that are in .flac plays perfectly.

And I can hear the musics the noise comes just in some frequencies.

---

### Post by phetre on 2009-10-05
Hmm! That's very strange: which players have you tried? Different music players may share the same backend (such as Gstreamer), so if you get bad results with Totem, Rhythmbox, Banshee, and Songbird (all of which use Gstreamer), you might try Mplayer, Amarok, or VLC (which use different backends).

Sorry I can't be more specifically helpful. This seems unlikely to be a Windows/Linux issue; it's more likely that these particular MP3s are causing problems with a specific decoding library. Do you know which program was used to encode them?

---

### Post by 013raptor on 2009-10-17
I've already tried with VLC and still the same. I think it's not hardware issue, I tested in my old computer and the problem was there too.

---

### Post by kostkon on 2009-10-17
You could try [*MP3 Diags*]("http://mp3diags.sourceforge.net/"). It will identify and fix any errors that your files may have.

You can install it from the repos.

---

### Post by 013raptor on 2009-10-18
But this program fixes the musics, the problem is not in the files.

---

### Post by jongkind on 2009-10-18
> **013raptor said:**
> Some musics are reproduced with a lot of noise (in all the players) but in windows they're perfect. what's is going on?

I encounter a comparable problem with Banshee (equalizer on). With Rhythmbox I don't have this problem.

---

### Post by lucanuscervus on 2009-10-26
Same problem with Amarok 1.4.10/2.2 on 9.10 RC.
Also, films in SMplayer sounds really bad. There is a sort of metallicnoise at the background

---

