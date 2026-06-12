---
title: "dsp ?"
date: 2008-12-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cecilpierce on 2008-12-04
Does anybody know what took the place of /dev/dsp ?
I have a prg called qsstv that says "cannot open sound device" and its setup for dsp in the config file. Thanks

---

### Post by amauk on 2008-12-04
Pulseaudio ties up /dev/dsp
run your program with padsp

padsp will route dsp (oss) sound through pulseaudio

```
padsp your_program --any_args
```

---

### Post by knarf on 2008-12-04
> **cecilpierce said:**
> Does anybody know what took the place of /dev/dsp ?
I have a prg called qsstv that says "cannot open sound device" and its setup for dsp in the config file. Thanks
*/dev/dsp* is the OSS pcm device file. If it is not there you do not have the OSS compatibility modules (*snd-pcm-oss* and *snd-mixer-oss*) loaded. You can either use *padsp* to start the program (which reroutes sound through pulseaudio) or load the required modules. In the latter case sound can still go through pulseaudio by way of the default ALSA driver if you have your system configured that way (pcm.!default { type pulse }; ctl.!default { type pulse } in .asoundrc or a file sourced from there).

---

### Post by cecilpierce on 2008-12-05
I tried "dpadsp qsstv" and after a few seconds it turns dark gray and locks up, any thoughts ?

Thanks for the info.

---

### Post by knarf on 2008-12-05
Two things. First reload ALSA, this has solved many a sound problem for me:

```
sudo /etc/init.d/alsa-utils restart
```

Try again. Does it work? Fine. If it doesn't you can try to load the OSS compatibility modules:

```
sudo modprobe snd-pcm-oss
```

Then try to run the program (without padsp).

---

### Post by cecilpierce on 2008-12-05
knarf, the "sudo modprobe snd-pcm-oss" cmd worked,thanks. Is there a way to keep it when I reboot?
Still no system sound though !
Again thanks alot for the help.

---

### Post by knarf on 2008-12-05
You can install the *oss-compat* package which was created for those users who need OSS compatibility```
apt-cache show oss-compat
``` to see what it does, ```
sudo apt-get install oss-compat
``` to install it. You'll have to enable the *universe* repo to get access to this package.

These modules were originally loaded from within */etc/modprobe.d/alsa-base* but that was disabled to avoid problems with dmix (see Debian bug [499695]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=499695%29%29"))

---

