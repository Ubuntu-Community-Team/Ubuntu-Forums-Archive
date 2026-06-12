---
title: "Distorted Audio Playback"
date: 2009-05-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Nullack on 2009-05-09
Im getting sizzling crackling when playing back audio. My old fix in Jaunty doesnt work anymore with turning off all unused playback items. If I turn down the volume I get less sound level but sill distortion.

Ideas? I had hoped the new alsa and pulse versions would finally see an end to audio problems.

---

### Post by taavikko on 2009-05-10
G'day mate :)

Just tested on 
```
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

And Rhythmbox playing (.mp3) various artist, throwed in a few pauses, stopped for a while, then hitting play again.
All the channels at the max levels, Only thing I noticed was that my laptops speakers are poor quality, headphones (sennheiser hd215)
were a bit better.

But as a conclusion: Robert Plant, Ozzy, AC/DC, Kiss, etc. didn't gave any trouble.

Related to HW in use?

---

### Post by plun on 2009-05-10
Hello "downunder"

Also no problems

```
plun@plun:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [SB Audigy 2 Platinum [SB0240P]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]

```

Mplayer sound has been distorted but I just rebuilt it using [URL="http://ubuntuforums.org/showthread.php?t=1081070"]Andrews guide
[/URL]

---

### Post by dinxter on 2009-05-10
i had crackling sound since the first kernel upgrades, managed to fix it by editing '/etc/pulse/default.pa'
and changing
load-module module-hal-detect tsched=0
to,
load-module module-hal-detect 
might be worth a try, something to do with "glitch free" pulseaudio and the new kernels if i remember rightly

---

### Post by mickey57 on 2009-05-19
[COLOR="DarkRed"][SIZE="4"]I got my VLC to work by: (on the player gui)Tools/Preferences/Hit show settings-all-)/Audio/output modules/Alsa
......Click each one of those devices and see if one of them clears it up for ya..Did for me [/SIZE][/COLOR]

---

### Post by psyke83 on 2009-05-19
Nullack,

Change the resampler from src-linear to speex-float-1 in the relevant PulseAudio's configuration file (I'm not running Ubuntu at the moment, so I don't recall the proper name of the file). This solved "sizzling" audio for me (i.e., distortion at high volumes, not stuttering).

---

### Post by Naddiseo on 2009-05-19
I get stuttering when playing .wma files through rhythmbox, I've had to switch my sound to use OSS: pulse and alsa aren't working for me at the moment. I haven't really dug very deep into this since I'm happy just playing the .ogg files I have using OSS.. 

> $ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0


I'm using Card 0, device 2.

---

### Post by Nullack on 2009-05-19
> **psyke83 said:**
> Nullack,

Change the resampler from src-linear to speex-float-1 in the relevant PulseAudio's configuration file (I'm not running Ubuntu at the moment, so I don't recall the proper name of the file). This solved "sizzling" audio for me (i.e., distortion at high volumes, not stuttering).

Thanks mate. Ive done a 

```
gksudo gedit /etc/pulse/daemon.conf
```

and edited

```
resample-method = speex-float-1
```

And its *FIXED*! Your the man :) Im going to add this to the bug comments it should be default.

---

### Post by Nullack on 2009-05-19
Here's a nicely relevant bug comment from the resident master of audio:

The "src-linear" resampler (current setting in Jaunty) is really awful, too. It causes crackles for certain ranges in audio (e.g. explosions); by crackles I mean resampling artifacts, not stuttering or buffering problems. These crackles never occurred with ALSA's default dmix, and I mentioned some of my results regarding the different resamplers in the comments of bug #190754.

My understanding is that this is the rough "ranking" of resamplers, from best to worst (with CPU usage following the same trend, from high to low): src-sinc-best-quality, src-sinc-medium-quality, src-sinc-fastest, speex-float-{10-0}, speex-fixed-{10-0}, ffmpeg, src-zero-order-hold, src-linear, trivial.

As you can see, we're currently using the second-worst resampler. From personal testing, my conclusion was that speex-float-1 was the best resampler that balanced low CPU usage with audio quality (no distortion or crackles at certain ranges). For all the resamplers from speex-float-0 and below, crackles occured on both of my systems (using different codecs of snd-intel8x0).

I suggest if you have time (and find some appropriate audio samples), you test some of the resamplers to find the optimal default in PulseAudio.

---

### Post by Nullack on 2009-05-20
And a quote from Lennart where he elaborates on the default Ubuntu value in a colurful way:

"Depends on your metric do define to be 'best quality'.

Closest to mathematically perfect is src-sinc-best-quality.

src-linear is one of the crappiest. It uses linear interpolation which
is evil ****. If you consider that good quality you have a very, uh, ...
distuingished taste. ;-)

Lennart"

---

### Post by yoasif on 2009-05-20
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/376374](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/376374) you can comment on this bug.

---

### Post by Nullack on 2009-05-20
That appears to be a duplicate of a master bug on crackling that I replied too:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627)

---

### Post by psyke83 on 2009-05-20
> **Nullack said:**
> That appears to be a duplicate of a master bug on crackling that I replied too:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627)

Yes, this bug is more active and should be given priority. I would encourage this original reporter to mark it as a duplicate (I would do it, but I don't want to do so unless the reporter wants that themselves).

BTW Nullack, I added a comment re: src-linear, quoting the reply from Lennart that you posted - thanks.

---

### Post by Nullack on 2009-05-20
I made it duplicate as it cleary is.

---

### Post by dagrump on 2009-05-20
Psyke83 & Nullack, thank you! You have made hooking up the music drive worthwhile. I'm an old fool, & I was having no luck figuring out what to change. I was starting to worry, I'm prone to breaking things.
So, Thanks again!

---

### Post by psyke83 on 2009-05-20
It seems that Daniel has isolated the distortion in Karmic with src-linear into a new bug: [#376374]("https://bugs.launchpad.net/bugs/376374")

Bug [#345627]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627") is still worth watching, though.

---

### Post by Nullack on 2009-05-20
Yeah its a bit bizzare with how he wants the bugs setup, but whatever floats his boat I guess.

By the look of things he wants to move the default to ffmpeg from src-linear.

Not disrespect to Daniel, but I'm generally confused and unconvinced of the claim that we cant be "deterministic" about the correct value based on hardware queries. This is computer science afterall and not some extra dimensional illogical reality ;) Seems to me RedHat dont have such issues.

---

### Post by psyke83 on 2009-05-20
> **Nullack said:**
> Yeah its a bit bizzare with how he wants the bugs setup, but whatever floats his boat I guess.

By the look of things he wants to move the default to ffmpeg from src-linear.

Not disrespect to Daniel, but I'm generally confused and unconvinced of the claim that we cant be "deterministic" about the correct value based on hardware queries. This is computer science afterall and not some extra dimensional illogical reality ;) Seems to me RedHat dont have such issues.

Well, I would say that Daniel is doing a good job. Keep in mind that Fedora is given preferential treatment with respect to PulseAudio (presumably since it's Lennart's favoured distribution).

It's logical to split the bugs, as the src-linear resampler doesn't exhibit that horrible distortion on Jaunty. I suspect these fixes are required for Karmic: [https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-May/003704.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2009-May/003704.html)

We do need to use a different resampler by default, though!

---

### Post by Nullack on 2009-05-20
Yes hes doing a great job mate :) Im just trying to explain how I dont understand why we cant be deterministic about the default resampling value. Hardware quirks are defined into FOSS all the time. If the combination of hardware is known, and the results are testable, both premises which I submit can be logically true, then therefore you can be deterministic and offer the best audio experience out of the box to our users. In this way, audio would "just work", as does lots of other FOSS that has programmed hardware quirks.

---

### Post by vishalrao on 2009-05-21
> **psyke83 said:**
> Keep in mind that Fedora is given preferential treatment with respect to PulseAudio (presumably since it's Lennart's favoured distribution).

I believe LP works for RH so we can assume PA might work better (and sooner so) on Fedora :)

Another problem I see is Ubuntu's release schedule vs. Fedora's, Fedora releases just after Ubuntu does and many a times I've noticed stable packages come out right after Ubuntu feature freeze/release dates :) Call me a conspiracy theorist!

---

### Post by markbuntu on 2009-05-22
The use of src-linear is to reduce cpu usage and alleviate kernel issues that popped up with the attempt to use glitch-free with pulse0.9.14 in Jaunty. This is also why tsched=0 is in default.pa, it disables glitch-free mode. 

Pluseaudio 0.9.14 was strongly discouraged by lennart for use in distributions since many bugs and other issues were abandoned in the push for 0.9.15. He reccomended strongly that dstros use either 0.9.10 or 0.9.15 This is what is haunting koala.

Things are ready when they are ready and the ubuntu release schedule does not make much room for that. Besides, the way ubuntu has implemented pulse in the last three releases, no wonder lennart ignores them.

And yes, he does work for Red Hat and Fedora is red hat, but he does not work for Mandriva and they have a consistently better sound scheme than Ubuntu.

I think the big problem with Ubuntu is that some person there does not like pulseaudio and is deliberately sabotaging it. Either that or the entire ubuntu-audio team is brain dead.

Why else have pulseaudio as the default sound server and then configure the default sound scheme to create deliberate conflicts with alsa and oss applications? 

Why else would pavucontrol be excluded from the desktop seed?

If this continues into the koala release it will be the end of my attempts to bring some coherence to an increasingly insane situation.

---

### Post by Nullack on 2009-05-22
Hmmm do we have 9.14 or 9.15 in KK?:

Package libpulsecore9

    * karmic (libs): PulseAudio sound server core
      1:0.9.14-0ubuntu20: amd64 i386

Package pulseaudio

    * karmic (sound): PulseAudio sound server
      1:0.9.15-1ubuntu3: amd64 i386

For alsa:

Package alsa-base

    * karmic (sound): ALSA driver configuration files
      1.0.19.dfsg-3ubuntu1: all

Seems we have 19 and not 20 currently

---

### Post by mj_ja55 on 2009-05-28
> **Nullack said:**
> Thanks mate. Ive done a 

```
gksudo gedit /etc/pulse/daemon.conf
```

and edited

```
resample-method = speex-float-1
```

And its *FIXED*! Your the man :) Im going to add this to the bug comments it should be default.
Thanks a ton! This fixed the "sizzling" audio for me!

---

