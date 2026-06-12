---
title: "pSX under Lucid Lynx Beta1"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by -siGGi- on 2010-03-22
i already tried this [http://ubuntuforums.org/showpost.php?p=6127662&postcount=246](http://ubuntuforums.org/showpost.php?p=6127662&postcount=246)
and the killall pulseaudio command also did not help
terminal says

 * PulseAudio configured for per-user sessions
Home directory /home/ubuntu not ours.
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
[src/linux/sound.cpp, line 582]: 'snd_pcm_open(&pcm_handle,dev->info->device_fname,SND_PCM_STREAM_PLAYBACK,0)' returned 'Device or resource busy'
pSX: pcm_params.c:2274: snd_pcm_hw_refine: Assertion `pcm && params' failed.
Aborted (Speicherabzug geschrieben)


any ideas how to solve this problem?

---

