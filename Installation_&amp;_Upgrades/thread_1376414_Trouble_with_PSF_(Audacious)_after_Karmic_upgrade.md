---
title: "Trouble with PSF (Audacious) after Karmic upgrade"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by Diya on 2010-01-09
Audacious wasn't working at all at first but then I installed the latest release (2.2.0) and plugins (plugins-2.2) and that made it work in karmic only under PulseAudio, however.

It plays everything smoothly now except for PSF files (Which is the main reason I'm using it in the first place). When I play any PSF file, the CPU usage goes through the roof and the playback is very distorted. This wasn't the case in past ubuntu releases such as Hardy for example.

Also, the plugins don't include any MIDI plugin so I can't play MIDI files with Audacious. I didn't try installing the version 2.1 MIDI plugin because I'm guessing that it's not compatible with Audacious 2.2

---

### Post by Diya on 2010-01-16
1st weekly pump.

I'm sick of Audio Overload and the poor MIDI soundfont of Totem. I really miss Audacious.

---

### Post by elitenoobboy on 2010-01-16
Where/How did you install you version of audacious? I know that the official builds for ubuntu break up the input plugins into 2 different packages, one of them being an extra package, which, I assume would have the midi plugin that you want, assuming that it is not in the plugin package that you installed. As for the psf, it sounds like an actual bug, but psf is working in the latest svn that I am using, so you might want to try using that.

---

### Post by Diya on 2010-01-16
This is exactly what happened:

I used to have the latest Audacious (2.1) in the repositories installed + plugins (2.1) + plugins-extra (2.1)

When I upgraded to Karmic, audacious stopped working altogether. So I re-installed it but it still didn't work. I made a thread here on the forum and people suggested that I should install version 2.2 because version 2.1 is buggy in Karmic.

After uninstalling Audacious 2.1 and its plugins, I went to Audacious website and grabbed the two files there:
* audacious-2.2.0.tgz
* audacious-plugins-2.2.0.tgz

Installed the two files the usual way (./configure, make, make install, etc) and it's now playing all files good except PSF (buggy) and MIDI (no plugins-extra 2.2).

Audacious-plugins-extra 2.1 is dependent on Audacious 2.1. Any ideas?

---

### Post by elitenoobboy on 2010-01-16
PSF may be bugged on 2.2 audacious, as I tried it with a week old dev version and it crashed audacious. Try these instead:

[http://hg.atheme.org/audacious/audacious/archive/9badf5bf2b21.tar.bz2](http://hg.atheme.org/audacious/audacious/archive/9badf5bf2b21.tar.bz2)
[http://hg.atheme.org/audacious-plugins/audacious-plugins/archive/a6398f0217d7.tar.bz2](http://hg.atheme.org/audacious-plugins/audacious-plugins/archive/a6398f0217d7.tar.bz2)

The dev versions sometimes have bugs, but I tested the specific builds I listed, and psf and midi work with them.
Make sure you do "sudo apt-get build-dep audacious audacious-plugins" before you begin compiling them to make sure you have all build deps installed, and do "./autogen.sh" before you ./configure them, and for the audacious plugins, check the output at the end of configuring; it should give you a list of everything that it will support when making, so you can check that something such as midi support will be included. Make sure you install audacious completely before you config or compile audacious-plugins.

Also, instead of make install, it is best to do "sudo checkinstall", which will install it using the debian packager, which makes it easier to uninstall later. Just answer the default for most of the questions, changing the version number to something like "2.3dev" when it gives you the option.

---

### Post by Diya on 2010-01-17
Thanks a lot! PSF is working perfectly in that version.

There is no MIDI plugin, however.

---

### Post by elitenoobboy on 2010-01-17
> **Diya said:**
> There is no MIDI plugin, however.


Is it not being built from the plugin's source, or is it just not working? After you ./configure the audacious-plugin package, you should see something like   ```
MIDI modular plugin (amidi-plug):       yes
    -> ALSA backend:                      yes
    -> FluidSynth backend:                yes
```
in the output, under input plugins, and an "amidi-plug.so" in /usr/local/lib/audacious/input/. If there is a plugin, it may need to be configured.
[http://linuxtechie.wordpress.com/2008/01/22/how-to-ubuntu-midi-playback-with-audacious/](http://linuxtechie.wordpress.com/2008/01/22/how-to-ubuntu-midi-playback-with-audacious/)
I got it to work after selecting fluidsynth with both of the sf2 files from here:
[http://sounds.resonance.org/patches.py?Action=item&ItemId=6816](http://sounds.resonance.org/patches.py?Action=item&ItemId=6816)

Also, keep in mind that you can always convert these rare or old formats to something more common, by selecting audacious' filewriter output plugin in the audio tab, and then configure it to convert to something such as vorbis files. Then you won't have to rely on the not so often used input plugins that may or may not always work.

---

### Post by Diya on 2010-01-17
> **elitenoobboy said:**
> Is it not being built from the plugin's source, or is it just not working? After you ./configure the audacious-plugin package, you should see something like   ```
MIDI modular plugin (amidi-plug):       yes
    -> ALSA backend:                      yes
    -> FluidSynth backend:                yes
```
in the output, under input plugins, and an "amidi-plug.so" in /usr/local/lib/audacious/input/.

It wasn't built from the plugin's source.

```
MIDI modular plugin (amidi-plug):       no
    -> ALSA backend:                      auto
    -> FluidSynth backend:                auto
```

There is no "amidi-plug.so" in /usr/local/lib/audacious/input/.

---

### Post by Diya on 2010-01-21
MIDI pump

---

### Post by elitenoobboy on 2010-01-22
The only other advice that I can offer is to check all of the output from the ./configure, and look for errors or any place where it mentions missing packages or dependencies, as the amidi plugin should be compiled by default. Maybe try forcing it by doing "./configure --enable-amidiplug"

---

### Post by Diya on 2010-01-22
> **elitenoobboy said:**
> "./configure --enable-amidiplug"
This worked like a charm!
Thanks for helping me so much. Audacious works perfectly now!

Another problem and it's fix just for the record:

When I did "./configure --enable-amidiplug" I got this:
```
MIDI modular plugin (amidi-plug):       yes
    -> ALSA backend:                      yes
    -> FluidSynth backend:                **no**
```
What? No FluidSynth backend? but I had FluidSynth installed and working before upgrading to Karmic, what's wrong! :o

So I "./configure --help" and learned about "./configure --enable-amidiplug-flsyn", I got this error:
```
configure: error: Cannot find FluidSynth development files (ver >= 1.0.6), but compilation of AMIDI-Plug FluidSynth backend has been explicitly requested; please install FluidSynth dev files and run configure again
```

Checked Synaptic for FluidSynth and found out that it IS installed BUT the development files are not installed (libfluidsynth-dev). So I installed them and ran the ./configure again:
```
MIDI modular plugin (amidi-plug):       yes
    -> ALSA backend:                      yes
    -> FluidSynth backend:                **yes**
```
Tada! MIDI and PSF are working under Karmic!

Thanks a lot elitenoobboy!

---

### Post by Diya on 2010-01-22
Horrible MIDI playback. Some notes are missing and the tempo is not consistent. RAM/CPU usage has nothing to do with it. (Processor 10% in use, memory 25% in use).

Tried playing around with the buffer size etc but the playback is still horrible. so I'm guessing the amidi plugin for this version is a little bit buggy. lol

---

