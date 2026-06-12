---
title: "ubuntu 8.04 plays only AC3 no PCM over spdif"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by laluz on 2008-05-04
My card is connected to the DAC via spdif. I had no problem with Gutsy and have just upgraded to Hardy. Now I can only play files with AC3 (mplayer). Alsamixer runs fine and I have set 100% on all channels. Still no sound.

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


sudo lshw -C sound
  *-multimedia
       description: Audio device
       product: MCP55 High Definition Audio
       vendor: nVidia Corporation
       physical id: 6.1
       bus info: pci@0000:00:06.1
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi ht bus_master cap_list
       configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2 module=snd_hda_intel

lsmod |grep snd
snd_hda_intel         344728  6
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  21 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd


I have noticed that a lot of packages were deleted after upgrade, like amarok, may be I am still missing something?

---

### Post by laluz on 2008-05-04
it seems like alsa is not configured/not functional in any way. I do not see any alsa modules in lsmod, amarok-xine could not configure no sound driver... but kaffeine plays movies with dolby sound just fine.

---

