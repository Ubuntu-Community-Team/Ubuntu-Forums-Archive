---
title: "Jaunty Alpha 3 morning updates lost sound all together!"
date: 2009-01-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by dBuster on 2009-01-28
After this mornings 80 some odd updates I have lost sound all together!  I can see the sound card using the lscpi -l and the alsamixer can control sound levels but no sound is coming out of the speakers....

1.  How can I retrieve a list of updates that happened this morning?
2.  When I go to preferences by right clicking on the volume control I can control the input but there is no output device listed!!!

I am running Jaunty Alpha 3 64bit on a Compaq CQ60-215 as it was the only release of 64bit flavor that I could get to load!  Something happened this morning with the updates and I would like to help track it down and if needed submit bug report...

---

### Post by olskar on 2009-01-28
> **dBuster said:**
> After this mornings 80 some odd updates I have lost sound all together!  I can see the sound card using the lscpi -l and the alsamixer can control sound levels but no sound is coming out of the speakers....

1.  How can I retrieve a list of updates that happened this morning?
2.  When I go to preferences by right clicking on the volume control I can control the input but there is no output device listed!!!

I am running Jaunty Alpha 3 64bit on a Compaq CQ60-215 as it was the only release of 64bit flavor that I could get to load!  Something happened this morning with the updates and I would like to help track it down and if needed submit bug report...

Check /var/log/apt-get or /var/log/aptitude :)

---

### Post by punischdude on 2009-01-28
Today's updates borked my sound, too. Reverting the sound related stuff didn't bring it back, but I could have missed sth.

The audio chip is a nVidia MCP65 High Definition Audio used by amd64 Jaunty.

Any ideas?

---

### Post by habtool on 2009-01-28
I have login sound when i boot up and login.

But after that I have no sound in totem, vlc etc.

---

### Post by Vaun on 2009-01-28
I just filed a bug on this.

[https://bugs.launchpad.net/bugs/322344](https://bugs.launchpad.net/bugs/322344)

---

### Post by jerrylamos on 2009-01-28
Added my info to the bug:

After today's updates 20090128 login sound O.K. otherwise dumb.
And yes the volume controls are at max.

Synaptic shows pulseaudio 0.9.14-0ubuntu2

System>Sound>output lists no devices.  It can't find:

Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]

but it could yesterday.

Compaq Presario 3.3 gHz Celeron
Linux version 2.6.28-5-generic (buildd@rothera) (gcc version 4.3.3 20090119 (prerelease) (Ubuntu 4.3.2-2ubuntu14) ) #15-Ubuntu SMP Thu Jan 22 21:21:04 UTC 2009

Jerry

---

### Post by punischdude on 2009-01-28
```

~$ asoundconf list
Names of available sound cards:
NVidia
```
followed by
```

~$ alsactl init NVidia
```

brought my sound back!

---

### Post by jerrylamos on 2009-01-28
alsamixer -Dhw
did it for me.

lots of volume settings at zero.  Set them all at max.

Shakira ojos asi FULL BLAST!

Jerry

---

### Post by dBuster on 2009-01-28
> **punischdude said:**
> ```

~$ asoundconf list
Names of available sound cards:
NVidia
```
followed by
```

~$ alsactl init NVidia
```

brought my sound back!

Will have to give this a try tonight when I get home!  Crossing my fingers...  

On a side note, would the updates have also caused video to become choppy in playback since the audio wasn't working?  Video before was smooth when I had the sound...

---

### Post by dBuster on 2009-01-28
> **dBuster said:**
> Will have to give this a try tonight when I get home!  Crossing my fingers...  

On a side note, would the updates have also caused video to become choppy in playback since the audio wasn't working?  Video before was smooth when I had the sound...

Was there an error experienced when you tried that??

This is what I received...

```
~$ alsactl init NVidia
Unknown hardware: "HDA-Intel" "Generic 10de NVIDIA MCP78 HDMI" "HDA:14f15051,103c360a,00100000 HDA:10de0002,10de0101,00100000" "" ""
Hardware is initialized using a guess method

```

