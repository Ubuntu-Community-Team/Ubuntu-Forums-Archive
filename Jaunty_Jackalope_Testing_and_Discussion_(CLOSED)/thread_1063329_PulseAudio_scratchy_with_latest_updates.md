---
title: "PulseAudio scratchy with latest updates?"
date: 2009-02-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2009-02-07
Has anyone else noticed that startup sounds and anything running with PulseAudio will sound scratchy or distorted?

This doesn't occur when using ALSA exclusively or in a media player like MPlayer.

---

### Post by ronacc on 2009-02-07
I've noticed it on the startup sounds for a few days .

---

### Post by nIRV on 2009-02-07
+1

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/322344](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/322344)

---

### Post by Starks on 2009-02-07
> **nIRV said:**
> +1

[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/322344](https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/322344)

Thanks.

---

### Post by W2IBC on 2009-02-08
I have noticed when using gnome desktop sound is scratchy 
but using KDE sound is fine for me

---

### Post by FishRCynic on 2009-02-08
fine for logon
scratchy when logging on

---

### Post by xens on 2009-02-08
> **fishrcynic said:**
> fine for logon
scratchy when logging on

+1

---

### Post by Starks on 2009-02-15
Still not fixed.

;_;

---

### Post by Cybie257 on 2009-02-15
I've only noticed the problem with Alpha 4 release ofJaunty. Both 32-bit and 64-bit. 8.10 seems to be fine on both my laptop and Tower. Now that I think about it, not sure if PulseAudio is active on my laptop, but when I tried the Jaunty Alpha 4 on my laptop, the sound was horribly scratchy. On my tower, I had to recently activate/install PulseAudio in order to have sound working in both my VirtualBox machine and real machine at the same time. Before doing that, I only had a choice of sound in one OR the other, not both. 

-Cybie

---

### Post by scaine on 2009-02-15
Same here - scratchy/popping audio during the login sound.  Funnily enough, video playback via gstreamer/totem doesn't exhibit any problems at all.  I've subscribed to that bug, but I'm not sure I have anything to add to it.

---

### Post by PythonPower on 2009-02-15
It's also scratchy when logging in for me. I only installed today's build and installed all updates. Playing music is fine after logging in; and logging out isn't effected.

---

### Post by Yes_It's_Me on 2009-02-16
After todays update, logging in now produces the sound as expected (it was all popping and stuff before). Music also seems to play with less/no skipping issues.

---

### Post by taavikko on 2009-02-19
Anyone else experiencing this?

At random times PA crashes:
```
var/log/user.log:Feb 19 17:41:45 elite pulseaudio[4167]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058055282162560 bytes (418293516404 ms)
```

I was under impression that PA should restart automatically...

Hardware:
```
lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801JI (ICH10 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

```

---

### Post by markbuntu on 2009-02-19
I was having some problems with Amarok being scratchy and glitching out with pulseaudio and crashing and phonon claiming pulseaudio not working and cpu useage skyrocketing but i seem to have fixed that by the following

Edit /etc/pulse/daemon.conf
uncomment these lines

high-priority = yes
nice-level = -11

change these to the following

default-fragments = 5
default-fragment-size-msec = 25

I think it was the last 2 that did the trick. You should also check users and groups and make sure root and user are enabled as members of the following groups

pulse
pulse-access
pulse-rt

---

### Post by ugkbunb on 2009-02-20
In VLC if I check the option to send audio through pulseaudio I get incredibly scratchy sound... this seems to go away when I change it to ALSA output.

---

### Post by taavikko on 2009-02-20
> **ugkbunb said:**
> In VLC if I check the option to send audio through pulseaudio I get incredibly scratchy sound... this seems to go away when I change it to ALSA output.

Have you installed vlc-plugin-pulse
Somehow it isn't installed with vlc (at least wasn't when I installed it)

---

### Post by ugkbunb on 2009-02-20
> **taavikko said:**
> Have you installed vlc-plugin-pulse
Somehow it isn't installed with vlc (at least wasn't when I installed it)

I was hoping it would be some as simple as that... but alas nope:

> sudo apt-get install vlc-plugin-pulse
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vlc-plugin-pulse is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

well everything seems to work fine have it set to ALSA (it seems pulseaudio is picking up the ALSA input just fine).

Also -- I have been unable to open pavucontrol with PulseAudio 0.9.15... it flashes open then segfaults immediately.

---

### Post by ugkbunb on 2009-02-20
thanks to the above poster... his tip plus a couple other changes seems to have fixed all my problems.

/etc/pulse/daemon.conf 
daemonize=yes
resample-method = src-sinc-best-quality 
system-instance = yes 
high-priority = yes 
nice-level = -11
default-fragments = 5
default-fragment-size-msec = 25

/etc/default/pulseaudio 
PULSEAUDIO_SYSTEM_START=1

I realize this is not the "recommended" way of running it (however my box is a single usr machine) but it fixes all my problems A) scratchy sound B) not correctly starting on boot and C) for some reason it fixed my access to pavucontrol.

pavucontrol segfaults when launched under a user as "pulseaudio &" ... however when run as a deamon systemwide it works fine.

---

### Post by Starks on 2009-02-20
Do the semicolons need to be removed?

---

### Post by ugkbunb on 2009-02-20
> **Starks said:**
> Do the semicolons need to be removed?

Yep, they are commented out and set to what the defaults are. So whichever you change uncomment.

---

### Post by Starks on 2009-02-21
Are these needed too?

```
default-fragments = 5
default-fragment-size-msec = 25
```

---

### Post by kurros on 2009-02-21
> **taavikko said:**
> Anyone else experiencing this?

At random times PA crashes:
```
var/log/user.log:Feb 19 17:41:45 elite pulseaudio[4167]: alsa-util.c: snd_pcm_avail_update() returned a value that is exceptionally large: 13835058055282162560 bytes (418293516404 ms)
```I was under impression that PA should restart automatically...

I have the same problem with an Intel Corporation 82801I (ICH9 Family).

This was apparently thought to be fixed with [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/319118](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/319118) but I just added my comments there as well[]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/323976")

---

### Post by ugkbunb on 2009-02-21
> **Starks said:**
> Are these needed too?

```
default-fragments = 5
default-fragment-size-msec = 25
```


woops! yah I changed my numbers to those... I am not too sure what changes fixed the scratchyness but I am sure that the following is what fixed no sound on startup.

/etc/pulse/daemon.conf 
daemonize=yes
system-instance = yes 


/etc/default/pulseaudio 
PULSEAUDIO_SYSTEM_START=1

Also I set the following to the best (also highest cpu)...
resample-method = src-sinc-best-quality 

from best to worst the options are:
src-sinc-best-quality, src-sinc-medium-quality, src-sinc-fastest, speex-float-{10-0}, speex-fixed-{10-0}, ffmpeg, src-zero-order-hold, src-linear, trivial

---

### Post by Starks on 2009-02-24
It seems that either the repo updates or Pulseaudio/Alsa ppas have fixed the scratchiness.

**Edit: Nevermind, I am mistaken. Nothing has been fixed.**

---

### Post by OliW on 2009-02-24
> **Starks said:**
> **Edit: Nevermind, I am mistaken. Nothing has been fixed.**

Heh. I've had that a couple of times. You feel it's fixed and ten minutes later it goes through a massive bout of skipping and scratching.

But it does *seem* better after today's updates.

---

