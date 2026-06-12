---
title: "volume control channel problem"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by puccaso on 2009-09-29
i have a few channels on my system

my audio card is

Audio device: Intel Corporation 82801G (ICH7 Family)

when i turn the volume down from the menu bar, it turns down the MASTER CHANNEL, which leaves the WOOFER (LFE) ON...
i need the volume mixer to affect the PCM channel as standard,

how do i do this?

the old UI had an option, but the new PA/volume-mixer UI doesnt have it..

---

### Post by seamuso on 2009-09-30
Adding to this so it gets a little bump ..

I'm also having channel mixing issues -

Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)

dmesg-

hda_codec: Unknown model for ALC1200, trying auto-probe from BIOS...


I have 5.1 sound setup, independednt channels, not mixed by the speaker system (logitech x-540). If I set my output to stereo, I get sound across my front speakers .. all 3, left middle right. When I have them in 5.1, I get the same thing from audio sources that I know are only 2 channel audio files.

If I disable the center channel in Gnome Also Mixer, it mutes everything. If I unmute, it again plays across all 3 speakers.

Any ideas on this and how to make it stop?

---

### Post by Amaranth on 2009-09-30
> **puccaso said:**
> i have a few channels on my system

my audio card is

Audio device: Intel Corporation 82801G (ICH7 Family)

when i turn the volume down from the menu bar, it turns down the MASTER CHANNEL, which leaves the WOOFER (LFE) ON...
i need the volume mixer to affect the PCM channel as standard,

how do i do this?

the old UI had an option, but the new PA/volume-mixer UI doesnt have it..

There is no longer an option for this because pulseaudio is supposed to be using so called "flat" volume where it adjusts all the channels at once. Unfortunately there are still too many sound cards/codecs/whatever that have issues with this (they sound distorted when they get turned all the way up) so we've disabled this feature. Really the only way to have a GUI way of changing the volume for this woofer channel now is to turn that option back on. Just change flat-volumes to yes in /etc/pulse/daemon.conf

---

