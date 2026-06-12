---
title: "Pulseaudio and Wine really don't want to play"
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tghe-retford on 2009-07-24
Noticed after a reinstall of Karmic Alpha 2 (updated to Alpha 3 since) that Wine and Pulseaudio will simply not work together under any circumstances. No matter what audio device I choose or what I do, Pulseaudio simply refuses to acknowledge Wine's existence. I did managed to get sound earlier in Karmic's development, but since the reinstallation, absolutely nothing.

Nothing of relevance to any sound problems comes up if I run winecfg or any wine application.

Someone did a bug report on this problem, but I am just wondering why Pulseaudio simply refuses to have anything to do with Wine when it worked with Karmic in the past and whether this is going to be rectified before Karmic goes public later this year?

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/355377](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/355377)

---

### Post by plun on 2009-07-24
I am running Spotify with Wine and I must use [pavucontrol]("http://packages.ubuntu.com/karmic/pavucontrol") for adjusting sound from Wine

---

### Post by psyke83 on 2009-07-24
> **tghe-retford said:**
> Noticed after a reinstall of Karmic Alpha 2 (updated to Alpha 3 since) that Wine and Pulseaudio will simply not work together under any circumstances. No matter what audio device I choose or what I do, Pulseaudio simply refuses to acknowledge Wine's existence. I did managed to get sound earlier in Karmic's development, but since the reinstallation, absolutely nothing.

Nothing of relevance to any sound problems comes up if I run winecfg or any wine application.

Someone did a bug report on this problem, but I am just wondering why Pulseaudio simply refuses to have anything to do with Wine when it worked with Karmic in the past and whether this is going to be rectified before Karmic goes public later this year?

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/355377](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/355377)

You should:
[LIST]
[*]ensure you've got the latest version of WINE (in Karmic, the package is now called wine1.2).
[*]set the ALSA driver with the default driver options in your winecfg Audio setup.
[*]make sure that PulseAudio works for other ALSA applications. For example, if you run ```
$ mplayer -ao alsa /some/file.mp3
```
...the PulseAudio Volume Control playback tab should say "mplayer [ALSA]", which indicates that the ALSA PulseAudio plugins are working. Just because Totem, Rhythmbox etc., plays sound, **does not** mean that PulseAudio is fully configured, as GStreamer applications output directly to the PulseAudio server.
[/LIST]

Here's what you need to keep in mind:
[LIST]
[*]That bug report is for a user running Jaunty (PulseAudio 0.9.14 is the version in Jaunty, and TheMuso's PPA packages are for Jaunty only).
[*]Older versions of WINE aren't particularly PulseAudio-friendly (which applies to that report).
[/LIST]

---

### Post by tghe-retford on 2009-07-24
> **plun said:**
> I am running Spotify with Wine and I must use [pavucontrol]("http://packages.ubuntu.com/karmic/pavucontrol") for adjusting sound from Wine
Pavucontrol and the new Volume Control (in the applications tab) won't even acknowledge the existence of Wine when I ran Kega Fusion and Spotify.

Everything is setup fine and did work with psyke83's suggestion to check if ALSA works with other applications.

---

### Post by no1wantdthisname on 2009-07-24
I have the same issue.
Wine doesn't work through pulseaudio until I do:

```

sudo alsa force-reload

```

I have to do that every reboot.

---

### Post by psyke83 on 2009-07-24
tghe-retford,

Are you using the 64-bit release? It may be a problem with the 32 bit lib32asound2 libraries, or something similar.

---

### Post by nystire on 2009-07-25
> **psyke83 said:**
> You should:
[LIST]
[*]ensure you've got the latest version of WINE (in Karmic, the package is now called wine1.2).
[/LIST]
...


Not confusing at all... :)

Why did they simply not update the package, instead of adding a new, duplicate package?

---

### Post by tghe-retford on 2009-07-25
> **psyke83 said:**
> tghe-retford,

Are you using the 64-bit release?
Yes I am.

