---
title: "Can't play sounds in widelands (something about SDL Mixer)"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2008-10-18
Hi all, 
  There is a game called widelands which I tried out. I couldn't get far because sound is not working. It turns out the game uses something called sdl mixer and while I've got pulseaudio I dunno what is needed or how to configure it. 

Looking forward to comments and suggestions on the same.

---

### Post by taavikko on 2008-10-18
```
aptitude search sdl
```

First I would try **libsdl1.2debian-pulseaudio**

---

### Post by nystire on 2008-10-18
Perhaps "sudo apt-get install libsdl-mixer1.2" ?

EDIT:
On my install (Upgraded from Hardy), libsdl-mixer1.2 was already installed, and the sound worked straight after installing the game.

---

### Post by ShirishAg75 on 2008-10-19
Both are installed but still nada :( Anything more guys?

I have used the pulse-audio distilled guide to get my audio working. That shouldn't break this game, should it?

---

### Post by nystire on 2008-10-19
Do you remember more or less what you did to get the sound working?

---

### Post by ShirishAg75 on 2008-10-19
I used pyske83's [thread]("http://ubuntuforums.org/showthread.php?t=866965") for doing the same. These are the steps I followed :-

a. Configure libao applications to use PulseAudio:

```
$ echo "default_driver=pulse" >~/.libao
```

b. Then did 

```
$ sudo adduser $USER pulse-access
$ sudo adduser $USER pulse-rt
```

c. Then made the following changes in /etc/pulse/daemon.conf

```
resample-method = speex-float-0
default-fragments = 8
default-fragment-size-msec = 5
```

The only thing I see which might be the issue is doing the first step, I dunno, comments and suggestions welcome.

---

### Post by nystire on 2008-10-19
What does "groups $USER" return?

Also, if you delete .libao and reboot, does the sound still work? 
Have you tried installing padevchooser (sudo apt-get install padevchooser) and selecting your ALSA device as the default output device ( and also choosing "PulseAudio Sound Server" in sound preferences for all the devices apart from the Mixer)?

Sorry for seeming so demanding, but I'm still trying to force breakfast down my throat here while studying and browsing the net :D

---

### Post by nystire on 2008-10-19
Deleted due to double posting

---

### Post by ShirishAg75 on 2008-10-20
> **nystire said:**
> What does "groups $USER" return? 

Doing  groups $USER gives 

 ```
groups $USER
shirish adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin pulse-access pulse-rt

```[quote=nystire]
Also, if you delete .libao and reboot, does the sound still work? [/quote]

Yes sound and music work :)

[quote=nystire]
Have you tried installing padevchooser (sudo apt-get install padevchooser) and selecting your ALSA device as the default output device ( and also choosing "PulseAudio Sound Server" in sound preferences for all the devices apart from the Mixer)? [/quote]

The latter was not done. padevchooser was already installed (that is the Pulseaudio applet which is in the systray right)

[quote=nystire]
Sorry for seeming so demanding, but I'm still trying to force breakfast down my throat here while studying and browsing the net :D[/quote]

No issues, will test it in 5 mins. and report back.

Update : Hey thanx, everything works :)

---

### Post by nystire on 2008-10-21
Everything meaning the sound in the game? Or just the rest of the pc? :)

---

### Post by ShirishAg75 on 2008-10-21
sound in game as well as on the pc, although have now got a slightly different issue, dunno if the two are related or not [lpbug]286794[/lpbug]

---

### Post by nystire on 2008-10-21
Could you please mark the thread as solved then? 

Thanks.

---

### Post by ShirishAg75 on 2008-10-21
how forgetful, thanx for reminding me :)

---

