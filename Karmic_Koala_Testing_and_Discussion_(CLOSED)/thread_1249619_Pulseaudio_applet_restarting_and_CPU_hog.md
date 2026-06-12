---
title: "Pulseaudio applet restarting and CPU hog"
date: 2009-08-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ace214 on 2009-08-25
I have 9.16-test6 installed and it is hogging my CPU all the time, even when there are no sound events going on. Also, the applet will disappear and reappear periodically.

Anybody else having this problem? It's making my laptop run so hot I think I'm gonna stay off Ubuntu for a couple days... :-(

---

### Post by crimsun on 2009-08-25
> **ace214 said:**
> I have 9.16-test6 installed and it is hogging my CPU all the time, even when there are no sound events going on. Also, the applet will disappear and reappear periodically.

The ... applet? What applet?

---

### Post by ace214 on 2009-08-25
The new volume control applet...

The one in the attached screenshot that opens the opened window (in between the shutter icon and the dropbox icon).

Is there some sort of pulseaudio log I could post?

---

### Post by crimsun on 2009-08-25
> **ace214 said:**
> Is there some sort of pulseaudio log I could post?

killall pulseaudio;pulseaudio -vvvv

Try using pavucontrol instead of the volume/mixer applet.

---

### Post by ace214 on 2009-08-25
Your command didn't work- it wouldn't let me restart it because it had already restarted itself. It was complaining about duplicate processes or something. Anyway, I figured out what it was- pulseaudio was trying to initialize the microphone on my webcam.

I typed pulseaudio into a terminal and got this:
```
E: module-alsa-card.c: Failed to find a working profile.
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="usb-Microsoft_Microsoft___LifeCam_NX-6000-02" card_name="alsa_card.usb-Microsoft_Microsoft___LifeCam_NX-6000-02" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Soft CPU time limit exhausted, terminating.
E: cpulimit.c: Received request to terminate due to CPU overload.

```

The last shows why it kept restarting.

So, unplugging my webcam takes the load off of the CPU, but that is obviously not a solution for when I want to Skype or whatever. I would LOVE to get the microphone on the webcam working because it hasn't in Ubuntu yet, but first, I would just like to keep it from overloading my CPU when the camera is plugged in.

---

### Post by crimsun on 2009-08-25
> **ace214 said:**
> ```
E: module-alsa-card.c: Failed to find a working profile.
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="usb-Microsoft_Microsoft___LifeCam_NX-6000-02" card_name="alsa_card.usb-Microsoft_Microsoft___LifeCam_NX-6000-02" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Soft CPU time limit exhausted, terminating.
E: cpulimit.c: Received request to terminate due to CPU overload.

```

That's a linux (ALSA) issue dealing with enumeration of supported sample rates; it has been fixed today and merged into linux-2.6.git (and thus will ship in Karmic).

---

### Post by rajeev1204 on 2009-08-26
Hello,iam having this problem of volume control icon disappear and appearing again.

And all i hear is static now.This happened after latest updates.

---

### Post by dumblebee100 on 2009-08-26
I too observed this problem ...
my cpu was 100% on idle ..that was ridiculous 

so I shifted to windows for my daily work ..

since people here are telling me that bug is fixed ...I gonna install my updates ....

---

### Post by ace214 on 2009-08-30
I am still experiencing this, even after upgrading 2.6.31-8. Any idea which version the fix will be in.

---

### Post by virx on 2009-09-05
Same here:
```
$ tail /var/log/syslog
Sep  5 12:30:17 kast pulseaudio[4363]: module-alsa-card.c: Failed to find a working profile.
Sep  5 12:30:17 kast pulseaudio[4363]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="pci-0000_03_09.0" card_name="alsa_card.pci-0000_03_09.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Sep  5 12:30:17 kast pulseaudio[4363]: module-alsa-card.c: Failed to find a working profile.
Sep  5 12:30:17 kast pulseaudio[4363]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="pci-0000_03_09.0" card_name="alsa_card.pci-0000_03_09.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Sep  5 12:30:17 kast pulseaudio[4363]: module-alsa-card.c: Failed to find a working profile.
Sep  5 12:30:17 kast pulseaudio[4363]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="pci-0000_03_09.0" card_name="alsa_card.pci-0000_03_09.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Sep  5 12:30:17 kast pulseaudio[4363]: module-alsa-card.c: Failed to find a working profile.
Sep  5 12:30:17 kast pulseaudio[4363]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="pci-0000_03_09.0" card_name="alsa_card.pci-0000_03_09.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
Sep  5 12:30:17 kast pulseaudio[4363]: module-alsa-card.c: Failed to find a working profile.
Sep  5 12:30:17 kast pulseaudio[4363]: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="1" name="pci-0000_03_09.0" card_name="alsa_card.pci-0000_03_09.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.

```

I am using 
pulseaudio: 1:0.9.16~test6-3-g57e1-0ubuntu2
kernel: 2.6.31-9-generic


Any hope it will be fixed?



EDIT: Got sound back. Found it from launchpad:
comment /etc/pulse/default.pa file to:
```
### Automatically load driver modules depending on the hardware available
#.ifexists module-udev-detect.so
#load-module module-udev-detect
#.else
### Alternatively use the static hardware detection module (for systems that
### lack udev support)
load-module module-detect
#.endif

```
killall pulseaudio
pulseaudio

---

### Post by X10N on 2009-09-05
If I open any app when I have any kind of audio on crashes Pulse. Even Transmission borked Rhythmbox :confused:

---

### Post by 0x656b694d on 2009-09-05
Hello,

do we have an open critical bug on this issue yet?

default pulse installation doesn't have any default.pa files neither in /etc/pulse nor in ~/.pulse/ directories. I added one to the ~/.pulse and it fixed the issue.

**update:**
ah, no default.pa if i install only pulseaudio package with its deps. But it appeared after i installed paprefs.

---

### Post by Kazade on 2009-09-06
I'm also getting this bug, is there a bug report for it somewhere?

---

### Post by 0x656b694d on 2009-09-06
Looks like [this one]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/382440") is about our problem.

---

### Post by papangul on 2009-09-06
> **X10N said:**
> If I open any app when I have any kind of audio on crashes Pulse. Even Transmission borked Rhythmbox :confused:
Are you using hda-intel?

---

### Post by 0x656b694d on 2009-09-07
Ok, got alsa and pulseaudio updated today.
pulseaudio:
[INDENT]Architecture: amd64
Version: 1:0.9.16~test7-14-g7ca81-0ubuntu1
[/INDENT]libasound2:
[INDENT]Architecture: amd64
Version: 1.0.20-3ubuntu5[/INDENT]

Now it doesn't crash, but just uses 100% of CPU printing the following:
```
E: module-alsa-card.c: Failed to find a working profile.
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id="2" name="pci-0000_08_01.0" card_name="alsa_card.pci-0000_08_01.0" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1""): initialization failed.
```
I have intel audio on board plus PCI TV-tuner card, which is the second audio device:
```
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
...
08:01.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev f0)

```
With the suggested default.pa changes pulseaudio sometimes cannot get list of devices and i cannot set the desired configuration (5.1 or stereo).

---

### Post by blackest_knight on 2009-09-11
pulseaudio here hogs the cpu but i think its due to not having a profile for my tv cards. Its just busy failing :(

taking pulse off my system and just using alsa gives me working audio after a fashion the AC97 sound gives low volume output on the audio out (green) 
very high distorting volume on the audio in (blue)

Anyone know how to give it a suitable profile?

pulseaudio in its current state is unuseable for me luckily its not needed for audio to work.

---