---

### Post by tghe-retford on 2009-07-25
> **no1wantdthisname said:**
> I have the same issue.
Wine doesn't work through pulseaudio until I do:

```

sudo alsa force-reload

```

I have to do that every reboot.
That gets sound back, but now I notice Kega Fusion is running 80% slower according to its fps counter (10-15fps) after running that command. This didn't happen before, it used to run at full speed (60fps) with sound.

---

### Post by aamukahvi on 2009-07-25
> **nystire said:**
> Not confusing at all... :)

Why did they simply not update the package, instead of adding a new, duplicate package?

Maybe because the stable version is still 1.0 but they also wanted to have 1.2?

---

### Post by nystire on 2009-07-25
This isn't a LTS version, so why be timid? :)

---

### Post by kaitwospirit on 2009-07-25
I get sound running wine applications but it's choppy - it sounds basically like about every second the sound is pausing. It's really weird.

---

### Post by psyke83 on 2009-07-25
> **kaitwospirit said:**
> I get sound running wine applications but it's choppy - it sounds basically like about every second the sound is pausing. It's really weird.

Yes, this is because PulseAudio in Karmic is not yet configured correctly, which causes very choppy audio in certain applications such as Skype and WINE. You can try to manually enable glitch-free playback. However, unless your audio card's kernel driver is compatible, this will make things worse. You've been warned.

See: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627/comments/132](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/345627/comments/132)

---

### Post by OliW on 2009-08-04
Well unless I am mistaken, glitch-free has now been enabled again.

A week ago, sound from Wine-run apps worked fine. Now it doesn't. Yey.

---

### Post by OliW on 2009-08-05
The fix that worked for me is a little complicated. But it works. (I had exactly the same symptoms as you had)

As 64bit users, we're missing a 32bit copy of libasound_module_pcm_pulse.so for some unknown reason. Copying/symlinking from the 64bit libs won't work so here's how you get a 32bit version for your /usr/lib32

[LIST=1]
[*]via the package search, find and download the 32bit version of alsa-utils
[*]extract libasound_module_pcm_pulse.so
[*]sudo cp it to /usr/lib32/alsa-lib
[*]bask in the glory of your unlimited powar
[/LIST]

Okay it's not that complicated but now you have a shared library that will expire and you will have to keep replacing as updates to alsa-lib are provided.

---

### Post by aamukahvi on 2009-08-05
> **OliW said:**
> The fix that worked for me is a little complicated. But it works. (I had exactly the same symptoms as you had)

As 64bit users, we're missing a 32bit copy of libasound_module_pcm_pulse.so for some unknown reason. Copying/symlinking from the 64bit libs won't work so here's how you get a 32bit version for your /usr/lib32

[LIST=1]
[*]via the package search, find and download the 32bit version of alsa-utils
[*]extract libasound_module_pcm_pulse.so
[*]sudo cp it to /usr/lib32/alsa-lib
[*]bask in the glory of your unlimited powar
[/LIST]

Okay it's not that complicated but now you have a shared library that will expire and you will have to keep replacing as updates to alsa-lib are provided.
Can you please file a bug and post your fix there? it would be nice to have it fixed in packaging :)

---

### Post by Kazade on 2009-08-05
> **nystire said:**
> This isn't a LTS version, so why be timid? :)

[This it explains it in detail.]("http://yokozar.org/blog/archives/103")

---

### Post by OliW on 2009-08-05
> **aamukahvi said:**
> Can you please file a bug and post your fix there? it would be nice to have it fixed in packaging :)

[https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/409250](https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/409250)

---

### Post by aldursys on 2009-08-09
Hi,

I've put together a version of the wine1.2 package that includes the native PulseAudio wine driver.

If you are testing the Karmic release and having problems with Wine sound can you try this package and see if it improves matters.

See: [https://bugs.launchpad.net/wine/+bug/371897/comments/10](https://bugs.launchpad.net/wine/+bug/371897/comments/10)

---

