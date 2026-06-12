---
title: "Getting 5.1 surround sound work on Karmic"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by pappfer on 2009-10-09
Getting 5.1 surround sound to work under Jaunty was the easiest I've ever seen so far. I just set a checkbox at sound preferences input tab (set mic as output) and it was working awesome. I miss this feature in Karmic's sound preferences. The most I could get out from it was setting the sound profile to surround 4.0 output but my rear speakers don't work this time.

Are they removed the "set mic as output" feature? Is it possible to get 5.1 sound work without having to edit any files or so?
I really hope that I'm just missing something and the developers didn't remove this great feature from Karmic.

---

### Post by ranch hand on 2009-10-09
What card have you got?

What mixer are you using?

---

### Post by emarkay on 2009-10-09
To the best of my ears I have full AC97 5.1 sound. 

I have a Windows based "sound tester" that confirms this,  as well as the same videos using VLC, they sound the same 

Anyone know of a sound card/multimedia tester for  Ubuntu?

---

### Post by ranch hand on 2009-10-09
Just run;
```

lspci

```
That should list it.

---

### Post by emarkay on 2009-10-09
> **ranch hand said:**
> Just run;
```

lspci

```That should list it.

That just ID's what's "plugged in" but doesn't confirm the operation of it - I think the OP wants to know if and how to confirm/and use Surround Sound.

---

### Post by ranch hand on 2009-10-09
And that depends on the mixer he is using, which depends on the card.

For instance, I have an old Audigy1 card and it works great.  As long as you are using the gnome-alsamixer.

---

### Post by dreamkin on 2009-10-10
Similar problem here. 

I have an Audigy 2 ZS, hooked to a 7.1 analog speaker set.

With 9.04 getting surround sound was easy. I had to select drivers manually from the Sound menu. (OSS usually worked. ALSA would produce surround sound too but would make sound crash either entirely or wasn't able to play anything if I played sound from two different sources.)

The Sound setup defulted to the ALSA mixer. But I  could select default mixer type too.

Now in Karmic that menu is gone. Instead we have the new GNOME volume sound control. Even if I download and use the ALSA mixer, this time Karmic defaults to Sigmatel type mixer (instead of plain Audigy ZS mixer) And the Sigmatel mixer somehow reports volumes wrongly. 

The notifier shows the sound is 1/4 way down but everything becomes muted at that point. No other hardware is shown. 

Is there a way to use the old Sound menu from Jaunty to set up sound. This made me switch to Kubuntu which so far operates sound perfectly.

---

### Post by pappfer on 2009-10-10
I don't have a clue what mixer I'm using. It's not written in sound preferences anywhere.

At hardware tab I selected "Analog Surround 4.0 Output" which makes all my speakers work but the rear ones.
I also tried to set "Analog Surround 4.0 Output + Analog Stereo Input" profile and was expecting that at the input tag I'll see something like "set mic as output" as it was under Jaunty but this feature is missing there.

I have a Sigmatel HD audio sound card which is not a proper 5.1 sound card but by software I could make all my speakers work before (setting mic as output).

---

### Post by Longinus00 on 2009-10-10
> **emarkay said:**
> To the best of my ears I have full AC97 5.1 sound. 

I have a Windows based "sound tester" that confirms this,  as well as the same videos using VLC, they sound the same 

Anyone know of a sound card/multimedia tester for  Ubuntu?

```
speaker-test -c6 -twav
```

Change the value of c to the number of channels.

---

### Post by ranch hand on 2009-10-10
> **pappfer said:**
> I don't have a clue what mixer I'm using. It's not written in sound preferences anywhere.

At hardware tab I selected "Analog Surround 4.0 Output" which makes all my speakers work but the rear ones.
I also tried to set "Analog Surround 4.0 Output + Analog Stereo Input" profile and was expecting that at the input tag I'll see something like "set mic as output" as it was under Jaunty but this feature is missing there.

I have a Sigmatel HD audio sound card which is not a proper 5.1 sound card but by software I could make all my speakers work before (setting mic as output).
Well, I am on Jaunty right now but I don't think that I would be much help anyway.  My old Audigy1 card works great under 9.10 with the gnome-alsamixer.

I am sure that there are 2 options in preferences (9.10 gnome-alsamixer has these under "edit") that you may want to try.  One is for external amplifier and the other for 4 speaker stereo.

---

### Post by emarkay on 2009-10-10
> **Longinus00 said:**
> ```
speaker-test -c6 -twav
```Change the value of c to the number of channels.

[http://linux.die.net/man/1/speaker-test](http://linux.die.net/man/1/speaker-test)
[http://www.mythtv.org/wiki/Using_ALSA%27s_speaker-test_utility](http://www.mythtv.org/wiki/Using_ALSA%27s_speaker-test_utility)
[http://alsa.opensrc.org/index.php/Speaker-test#A_5.1_speaker_setup_from_three_stereo_jacks](http://alsa.opensrc.org/index.php/Speaker-test#A_5.1_speaker_setup_from_three_stereo_jacks)

and files:
[http://www.kellyindustries.com/sounds.html#dts_downloads](http://www.kellyindustries.com/sounds.html#dts_downloads)
[http://forums.guru3d.com/showthread.php?t=279980](http://forums.guru3d.com/showthread.php?t=279980)
[http://uk.cinenow.com/](http://uk.cinenow.com/)
[http://elsmar.com/pdf_files/THX%20Dolby%20-%20Air%20Raid%20Surround%20Sound%20Test.mp3](http://elsmar.com/pdf_files/THX%20Dolby%20-%20Air%20Raid%20Surround%20Sound%20Test.mp3)
[http://www.gametrailers.com/user-movie/dolby-surround-sound-test/198448](http://www.gametrailers.com/user-movie/dolby-surround-sound-test/198448)
[http://digital-audio.net/sounds_o.shtml](http://digital-audio.net/sounds_o.shtml)
[http://www.digital-digest.com/dvd/downloads/trailers.html](http://www.digital-digest.com/dvd/downloads/trailers.html)
[http://www.microsoft.com/windows/windowsmedia/democenter/9series/avquality/wmapromp3/clips/EnablingMultichannelTutorial.asx](http://www.microsoft.com/windows/windowsmedia/democenter/9series/avquality/wmapromp3/clips/EnablingMultichannelTutorial.asx)
[http://www.microsoft.com/windows/windowsmedia/musicandvideo/hdvideo/contentshowcase.aspx](http://www.microsoft.com/windows/windowsmedia/musicandvideo/hdvideo/contentshowcase.aspx)
[http://www.virtualworlds.de/AudioCutter/download.php](http://www.virtualworlds.de/AudioCutter/download.php)
[http://www.lynnemusic.com/surround.html](http://www.lynnemusic.com/surround.html)

I think that's a good start, and no I haven't heard all these, but the links ARE good.


In SURROUND!              :guitar::guitar::guitar::guitar::guitar:

---

### Post by pappfer on 2009-10-11
What is the default sound in Karmic? Alsa or Pulseaudio?

Is there any way to make my mic as output (so that all of my speakers would work) like it was possible in Jaunty?

---

### Post by pappfer on 2009-10-12
> **pappfer said:**
> What is the default sound in Karmic? Alsa or Pulseaudio?

Is there any way to make my mic as output (so that all of my speakers would work) like it was possible in Jaunty?
At processes I see PulseAudio running, so I think I just answered my first question. :)

But still wondering about the other question.

---