---

### Post by dBuster on 2009-01-28
Okay, I have sound when I listen to say an mp3, however I have no sound in Firefox...  hmmm plugin maybe?

Here is the plugin list I have now...

```
Shockwave Flash

    File name: libflashplayer.so
    Shockwave Flash 10.0 d21

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes
Windows Media Player Plug-in 10 (compatible; Totem)

    File name: libtotem-gmp-plugin.so
    The Totem 2.25.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
application/x-mplayer2 	AVI video 	avi, wma, wmv 	Yes
video/x-ms-asf-plugin 	ASF video 	asf, wmv 	Yes
video/x-msvideo 	AVI video 	asf, wmv 	Yes
video/x-ms-asf 	ASF video 	asf 	Yes
video/x-ms-wmv 	Windows Media video 	wmv 	Yes
video/x-wmv 	Windows Media video 	wmv 	Yes
video/x-ms-wvx 	Windows Media video 	wmv 	Yes
video/x-ms-wm 	Windows Media video 	wmv 	Yes
video/x-ms-wmp 	Windows Media video 	wmv 	Yes
application/x-ms-wms 	Windows Media video 	wms 	Yes
application/x-ms-wmp 	Windows Media video 	wmp 	Yes
application/asx 	Microsoft ASX playlist 	asx 	Yes
audio/x-ms-wma 	Windows Media audio 	wma 	Yes
DivX® Web Player

    File name: libtotem-mully-plugin.so
    DivX Web Player version 1.4.0.233

MIME Type 	Description 	Suffixes 	Enabled
video/divx 	AVI video 	divx 	Yes
QuickTime Plug-in 7.2.0

    File name: libtotem-narrowspace-plugin.so
    The Totem 2.25.3 plugin handles video and audio streams.

MIME Type 	Description 	Suffixes 	Enabled
video/quicktime 	QuickTime video 	mov 	Yes
video/mp4 	MPEG-4 video 	mp4 	Yes
image/x-macpaint 	MacPaint Bitmap image 	pntg 	Yes
image/x-quicktime 	Macintosh Quickdraw/PICT drawing 	pict, pict1, pict2 	Yes
video/x-m4v 	MPEG-4 video 	m4v 	Yes
Default Plugin

    File name: libnullplugin.so
    The default plugin handles plugin data for mimetypes and extensions that are not specified and facilitates downloading of new plugins.

MIME Type 	Description 	Suffixes 	Enabled
* 	All types 	.* 	No
Demo Print Plugin for unix/linux

    File name: libunixprintplugin.so
    The demo print plugin for unix.

MIME Type 	Description 	Suffixes 	Enabled
application/x-print-unix-nsplugin 	Demo Print Plugin for Unix/Linux 	.pnt 	Yes
libnpjp2.so

    File name: libnpjp2.so

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	
```

The java one went on I truncated it here...

---

### Post by punischdude on 2009-01-29
> **dBuster said:**
> Was there an error experienced when you tried that??

This is what I received...

```
~$ alsactl init NVidia
Unknown hardware: "HDA-Intel" "Generic 10de NVIDIA MCP78 HDMI" "HDA:14f15051,103c360a,00100000 HDA:10de0002,10de0101,00100000" "" ""
Hardware is initialized using a guess method

```

Yes, same error but sound is working fine, even in Firefox, so I didn't mention it.

---

### Post by dBuster on 2009-01-29
> **punischdude said:**
> Yes, same error but sound is working fine, even in Firefox, so I didn't mention it.

Thanks for the reply, however I have no sound in firefox....  elsewhere it is working though thanks to your tip!!

---

### Post by gnudoc on 2009-01-29
Same story here. sound fine until today. login sounds still fine, nothing else anywhere.

i get exactly the same error message here, but no joy afterwards.

