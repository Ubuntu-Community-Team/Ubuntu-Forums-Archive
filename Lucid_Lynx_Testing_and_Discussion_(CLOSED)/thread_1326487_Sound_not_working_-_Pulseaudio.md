---
title: "Sound not working - Pulseaudio?"
date: 2009-11-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ubername on 2009-11-14
Hi

I have a problem with pulseaudio. I cannot get sounds to play on my lucid machine although I can 'pipe' them to my karmic machine (if 'pipe' is the right word &#8211; I can use pa applet to select the karmic server and hear the sounds from that box).

I have tried
sudo alsa force-reload

also changed settings in alsamixer (but not sure if I did the right thing &#8211; all output is set to max)

and looked at this thread [http://ubuntuforums.org/showthread.php?t=1317956](http://ubuntuforums.org/showthread.php?t=1317956)

but I'm not getting anywhere. Can anyone help? TIA

edit: should have said sound was working fine until updates +-2 days ago (about when kernel 2.6.32-4 came out)

---

### Post by plun on 2009-11-14
Install **pavucontrol** and unmute output device

---

### Post by ubername on 2009-11-14
> **plun said:**
> Install **pavucontrol** and unmute output device
 Thanks, already had pavucontrol, output was not muted (AFAIK)

---

### Post by plun on 2009-11-14
> **ubername said:**
> Thanks, already had pavucontrol, output was not muted (AFAIK)

What gives a pkill ?
```

pkill pulseaudio; sleep 2; pulseaudio -vv
```

---

### Post by Regenweald on 2009-11-14
What connections are you using ? front or back ? with the last updates my sound went ridiculously low. had to use alsamixer in the terminal to reset it.

---

### Post by dino99 on 2009-11-14
2 steps:

- remove / purge all pulseaudio installed packages
- reinstall pulseaudio

---

### Post by rtfm on 2009-11-14
I had the same issue on a clean install, no sound...

Like others my sound was returned by going to System/Administration/Hardware Drivers and removing the Software Modem Driver that I had "activated" a few days earlier.

Hope this helps.

---

### Post by Reiger on 2009-11-14
I had this problem too but solved it by removing my pulseaudiou config files in my home diretory like so:
```

kill `pidof pulseaudio` # stop pulseaudio
rm -r ~/.pulse # remove pulseaudio config under homee
rm ~/.pulse-cookie # remove pulseaudio session (?) data
pulseaudio & # start pulseaudio in the background

```

---

### Post by VMC on 2009-11-14
There's some good tips pointed out here already. 'll have to remember them if my Pulseaudio ever goes south on me.

How about looking at some log files for any indication of audio trouble.

---

### Post by ubername on 2009-11-15
Many thanks for all the help.

Rather foolishly I tried each of the suggestions individually, then rebooted after removing my web-cam, blue-tooth dongle and a dodgy usb memory stick.

Then I went into alsamixer -Dhw and set the volume of 'speaker' (which always seems to revert to 0 after reboot - also a symptom of the problem I have been having)and it works! So thanks to all even though I cannot, for the benefit of others, identify exactly which step (or combination thereof) did the trick.

Attached a screen shot if anyone is interested.

The output of pulseaudio -vv is too big to post(38Kb saved as text file with gedit) or for some other reason I cannot attach it but if someone is interested maybe I can show relevant parts?

I am just going to reboot and see if the volume of 'speaker' goes back to zero - if so I may be back if I cannot find how to resolve this anywhere else.

Thanks again.

---

### Post by ubername on 2009-11-15
Still stumped with resetting sopund to zero after logout (not just reboot)

I tried
sudo /etc/init.d/alsasound save

and
sudo alsactl store

Here is that file:
state.Intel {
	control.1 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Speaker Playback Volume'
		value.0 45
		value.1 45
	}
	control.2 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Speaker Playback Switch'
		value.0 true
		value.1 true
	}
	control.3 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 2
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Speaker Playback Volume'
		index 1
		value.0 64
		value.1 64
	}
	control.4 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 2
		iface MIXER
		name 'Speaker Playback Switch'
		index 1
		value.0 true
		value.1 true
	}
	control.5 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'Center Playback Volume'
		value 64
	}
	control.6 {
		comment.access 'read write'
		comment.type BOOLEAN
		comment.count 1
		iface MIXER
		name 'Center Playback Switch'
		value true
	}
	control.7 {
		comment.access 'read write'
		comment.type INTEGER
		comment.count 1
		comment.range '0 - 64'
		comment.dbmin -4800
		comment.dbmax 0
		iface MIXER
		name 'LFE Playback Volume'
		value 64
	}
	control.8 {
		comment.access 'read write'
		comment.type BOOLEAN 



Any idea why I have three speaker entries? I have only one set of speakers attached.

---

### Post by plun on 2009-11-15
Just a check because my sound was also broken this morning.

Used the pkill command and unmuted sound.

[[img]http://ubuntu-pics.de/thumb/30957/snapshot18_3JJ79N.png[/img]](http://ubuntu-pics.de/bild/30957/snapshot18_3JJ79N.png)

---

### Post by ranch hand on 2009-11-15
Usually all that is needed is to "wiggle" the volume slider.

---

### Post by hikaricore on 2009-11-15
Mine was muted today upon reboot for some reason. O.o

---

### Post by afv on 2009-11-15
I had no sound today after rebooting.
Checked alsamixer, pavucontrol and padevchooser, deleted ~/.pulse and ~/.pulse-cookie, purged all pulseaudio packages, reinstalled, etc. and still no sound.

Now, after upgrading pulseaudio from 0.9.20-0ubuntu1 (lucid) to 0.9.20-0ubuntu2~~karmic~ubuntuaudiodev1 (Ubuntu Audio Dev team PPA), followed by a killall pulseaudio, sound is back!

---

### Post by philinux on 2009-11-17
Done all the above apart from reinstall pulse. Still no sound.

I get the thud as the sda intel powersave kicks in.

---

### Post by MacUntu on 2009-11-17
According to Audacious' band analyzer something is playing but I hear no sound. :(

[img]http://img.xrmb2.net/images/569601.png[/img]

Also PA Volume Control shows activity:

[img]http://img.xrmb2.net/images/726731.png[/img]

---

### Post by darco on 2009-11-17
Just like ubername mentioned in an earlier post, run 
```
alsamixer -Dhw
```

then adjust the speaker that is currently zeroed out...work fine here. I do have to do this after each reboot.


darco

---

### Post by MacUntu on 2009-11-17
Already done, not working. Will purge and reinstall now.

Edit: nope, sound dead with a NVidia CK804 (Realtek ALC850 chip).

---

### Post by zika on 2009-11-17
Did You try with padevchooser? Just a shot in the dark before You purge and reinstall...

---

### Post by yoasif on 2009-11-17
> **darco said:**
> Just like ubername mentioned in an earlier post, run 
```
alsamixer -Dhw
```

then adjust the speaker that is currently zeroed out...work fine here. I do have to do this after each reboot.


darcois there a launchpad bug for this? I am seeing the same issue.

---

### Post by plun on 2009-11-17
Update is out:

> 
pulseaudio (1:0.9.20-0ubuntu2) lucid; urgency=low

  * Add 0002-Fix-makefiles-to-include-all-alsa-path-files-on-inst.patch
    from Debian unstable (thanks, Sjoerd Simons!)
  * Fix 0055-handle-Master-Front.patch to handle only front elements
    based on comments from Lennart. [B]The patch now does the right thing
    despite linux still doing the wrong thing, but at least we handle
    cases where linux will do the right thing.[/B];)


[https://lists.ubuntu.com/archives/lucid-changes/2009-November/000522.html](https://lists.ubuntu.com/archives/lucid-changes/2009-November/000522.html)

---

### Post by MacUntu on 2009-11-17
> **plun said:**
> Update is out:

"And there was sound."

\\:D/

---

### Post by plun on 2009-11-17
> **MacUntu said:**
> "And there was sound."

\\:D/

Still muted for me after restart...;)  I can live with that...

---

### Post by yoasif on 2009-11-17
update fixed the issue for me.

---

### Post by philinux on 2009-11-18
> **plun said:**
> Still muted for me after restart...;)  I can live with that...

