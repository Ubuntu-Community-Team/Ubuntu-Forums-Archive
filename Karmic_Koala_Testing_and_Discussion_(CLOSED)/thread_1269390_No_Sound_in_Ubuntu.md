---
title: "No Sound in Ubuntu"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gjoellee on 2009-09-18
Now first of all I have to say that I have the same issue with Jaunty, but I am using Karmic alpha 6 so I am posting here.

I don't have the product information about my speakers, but I know they are from Creative and it is 2.1 sound (One subwoofer and two speakers right?)

I son't know why, but I just can't get sound in Ubuntu. I am dual booting with Win7 and the sound works great in Win7 so there has to be an issue with Ubuntu.

Thanks for any help. I MUST have music or I am going to get depressed!

---

### Post by psyke83 on 2009-09-18
Post the results of:

```
$ aplay -l
```

Also, right-click on the volume indicator and choose Sound Preferences, making sure to check the settings on the Hardware and Output tabs.

---

### Post by gjoellee on 2009-09-18
output:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [SB Audigy 2 [Unknown]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 31/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Audigy2 [SB Audigy 2 [Unknown]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [SB Audigy 2 [Unknown]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Audigy2 [SB Audigy 2 [Unknown]], device 4: p16v [p16v]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by ktraub on 2009-09-18
My sound is now also completely gone with this morning's (alpha6)updates. 
I've been using the daily updates since Karmic Alpha2, and have had sound problems all along since moving from 9.04, usually only being able to hear anything from the LFE (subwoofer). 
The Sound in 9.04 worked, although I had to manually mute the LFE as it would never track with the main level control.
I'm on a Dell Inspiron 9400 with Intel HD audio and the output of aplay -l is:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I've tried selecting and deselecting both the analog stereo [IEC958]  and the digital stereo output, but still no joy.
Any help is greatly appreciated.
-Kev

---

### Post by gjoellee on 2009-09-18
I can also confirm that I can only hear the subwoofer

---

### Post by gjoellee on 2009-09-19
Bump

---

### Post by LKjell on 2009-09-19
> **ktraub said:**
> My sound is now also completely gone with this morning's (alpha6)updates. 
I've been using the daily updates since Karmic Alpha2, and have had sound problems all along since moving from 9.04, usually only being able to hear anything from the LFE (subwoofer). 
The Sound in 9.04 worked, although I had to manually mute the LFE as it would never track with the main level control.
I'm on a Dell Inspiron 9400 with Intel HD audio and the output of aplay -l is:

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I've tried selecting and deselecting both the analog stereo [IEC958]  and the digital stereo output, but still no joy.
Any help is greatly appreciated.
-Kev

Hi what I did to get my sound back was to uninstall paman and all the autoremove packeges which was related to paman. You can read more at [http://www.pulseaudio.org/wiki/PerfectSetup]("http://www.pulseaudio.org/wiki/PerfectSetup") on those packes.

Then I deleted ~/.pulse to reset pulse configuration.

Restarted the comp. Then go to System > Preferences > Sound

Under the Hardware tap use the Profile Analog Stereo Output. Thereafter I dechecked the mute box at the top. If it works then you might try the Analog Stereo Duplex to get input as well.

These are just my troubleshooting steps. Have fun.

---

### Post by waspbr on 2009-09-19
Does anyone know which offerings would please the gods of PA?

Here is the situation on 2 of my machines
Desktop: only gstreamer does not seem to work.Audio in general works

Hp tx1320 laptop:No internal card detected, so no audio at all. I can only get audio through a USB adapter.

---

### Post by gjoellee on 2009-09-19
> **LKjell said:**
> Hi what I did to get my sound back was to uninstall paman and all the autoremove packeges which was related to paman. You can read more at [http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup) on those packes.

Then I deleted ~/.pulse to reset pulse configuration.

Restarted the comp. Then go to System > Preferences > Sound

Under the Hardware tap use the Profile Analog Stereo Output. Thereafter I dechecked the mute box at the top. If it works then you might try the Analog Stereo Duplex to get input as well.

These are just my troubleshooting steps. Have fun.

Nope, still not working.

EDIT: I made a new post in General Help due to higher population

---

### Post by amano on 2009-09-19
> **waspbr said:**
> Does anyone know which offerings would please the gods of PA?

Here is the situation on 2 of my machines
Desktop: only gstreamer does not seem to work.Audio in general works

Hp tx1320 laptop:No internal card detected, so no audio at all. I can only get audio through a USB adapter.

Both don't sound like PulseAudio issues. The first sounds like a gstreamer issue, the second like a (missing?, broken?) driver issue.

---

### Post by gjoellee on 2009-09-19
Forgot to say, that I have been using the same soundcard for the last 6 years, and sound has been working perfect in Ubuntu until I bought and replaced my speakers.

---

### Post by shakaran on 2009-09-19
Did you try this?

```
sudo rm -rf ~/.pulse ~/.pulse-cookie
```

For me it works.

---

### Post by gjoellee on 2009-09-20
> **shakaran said:**
> Did you try this?

```
sudo rm -rf ~/.pulse ~/.pulse-cookie
```

For me it works.

Nope, that does not work...

---

### Post by shakaran on 2009-09-20
And I forget say that you need kill pulseaudo after:
```
sudo killall pulseaudio
```

---

### Post by gjoellee on 2009-09-20
> **shakaran said:**
> And I forget say that you need kill pulseaudo after:
```
sudo killall pulseaudio
```

I did do a restart after I ran the command. PulseAudio would get killed then, so would there really be a difference?

---

### Post by shakaran on 2009-09-20
Nop, theorically. Maybe you problem is diffent that mine. Did you fill a bug on launchpad?

---

### Post by kansasnoob on 2009-09-20
Not at all sure this will be helpful, but OTOH it won't break anything. Try installing 'gnome-alsamixer' either from Synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video:

[ATTACH]129204[/ATTACH]

Fairly self explanatory, basically see if certain channels are muted or turned down, etc.

In Karmic I notice that changing settings in 'gnome-alsamixer' often causes the system volume to mute, so watch for that as you play with things.

---

### Post by gjoellee on 2009-09-21
> **kansasnoob said:**
> Not at all sure this will be helpful, but OTOH it won't break anything. Try installing 'gnome-alsamixer' either from Synaptic or:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video:

[ATTACH]129204[/ATTACH]

Fairly self explanatory, basically see if certain channels are muted or turned down, etc.

In Karmic I notice that changing settings in 'gnome-alsamixer' often causes the system volume to mute, so watch for that as you play with things.

Thanks! Playing with some options there solved it!

---

### Post by mohi on 2009-09-22
same problem here in Kubuntu. any idea of what can i use instead of gnome-alsamixer in kubuntu? :)

---

### Post by mohi on 2009-09-23
I also tested gnome-alsamixer but nothing changed.

this day after upgrading libphonon4 to 4.3.1-4ubuntu1 (which is in 9.04 repos now) the problem solved for me. :)

---

### Post by psyke83 on 2009-09-23
> **mohi said:**
> I also tested gnome-alsamixer but nothing changed.

this day after upgrading libphonon4 to 4.3.1-4ubuntu1 (which is in 9.04 repos now) the problem solved for me. :)

If you're using Kubuntu, you probably don't even have PulseAudio installed (and Phonon is a multimedia API used only in KDE), so it's apples to oranges.

---

### Post by toopi on 2009-09-30
Same problem here.  In alsamixer, unmuting **Master** channel and bumping up the volume got the sound, but it won't survive reboots.  Any thoughts?

**Edit:**
Found a temp fix:
- Add the following at *System > Preferences > Startup Applications*:
```
 amixer set 'Master' unmute playback 0dB 
```

So, at every log in, it would unmute the Master channel and set the volume at 100%.

---

### Post by RaZoR1394 on 2009-10-01
> **toopi said:**
> Same problem here.  In alsamixer, unmuting **Master** channel and bumping up the volume got the sound, but it won't survive reboots.  Any thoughts?

**Edit:**
Found a temp fix:
- Add the following at *System > Preferences > Startup Applications*:
```
 amixer set 'Master' unmute playback 0dB 
```

So, at every log in, it would unmute the Master channel and set the volume at 100%.

Do you by any chance use ALC889A?

I have the same problem and have tried adding alsactl restore to /etc/rc.local and also instead of alsactl restore adding individual channel values but it does not help. And of course I raised the channels and did a store before that. Weird.

I noticed that I had a different settings in sound properties on my htpc where the problems are. The htpc is HDA Intel ALC889A and the desktop is HDA ATI ALC889A. The desktop works fine so I used the settings from that comp on the HTPC (Analog stereo duplex) even though I use digital output and it seems to work fine now.

---

### Post by toopi on 2009-10-01
> **RaZoR1394 said:**
> Do you by any chance use ALC889A?

I have the same problem and have tried adding alsactl restore to /etc/rc.local and also instead of alsactl restore adding individual channel values but it does not help. And of course I raised the channels and did a store before that. Weird.

I noticed that I had a different settings in sound properties on my htpc where the problems are. The htpc is HDA Intel ALC889A and the desktop is HDA ATI ALC889A. The desktop works fine so I used the settings from that comp on the HTPC (Analog stereo duplex) even though I use digital output and it seems to work fine now.

It's AD2000BX, a variation of AD1989B on ASUS P6T Deluxe V2 motherboard.  I'm using the digital output as well, but I had to use the amixer command to prevent the Master channel being muted at startups.

---

