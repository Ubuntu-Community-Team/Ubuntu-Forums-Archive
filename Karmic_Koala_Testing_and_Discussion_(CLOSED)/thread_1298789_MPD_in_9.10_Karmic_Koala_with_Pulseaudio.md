---
title: "MPD in 9.10 Karmic Koala with Pulseaudio"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taavi on 2009-10-23
Hey. 

Can someone help to get MPD working with Pulseaudio in Karmic with smallest hassle and hacks.

I'm willing to update this post to get final good HOW-TO for everyone everywhere. Thank you!

EDIT: Thanks to fenian posting below, we can have working MPD. All hails and here it goes...
_____________________________________________________________________________________



[SIZE="5"]How to get MPD working with pulseaudio in Karmic Koala (Ubuntu 9.10)[/SIZE]
[LIST=1]
[*]Install pulseaudio prefs (paprefs) from synaptic or open a terminal and enter...

```
sudo apt-get install paprefs
```

[*]Open PulseAudio prefrences from the menu System->Prefrences->PulseAudio Preferences

[*]Click the Network Server tab

[*]Check the box "*Enable network access to local sound devices*"

[*]Check the box "*Don't require authentication*"

[*]Next enable pulse in your mpd.conf file,in a terminal enter...
```
gksudo gedit /etc/mpd.conf
```
[*]In the audio output section add these lines...

```

audio_output {
    type "pulse"
    name "My Pulse Device"
}
```

[*]Finally restart mpd,in the terminal enter...
```
sudo /etc/init.d/mpd restart
```
[*] Open up your favourite client -- sonata, ncmpc, mpc -- & enjoy.

[/LIST]

---

### Post by fenian on 2009-10-24
Try this 

Install pulseaudio prefs (paprefs) from synaptic or open a terminal and enter...

> sudo apt-get install paprefs

Open PulseAudio prefrences from the menu System>Prefrences>PulseAudio Prefrences

Click the Network Server tab

Check the box "Enable network access to local sound devices"

Check the box "Don't require authentication"

Next enable pulse in your mpd.conf file,in a terminal enter...

> gksudo /etc/mpd.conf

In the audio outpu section add these lines...

> audio_output {
	type    "pulse"
	name    "My MPD PulseAudio Output"
}

Finally restart mpd,in the terminal enter...

> sudo /etc/init.d/mpd restart

Tht should do it.

---

### Post by taavi on 2009-10-26
Thank you so much, this really did work like a charm.

---