All fine here too. Not muted on restart though. Have you been tweakin :p.

---

### Post by ubername on 2009-11-18
Seem to be sorted now, although initially upgrades appeared not to make any difference. I then discovered that my 'master' chanel had been reset to zero following the upograde, rather than the 'speaker' channel after every logout as before.

So I followed 
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
 HOWTO: PulseAudio Fixes & System-Wide Equalizer Support (thanks psyke83)

once again(!), then

alsamixer -Dhw

set master volume to something reasonable and now all works, including logon / logof desktop sounds.

---

### Post by darco on 2009-11-19
> **ubername said:**
> Seem to be sorted now, although initially upgrades appeared not to make any difference. I then discovered that my 'master' chanel had been reset to zero following the upograde, rather than the 'speaker' channel after every logout as before.

So I followed 
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
 HOWTO: PulseAudio Fixes & System-Wide Equalizer Support (thanks psyke83)

once again(!), then

alsamixer -Dhw

set master volume to something reasonable and now all works, including logon / logof desktop sounds.

Heh, same issue..I followed the HOWTO as well and it works after reboot...thxs


darco

---

### Post by ktechman on 2010-01-14
Thank you Ubername

> So I followed
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
HOWTO: PulseAudio Fixes & System-Wide Equalizer Support (thanks psyke83)

once again(!), then

alsamixer -Dhw

set master volume to something reasonable and now all works, including logon / logof desktop sounds. 

With: Azalia (Intel HDA) On-board sound

Worked for me

Ktechman

---

