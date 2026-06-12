---
title: "PulseAudio &amp; M-Audio Revolution 5.1 (ice1724)"
date: 2009-08-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by adancau on 2009-08-04
Hi all, thanks to everyone who will take time to read this. First of all I'd like to mention that Karmic works fine on two machines I use and it's been a great experience so far.
Only problem I have is with sound, mainly PulseAudio.

My card is an M-Audio Revolution 5.1 (ICE1724) and I'm using it with a 4.0 surround system. It works pretty well, minus a few nagging issues. Guess all of them stem from the fact that I don't seem to have a master channel. In alsamixer I have PCM (that actually controls the front channel), PCM Center, PCM Headphone, PCM LFE, PCM Rear, Line Loopback, CD Loopback, Mic Loopback and a bunch of none too clear switches that don't seem to do much.

 Previously using the old Sound Preferences I could select and lock the PCM & PCM Rear into a sort of Master channel that could be controlled either by the volume keys on the keyboard or from the volume applet. Since introducing the PulseAudio control I can't do that anymore, and it's very annoying. I have to use alsamixer to separately change the PCM and PCM Rear volume.

In the new SoundPreferences I have selected Output Analog Surround 4.0 from the Profile list.

The Output Volume slider in SoundPreferences seems to only control the PCM (front channel). The Fade slider seems to do something when moved toward Rear, but I don't see any change on any channels in alsamixer. Basically it acts the opposite way, when it's in Rear I can only hear sound on the front speakers. If I move it towards Front it turns down PCM (front) in a very jumpy way, rear sound disappears completely and Output Volume goes down with it until I can't hear anything. Turning the Output Volume back up resets the Fade back to center. My speakers are correctly connected, so I haven't connected front to rear and the other way around, and still that wouldn't make much of a difference since sound is not controllable.

At the moment I'm forced to use alsamixer to independently control front/rear. I don't have/use any .asoundrc or alsa.conf file. I suspect the problem stems from the fact that PCM was somehow supposed to control Master and the front channel to be a separate control (at least I guess that's what PulseAudio assumes).

I would appreciate any kind of advice. Searching on Google didn't turn out anything relevant unfortunately, and this is the only problem that prevents me from enjoying Karmic to its fullest.

Thanks.

---

### Post by adancau on 2009-08-06
No ideas at all?

---

### Post by taavikko on 2009-08-06
> **adancau said:**
> No ideas at all?

change this:
```
; default-sample-channels = 2
```
to this
```
default-sample-channels = 5
```

in "/etc/pulse/daemon.conf" Just to test the channels for starters.

---

### Post by adancau on 2009-08-06
Thank you. Unfortunately already done that a long time ago, I have speaker output on both front and rear, so no issues there. Incidentally I think output selection in the new Sound Prefs modifies the daemon.conf file and sets the number of speakers accordingly.
Guess I might have to go with a different audio board. Pity, I really like the Revo. Won't give up until the final Karmic release though :)

---

### Post by psyke83 on 2009-08-06
Install PulseAudio Volume Control (pavucontrol). On the Configuration tab, you may need to choose a different profile that reflects your setup.

Also, keep in mind that we're currently using a test release of PulseAudio 0.9.16 which has some issues currently. See [this]("http://ubuntuforums.org/showpost.php?p=7739984&postcount=17") post and its associated thread.

P.S. I don't have a surround setup to test, but you may not need to edit /etc/pulse/daemon.conf in the newest version (in fact, it may cause issues). Check the new features of the PulseAudio Volume Control before making customizations to the configuration files.

---

