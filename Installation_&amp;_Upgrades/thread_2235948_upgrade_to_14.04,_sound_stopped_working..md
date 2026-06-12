---
title: "upgrade to 14.04, sound stopped working."
date: 2014-07-23
forum: Installation &amp; Upgrades
---

### Post by davea42 on 2014-07-23
System is Ubuntu (across many upgrades), not xubuntu. 
With Unity in ascendence I started using xfce/thunar
exclusively a couple releases ago (13.04?).   Upgrade 13.10 to 14.04 resulted in sound
stopping completely. Not a click or a burp. Silence.

alsamixer says nothing is muted.

Volume control on top panel menu says volume set high.
No system sounds, no youtube sound, no sound from an MP4 video I made.

Been googling and searching for a day now and tried various suggestions on these forums
and from other places. No help.

I don't know what information  to use or look for to determine what is going wrong 
with sound. This is a desktop with Intel sound on the motherboard (tsched=0 is important
for decent sound) but I get no sound at all since 14.04.


q2 502: lsmod |grep snd
snd_hda_codec_analog    14537  1 
snd_hda_intel          42730  1 
snd_hda_codec         164067  2 snd_hda_intel,snd_hda_codec_analog
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                85501  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25135  1 snd_seq_midi
snd_seq                55383  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              28584  2 snd_pcm,snd_seq
snd                    60871  12 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog,snd_seq_midi
soundcore              12600  1 snd


Thanks in advance for any suggestions on how to diagnose this.

---

### Post by davea42 on 2014-07-23
I booted into an Ubuntu 11.04 CD and I had a proper gui to turn on system sounds
and that worked, so I had system sounds.  I'm just not finding a sensible gui.
MultiMedia->Pulse Audio Volume Control
is there, but is no help for system sound control.
Something missing.

---

### Post by davea42 on 2014-07-23
Ok. 'Playback' in PulseAudio Volume Control is there for system sounds, but
I set at 100% and no system sounds come out. Still no joy.

---

### Post by davea42 on 2014-07-24
Fixed. in  
alsamixer
use right arrow enough times to get the column labeled <Auto-Mute> where it says enabled
and use down-arrow to turn it to disabled.
Sound immediately started working.

---

