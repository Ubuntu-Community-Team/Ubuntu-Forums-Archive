---
title: "Dell XPS M1330 and the sliders in every single damn volume applet"
date: 2009-04-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cfogelberg on 2009-04-14
Hello all,

With a lot of help from nwadams I've managed to mostly resolve the problems I had with my internal mic (see here: [http://ubuntuforums.org/showthread.php?t=1124329]("http://ubuntuforums.org/showthread.php?t=1124329")).

Unfortunately sound is still mostly broken and finicky, because the volume sliders don't work right.

Here's what happens, for every single slider:
* When the slider is at maximum, the volume or relevant "part" of the volume is at maximum.
* When the slider is at 50% or slightly less the volume or relevant part of the volume is mute.
* The bottom 50% of the slider has no effect.

This makes it very hard to get the volume at the right level. And it affects every single slider, in gnome-volume-control, gnome-volume-control-pulse, aumix, alsamixer and I might have tried some others too but those are the only ones that come straight to mind.

My computer is a Dell XPS M1330 with the Intel sound card, and I'm running a fully updated version of the 64 bit Jaunty beta. If anyone has any ideas why the volume sliders misbehave so badly I would be eternally grateful!

Thanks,
Christo

---

### Post by nwadams on 2009-04-14
yes...its me again :p. 

Ok. I have found that if you set it to control the gnome-volume-control-pulse slider only and/or the PCM slider and leave the master on max You get a wider range. AND the mic record volume is always set to max in the system (i believe). 

You can adjust which slider is controlled by the hardware buttons in system -> preferences -> sound (and you can change the default mixer track to whatever you want) and then you can change the applet (the default one) to show that track by right clicking on it and going preferences.

EDIT: your link, links back to this thread instead of the other one.

---

### Post by Technoviking on 2009-04-14
I'm unable to get a external mic working on my m1330. Make Skype a pain to use.

T-V

---

### Post by nwadams on 2009-04-14
[http://ubuntuforums.org/showthread.php?t=1124329](http://ubuntuforums.org/showthread.php?t=1124329)

that thread may interest you depending on the issue you are having with the mic. Does it work with say gnome sound recorder?

---

### Post by cfogelberg on 2009-04-15
> **nwadams said:**
> yes...its me again :p. 

Ok. I have found that if you set it to control the gnome-volume-control-pulse slider only and/or the PCM slider and leave the master on max You get a wider range. AND the mic record volume is always set to max in the system (i believe). 

You can adjust which slider is controlled by the hardware buttons in system -> preferences -> sound (and you can change the default mixer track to whatever you want) and then you can change the applet (the default one) to show that track by right clicking on it and going preferences.

EDIT: your link, links back to this thread instead of the other one.

Sorry, this is a bit unclear to me. I have four "Sound" entries now on my preferences menu, maybe that's why it's unclear.

I've renamed them a bit to try and make it clearer:
* 1) Sound
* 2) Sound - PulseAudio Preferences
* 3) Sound - Pulse Volume Control
* 4) Sound - Volume Control

(2) is a window with three tabs: Network Access, Multicast/RTP and Simultaneous Output. I don't think it's the one you mean. According to alacarte it's "paprefs"/

(3) is just the Pulse volume window I use to adjust the volume level for the mic and which I can get to by right clicking on the Pulse icon in the tray and selecting "Sound Preferences". According to alacarte this is "gnome-volume-control-settings".

(4) is the volume window I get by right clicking on the other speaker icon in the task bar and selecting "Open Volume Control". According to alacarte this is "gnome-volume-control".

In the properties when using alacarte, (1) is called Sound Tests (but for some reason this change doesn't show up in the menu). According to alacarte selecting this runs gnome-sound-properties. 

gnome-sound-properties let's me specify from a drop down the source of "Sound Events", "Music and Movies", and Sound Playback and Sound Capture for "Audio Conferencing". All of these drop downs are set to "Autodetect" except Sound Capture for "Audio Conferencing", which is set to ALSA.

Down the bottom of this window is another drop down that might be what you're talking about:

[[IMG]http://img142.imageshack.us/img142/1548/screenshotsoundpreferen.th.png[/IMG]](http://img142.imageshack.us/my.php?image=screenshotsoundpreferen.png)

However, when I do this the only entry in the mixer box is "Master". If I choose "HDA Intel (Alsa mixer)" there are a lot of entries in the devices list, including the +50db Mic boost thing from alsaboost that I thought I'd removed. When I select SigmaTel STAC9229 (OSS Mixer) I get a lot of device options.

Overall though I'm just confused by what you recommend I do here. If you cna clarify I'd be muchly appreciative! :)

Christo

---

### Post by nwadams on 2009-04-15
the screenshot is the right one. Set it to the playback on pulseaudio and that should do it.

---

### Post by cfogelberg on 2009-04-16
> **nwadams said:**
> the screenshot is the right one. Set it to the playback on pulseaudio and that should do it.

OK, only preliminary testing as I have to run off to my lab now, but I think this actually works!? :D Will post confirmation when I get home and/or in the weekend when I might have a bit more time to do this :)

Cheers,
xto

---

### Post by cfogelberg on 2009-04-16
Yep, that worked and the hardware volume controls all work. wrt Skype I also needed to configure it to use pulse for its Sound In (see "Jaunty and my internal microphone thread", last post for details).

---

