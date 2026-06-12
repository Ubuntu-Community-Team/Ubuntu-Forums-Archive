---
title: "A52 plugin no longer works with pulseaudio!"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by danwood76 on 2009-03-25
I route all my audio to my surround sound amp through a digital optical cable.
In the previous few ubuntu releases I've been able to send my audio from pulse through the alsa a52 plugin which has caused encoded a52 to be transmitted to my amp and thus get sound.

In the latest pulseaudio and jaunty release this is no longer the case.

I was wondering if anyone had the same problem and found a fix?

I filed a bug here:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/348353](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/348353)

---

### Post by Catscrash on 2009-03-26
same problem, yes, solution no :-(

---

### Post by danwood76 on 2009-03-26
I found installing the next version of pulseaudio from this ppa made it work sort of:
[http://ubuntuforums.org/showthread.php?t=1066212&highlight=pulseaudio+15+ppa](http://ubuntuforums.org/showthread.php?t=1066212&highlight=pulseaudio+15+ppa)

But I cant make it mix 2 sources into one without it going nasty.

It works fine with just one audio source though.

---

### Post by danwood76 on 2009-03-27
On a further update, just installed 9.04 beta and it now works.
Hurrah!
Odd clicks and crackles every now and then but mixing is working and everything.

Make your asound.conf to be this:
```

pcm.!default {
	type pulse
}

ctl.!default {
	type pulse
}

pcm.pulse {
    type pulse
}

ctl.pulse {
    type pulse
    card 0
}

pcm.a52 {
        type a52
        @args.0 { 
                type integer 
        }
}

ctl.a52 {
	type hw
	card 0
}

```
And then add this to the /etc/pulse/default.pa
```

# This was for a52 surround
load-module module-alsa-sink device=a52 rate=48000 tsched=0 channels=6 sink_name=alsa_surround
set-default-sink alsa_surround

```
I had to install the pulse gnome volume control to select it but it seems to work almost perfectly.

---

### Post by Catscrash on 2009-03-27
that sounds great, thanks for the info

---

### Post by danwood76 on 2009-03-27
Forgot to say you still need to compile the a52 module otherwise this wont work.
The original thread has dissapeared for some reason, but google still have a cache of it:
[http://209.85.229.132/search?q=cache:ZlUqeqF3uYAJ:ubuntuforums.org/archive/index.php/t-714712.html+ubuntu+a52encode+awesomeness&cd=1&hl=en&ct=clnk&client=pub-2070091971271392](http://209.85.229.132/search?q=cache:ZlUqeqF3uYAJ:ubuntuforums.org/archive/index.php/t-714712.html+ubuntu+a52encode+awesomeness&cd=1&hl=en&ct=clnk&client=pub-2070091971271392)

---

### Post by Timon&amp;Pumba on 2009-03-27
It is a shame that Ubuntu does not support digital out, with all our audio systems being equipped with digital connections for a long time.

---

### Post by danwood76 on 2009-03-27
You can output stereo through spdif fine but to encode full 5.1 you need this plugin.

---

### Post by Catscrash on 2009-03-27
hi, 
which version did you install now?
with the 15-test i have the following problem with a52 plugin:

```
D: alsa-util.c: Trying pulseaudio with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Cannot open shared library /usr/lib/alsa-lib/libasound_module_pcm_a52.so
I: alsa-util.c: Error opening PCM device pulseaudio: No such file or directory
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=pulseaudio rate=48000 channels=6 sink_name=alsa_surround mmap=0"): initialization failed.
E: main.c: Module load failed.
E: main.c: Konnte Daemon nicht initialisieren.

```

but the file is there

```

catscrash@catscrash-desktop /usr/lib/alsa-lib % ll | grep a52
-rwxr-xr-x 1 root root 1,4K 2009-03-27 23:25 libasound_module_pcm_a52.la*
-rwxr-xr-x 1 root root  63K 2009-03-27 23:25 libasound_module_pcm_a52.so*
catscrash@catscrash-desktop /usr/lib/alsa-lib %  
```

it's from alsa-plugins-1.0.19 and installed via sudo make install

---

### Post by Catscrash on 2009-03-27
same problem with pulseaudio from jaunty... (0.9.14)

---

### Post by Catscrash on 2009-03-27
okay i forgot to install the build-deps and libavcodec-dev, so now i have the next problem ;-)

with 0.9.15~test i get the following:
```

I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D1p failed
I: alsa-util.c: Error opening PCM device a52: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=a52 rate=48000 tsched=0 channels=6 sink_name=alsa_surround"): initialization failed.
E: main.c: Module load failed.
E: main.c: Konnte Daemon nicht initialisieren.

```

i found via google this: [https://tango.0pointer.de/pipermail/pulseaudio-discuss/2008-February/001436.html](https://tango.0pointer.de/pipermail/pulseaudio-discuss/2008-February/001436.html)

when i follow that and disable hal-detect pulseaudio finally starts, but i have no sound at all and my receiver keeps saying "Unlocked" - "digital 5.1" - "unlocked" - "digital 5.1" ... the pulseaudio volume-meter also shows mostly zero output

with 0.9.14 the daemon starts without disabling hal-detect module but i still get no sound, same problem as with 0.9.15~test and hal-detect disabled...

edit:
after a restart this morning (still version 0.9.14) i at least hear something when i play the test sound, but it sounds like crap... the sound comes and goes twice a second...
listen here:
[http://catscrash.info/gnome-test-sound.ogg](http://catscrash.info/gnome-test-sound.ogg)

and i always get these error-messages:

```

I: module-tunnel.c: Server signalled buffer overrun/underrun.
D: protocol-native.c: Requesting rewind due to end of underrun.
D: module-tunnel.c: Server reports playback started.
D: protocol-native.c: Requesting rewind due to end of underrun.
I: module-tunnel.c: Server signalled buffer overrun/underrun.
D: protocol-native.c: Requesting rewind due to end of underrun.
D: protocol-native.c: Requesting rewind due to end of underrun.

```

---

### Post by danwood76 on 2009-03-28
The mmap=0 should be deleted from the config line as 0.9.15 works that stuff out automagically and gets upset by that.

The other this is you should really compile the plugin to be the same as your current alsa version.
You can get your currently installed source by doing 
apt-get source alsa-plugins

On a fresh install of the jaunty beta I got it working using this method.
The test sound is the same on mine, really choppy, but all audio plays completely fine.

---

### Post by Catscrash on 2009-04-01
with the pulseaudio-version that just came in (test7) it finally works again great :-)

everything you have to do now is putting 

```

pcm.a52 {
	type a52 
	@args.0 {
		type integer 
		default 0 
		}
    }

```

to your .asoundrc, thats it, no additional lines at default.pa, nothing.
then you can go to pavucontrol and select digital output 5.1 and thats it :-)

a few cracks every like 20 seconds at the moment, but thats it, if someone knows how to get rid of them too, i would be perfectly happy ;-)

---

### Post by danwood76 on 2009-04-01
Like I said, on a fresh install of jaunty beta it works perfectly with the previous method.

You might try turning the fragment count to 5 and the fragment size to 25 ms in the daemon.conf.
That should take care of the clicking, if it doesnt I would reinstall the previous version of pulse and alsa (you will have to remove the ppa and remove all the pulse and alsa packages and reinstall)

Off topic, you know its april fools day when the ubuntu forums go pink!
Tho its after 12 so they are the fools!

---

### Post by danwood76 on 2009-04-17
I've just come back home after being away for a few weeks and it seems the pulseaudio updates in the couple of weeks have broken my a52 again.
Bit of a pain, just upgraded to the 15 version via the ppa and the sound dropping is unbearable.

I might wait until the official jaunty release comes out, until then I'm back on a 2.0 setup (upmixed by my amp)

---

### Post by jonasback on 2009-04-21
Yeah, not working for me either.. I hope they will fix this issue in the stable Jaunty release.. :/

---

