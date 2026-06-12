---
title: "Audio mixer issue with LFE"
date: 2009-10-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-10-30
I'm going to jump on this one as quick as possible as it's the only thing that doesn't work properly in Karmic for me.

I have a laptop (Dell Precision M90) that has a sub-woofer controlled by the LFE channel. In Jaunty, I was able to choose which channels were controlled by the volume control, but this has been changed in Karmic. Now, the volume control increases PCM first, followed by LFE, followed by Master. PCM and LFE increase very quickly compared to Master meaning audio is blaring out of my sub-woofer before the main speakers are hardly audible.

This was reported on Launchpad [bug 410948]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/410948").

I hope this can be solved for Lucid Lynx.

---

### Post by phenest on 2009-11-04
This is being currently discussed in [bug 410948]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/410948").
To sum up, here's what you do:
```
sudo nano /etc/pulse/default.pa
```
Uncomment the line : #load-module module-alsa-sink
And add: control=PCM
So it reads: load-module module-alsa-sink control=PCM
Further down where it reads: load-module module-udev-detect
Add: ignore-dB=1
So it reads: load-module module-udev-detect ignore_dB=1
And save. You may need to restart for changes to take effect.
The volume control will now only adjust the PCM channel, so you may want to turn the Master and LFE to maximum in alsamixer.

And if you're getting that crackling sound:
```
sudo nano /etc/modprobe.d/alsa-base.conf
```
Comment out the last line which reads: options snd-hda-intel power_save=10 power_save_controller=N

---

### Post by phenest on 2010-01-31
A new thing I've seen in Preferences>Sound 'Output' tab, is 2 options:
1. Internal Audio
2. Internal Audio Analog Stereo

The first changes the volume slider, so I'm able to exceed 100% volume, but is too quiet for headphones (!). The second resorts to using the Master channel for volume control (good for headphones, but not laptop speakers), whereas the first allows control via PCM (changes made to /etc/pulse/default.pa allow for this).

What is going on? This is a mess! Is Gnome to blame for this or PA? Daniel's comments in the bug report suggest is is definitely not an Ubuntu issue.

---

