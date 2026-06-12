---
title: "Skype stoped working"
date: 2009-08-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Hideaki on 2009-08-03
As of today's update Skype from the medibuntu repositories stopped working.

It was working fine yesterday, but I am now getting:

```

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)

```

When I attempt to start Skype.

---

### Post by danf_1979 on 2009-08-04
I don't know how to fix your problem, but if I where you, I would check those files with $ apt-file search filename, and then see if they are installed. Or maybe a symlink is missing somewhere.

---

### Post by rewz on 2009-08-04
Try to edit /usr/share/alsa/pulse.conf
and put a comment on /usr/share/alsa/pulse.conf

---

### Post by miegiel on 2009-08-04
> **Hideaki said:**
> As of today's update Skype from the medibuntu repositories stopped working.

It was working fine yesterday, but I am now getting:

```


When I attempt to start Skype.

I've got the same, but only after I installed the latest updates and I get some **more erros**. Before the updates it worked fine.

I can't remember the updates exactly, I just skimmed the dkpg.log, it's a really long list :| I remember kernel 2.6.31-5 (64bit) and that it was a package or 30 in total. Maybe I'll condense the long list to a short 1 if I have time later :)

[CODE]user@machine:~$ skype
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "gail": /usr/lib/gtk-2.0/modules/libgail.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "gail": /usr/lib/gtk-2.0/modules/libgail.so: wrong ELF class: ELFCLASS64
Gtk-Message: Failed to load module "atk-bridge": /usr/lib/gtk-2.0/modules/libatk-bridge.so: wrong ELF class: ELFCLASS64
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)
```

**ps** What does this ELF want anyway? I thought I had a gnome :twisted:

---

### Post by miegiel on 2009-08-04
> **rewz said:**
> Try to edit /usr/share/alsa/pulse.conf
and put a comment on /usr/share/alsa/pulse.conf

If you meant changing the line to ```
#			"/usr/share/alsa/pulse-alsa.conf"
``` that didn't work :(

---

### Post by psyke83 on 2009-08-04
> **rewz said:**
> Try to edit /usr/share/alsa/pulse.conf
and put a comment on /usr/share/alsa/pulse.conf

Don't mess with that - it will cause all ALSA applications not to work with PulseAudio.

---

### Post by psyke83 on 2009-08-04
> **Hideaki said:**
> As of today's update Skype from the medibuntu repositories stopped working.

It was working fine yesterday, but I am now getting:

```

Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:909:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)

```

When I attempt to start Skype.

Have you tried installing "skype-static" instead?

---

### Post by portis on 2009-08-04
I'm using amd64 karmic and I got the same problem after un upgrade of lib32asound2-plugin. libasound_module_conf_pulse.so is missing from this package. I extracted this file in the corresponding 32bit package and copied it to /usr/lib32/alsa-libs/ , and now everything's fine.
I reported here: [https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/408615](https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/408615)

---

### Post by miegiel on 2009-08-04
> **portis said:**
> I'm using amd64 karmic and I got the same problem after un upgrade of lib32asound2-plugin. libasound_module_conf_pulse.so is missing from this package. I extracted this file in the **corresponding 32bit package** and copied it to /usr/lib32/alsa-libs/ , and now everything's fine.
I reported here: [https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/408615](https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/408615)

I was trying that, but I'm having some trouble finding the right package.

---

### Post by harry2006 on 2009-08-04
has nyone got a solution for the same?

---

### Post by Labello on 2009-08-04
well i have been using skype since hardy from medibuntu with the static-oss package. and i do it right now as well and it works.

---

### Post by miegiel on 2009-08-04
> **Labello said:**
> well i have been using skype since hardy from medibuntu with the static-oss package. and i do it right now as well and it works.

Did you update yet today? Mine worked till I updated. And are you using 64bit 9.10?

---

### Post by Slug71 on 2009-08-04
I just tried to test if im having the same issue but it seems the NM updates have broken my wireless. Hopefully there will be a fix soon.

---

### Post by Slug71 on 2009-08-04
Nope, starts for me. Installed from Medibuntu repos too and on 64bit.



On a side note, I really wish Skype would give us a new version though. Its long overdue and it would be nice if they gave us better/newer Pulse and Alsa support.

---

### Post by BCurtisWX on 2009-08-04
> **Slug71 said:**
> Nope, starts for me. Installed from Medibuntu repos too and on 64bit.



On a side note, I really wish Skype would give us a new version though. Its long overdue and it would be nice if they gave us better/newer Pulse and Alsa support.

Its either that or empathy not supporting all protocols with voice/video.  Why can't linux wrap itself around voice and video.. its the biggest downside of Linux right now IMO.

---

### Post by taavikko on 2009-08-04
> **Slug71 said:**
> 
On a side note, I really wish Skype would give us a new version though. Its long overdue and it would be nice if they gave us better/newer Pulse and Alsa support.