also tried  maximising things in alsamixer - no use. :(

any other thoughts anyone?

---

### Post by gnudoc on 2009-01-29
Turn off pulseaudio.

The idiot's way to do that is... System -> Preferences -> Sessions -> Untick Pulseaudio Sound System - then restart.


I'm sure there's a proper way to do this, but i don't know it.

---

### Post by dBuster on 2009-01-29
> **gnudoc said:**
> Turn off pulseaudio.

The idiot's way to do that is... System -> Preferences -> Sessions -> Untick Pulseaudio Sound System - then restart.


I'm sure there's a proper way to do this, but i don't know it.

So you had to turn off pulseaudio and the sound came back in Firefox?

I will have to give it a try!

---

### Post by plun on 2009-01-29
> **gnudoc said:**
> Turn off pulseaudio.

The idiot's way to do that is... System -> Preferences -> Sessions -> Untick Pulseaudio Sound System - then restart.


I'm sure there's a proper way to do this, but i don't know it.

Well.....

Where is the bug report...?  ;)


After that "the idiots way" can be used or another...:D

---

### Post by Gina on 2009-01-29
I have no sound from Totem though it gives every appearance of playing the music (visual effects showing the beat) and normal progress bar.  Just no sound to be heard.  Login and startup sounds are fine.  In fact the startup sound has only just returned.

---

### Post by Arabica Bean on 2009-01-29
> **gnudoc said:**
> Turn off pulseaudio.

The idiot's way to do that is... System -> Preferences -> Sessions -> Untick Pulseaudio Sound System - then restart.


I'm sure there's a proper way to do this, but i don't know it.


I went into terminal and used

```
killall pulseaudio
```

Worked a treat!

---

### Post by W2IBC on 2009-01-29
i would have to say looks like sound is a issue in 9.04 for alot of people.

---

### Post by jerrylamos on 2009-01-29
> **Arabica Bean said:**
> I went into terminal and used

```
killall pulseaudio
```

Worked a treat!

Sure did work!  Thanks!

Jerry

---

### Post by techdude3177 on 2009-01-29
this command works great but it needs to be ran everytime after restart

---

### Post by dBuster on 2009-01-30
Combine the killall post along with the other post about disabling it and voila you have sound back in Firefox!!  No need to restart! :popcorn:

Nothing seems to be bothered by not having pulseaudio running either for me at least.

---

### Post by gnudoc on 2009-01-30
i've had pulseaudio off now for a day or so, and yes i'd agree - no obvious problems without it here.

i do recognise though, that there are several clever reasons why pulseaudio would be A Good Thing (TM) once it got working properly. so i'll be checking in with it on a regular basis. :)

---

### Post by Gina on 2009-01-30
[This other thread]("http://ubuntuforums.org/showthread.php?p=6646703#post6646703") describes another work around without disabling PA and the cause of the problem.

---

### Post by techdude3177 on 2009-01-30
Woops

---

### Post by chuckyp on 2009-01-31
Also had a similiar problem where sound would drop every once in a while. Disabling pulseaudio did the trick for me I have a intel ICH5 sound card off of a 82801 chipset

---

### Post by habtool on 2009-01-31
This is the bug report and a work around:
[https://bugs.edge.launchpad.net/ubuntu/+source/pulseaudio/+bug/322374](https://bugs.edge.launchpad.net/ubuntu/+source/pulseaudio/+bug/322374)

A work around, at a terminal type:

pulseaudio -k ; start-pulseaudio-x11

---

### Post by dBuster on 2009-01-31
> **habtool said:**
> This is the bug report and a work around:
[https://bugs.edge.launchpad.net/ubuntu/+source/pulseaudio/+bug/322374](https://bugs.edge.launchpad.net/ubuntu/+source/pulseaudio/+bug/322374)

A work around, at a terminal type:

pulseaudio -k ; start-pulseaudio-x11

I can also confirm this works!  Still having sound and pulseaudio running!  Wahoo!  Chalk another one up for the forums...

---

### Post by robertpolson on 2009-03-01
> **punischdude said:**
> ```

~$ asoundconf list
Names of available sound cards:
NVidia
```
followed by
```

~$ alsactl init NVidia
```

brought my sound back!

That worked for me. Thank you !

---