there might actually to be a chance that skype ceases to exist as we know it...
[http://www.zdnetasia.com/news/business/0,39044229,62056580,00.htm](http://www.zdnetasia.com/news/business/0,39044229,62056580,00.htm)

(don't use it so don't care, just an info blast for all the rest :) )

---

### Post by Truthiswithin on 2009-08-04
> **portis said:**
> I'm using amd64 karmic and I got the same problem after un upgrade of lib32asound2-plugin. libasound_module_conf_pulse.so is missing from this package. I extracted this file in the corresponding 32bit package and copied it to /usr/lib32/alsa-libs/ , and now everything's fine.
I reported here: [https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/408615](https://bugs.launchpad.net/ubuntu/+source/alsa-plugins/+bug/408615)

that should be "/usr/lib32/alsa-lib/" (no "s").  I can't get this to work on my system anyway... can you explain your fix in more detail?

---

### Post by Truthiswithin on 2009-08-04
Here's a fix that works for me (from [http://mapopa.blogspot.com/2008/10/skype-2.html]("http://mapopa.blogspot.com/2008/10/skype-2.html"))

Create /etc/ld.so.conf.d/alsa32.conf with the following contents:

> /usr/lib32/alsa-lib

After that, skype works fine.

---

### Post by Hideaki on 2009-08-05
> **Truthiswithin said:**
> Here's a fix that works for me (from [http://mapopa.blogspot.com/2008/10/skype-2.html]("http://mapopa.blogspot.com/2008/10/skype-2.html"))

Create /etc/ld.so.conf.d/alsa32.conf with the following contents:



After that, skype works fine.

I've tried that before and it doesn't work. I've also tried the skype-static packages, but I have no tired skype-static-oss.

None of the things I've tried fix the issue though.

I'm on Ubuntu Karmic 64-bit, btw.

---

### Post by kingborel on 2009-08-05
> **BCurtisWX said:**
> Its either that or empathy not supporting all protocols with voice/video.  Why can't linux wrap itself around voice and video.. its the biggest downside of Linux right now IMO.

[IMG]http://imgs.xkcd.com/comics/supported_features.png[/IMG]

---

### Post by Hideaki on 2009-08-05
I can confirm that using the skype-static-oss package from medibuntu solves the problem, but it seems like a work-around at best. I would be nice to get "native" skype(I really wish it was 64-bit...) working again.

---

### Post by miegiel on 2009-08-05
> **kingborel said:**
> [IMG]http://imgs.xkcd.com/comics/supported_features.png[/IMG]

Yeah, [_flash runs smooth fullscreen_]("http://ubuntuforums.org/showthread.php?p=7717588#post7717588"), what's that got to do with it anyway?

Of all the solutions posted here, only installing *skype-static-oss* helps a bit. Playback works, microphone doesn't and skype gets unhappy if I'm already using my soundcard for music. But at least it doesn't crash and I can always fallback to that really annoying OS if I need to make a call (don't do that to often anyway).

Still, it would be really nice if people would elaborate a bit more on how their solutions work. A "do this" solution provides little inspiration.

---

### Post by VMC on 2009-08-05
> **psyke83 said:**
> Have you tried installing "skype-static" instead?
Thank you! I never heard of skype-statc until you mentioned it. I was wondering around Medibuntu and saw it there. Installed it and UNBELIEVABLY it works. 

Skype - any flavour didn't work, or worked poorly under Linux. That's one of the reasons I keep Windows around.

The amazing thing is my video cam works, and that has not work on any program before. I'm not sure it it's Karmic, the kernel, or the general :). but now I even have video cam working.

---

### Post by Hideaki on 2009-08-07
The latest update to pulseaudio seems to have fixed things. I can now run the standard skype package, which is a relief cause skype-static-oss took the sound server hostage and wouldn't allow for any other program to play back audio =P

---

### Post by nystire on 2009-08-15
This issue still exists with a fresh install of Alpha 2 fully upgraded.

---

### Post by nhasian on 2009-08-15
> **nystire said:**
> This issue still exists with a fresh install of Alpha 2 fully upgraded.

if you installed alpha2 then fully upgraded it, your now alpha 4.

---

### Post by miegiel on 2009-08-15
Skype is running here again, but it still crashes when it tries to make sound. I'm running the "normal" skype and turned off all the sound effects for the notifications (like when someone sends you a message). I think I changed the skype startup sound when I tried the OSS version. This was probably what made skype crash at startup. Obviously I can't make calls (I think skype still crashes when people call me), but at least I can use it as an ordinary messenger.

---

### Post by laborg on 2009-08-15
For me Skype will only work reliable when using the OSS-version. Normal "Skype" doesn't work at all and "Skype-static" behaves dependent on the moon or so. I think it's time for google talk and empathy...

---

