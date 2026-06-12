---
title: "ALSA 1.0.20, STAC92xx chipset"
date: 2009-05-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by taavikko on 2009-05-29
Running Karmic on HP laptop dv5 with mentioned audio chipset, and user.log is reporting this:

```
May 29 17:43:50 hp-dv5 pulseaudio[19495]: pid.c: Stale PID file, overwriting.
May 29 17:43:51 hp-dv5 pulseaudio[19495]: alsa-sink.c: Unable to set switch: Operation not permitted
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c: snd_pcm_avail() returned a value that is exceptionally large: 16140901064495857200 bytes (384307168199 ms).
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c: snd_pcm_dump():
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c: Hooks PCM
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c: Its setup is:
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   stream       : PLAYBACK
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   access       : MMAP_INTERLEAVED
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   format       : S16_LE
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   subformat    : STD
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   channels     : 2
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   rate         : 48000
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   exact rate   : 48000 (48000/1)
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   msbits       : 16
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   buffer_size  : 3840
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_size  : 480
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_time  : 10000
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   tstamp_mode  : ENABLE
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_step  : 1
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   avail_min    : 480
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_event : 0
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   start_threshold  : -1
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   stop_threshold   : 8646911284551352320
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   silence_threshold: 0
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   silence_size : 0
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   boundary     : 8646911284551352320
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c: Slave: Hardware PCM card 1 'HDA ATI HDMI' device 3 subdevice 0
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c: Its setup is:
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   stream       : PLAYBACK
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   access       : MMAP_INTERLEAVED
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   format       : S16_LE
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   subformat    : STD
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   channels     : 2
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   rate         : 48000
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   exact rate   : 48000 (48000/1)
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   msbits       : 16
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   buffer_size  : 3840
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_size  : 480
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_time  : 10000
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   tstamp_mode  : ENABLE
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_step  : 1
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   avail_min    : 480
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_event : 0
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   start_threshold  : -1
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   stop_threshold   : 8646911284551352320
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   silence_threshold: 0
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   silence_size : 0
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   boundary     : 8646911284551352320
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   appl_ptr     : 216596
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   hw_ptr       : 212640
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c: snd_pcm_delay() returned a value that is exceptionally large: 2305843009213863376 bytes (882 ms).
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c: snd_pcm_dump():
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c: Hooks PCM
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c: Its setup is:
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   stream       : PLAYBACK
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   access       : MMAP_INTERLEAVED
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   format       : S16_LE
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   subformat    : STD
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   channels     : 2
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   rate         : 48000
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   exact rate   : 48000 (48000/1)
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   msbits       : 16
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   buffer_size  : 3840
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_size  : 480
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_time  : 10000
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   tstamp_mode  : ENABLE
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_step  : 1
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   avail_min    : 480
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_event : 0
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   start_threshold  : -1
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   stop_threshold   : 8646911284551352320
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   silence_threshold: 0
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   silence_size : 0
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   boundary     : 8646911284551352320
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c: Slave: Hardware PCM card 1 'HDA ATI HDMI' device 3 subdevice 0
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c: Its setup is:
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   stream       : PLAYBACK
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   access       : MMAP_INTERLEAVED
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   format       : S16_LE
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   subformat    : STD
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   channels     : 2
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   rate         : 48000
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   exact rate   : 48000 (48000/1)
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   msbits       : 16
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   buffer_size  : 3840
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_size  : 480
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_time  : 10000
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   tstamp_mode  : ENABLE
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_step  : 1
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   avail_min    : 480
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   period_event : 0
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   start_threshold  : -1
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   stop_threshold   : 8646911284551352320
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   silence_threshold: 0
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   silence_size : 0
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   boundary     : 8646911284551352320
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   appl_ptr     : 254996
May 29 17:43:53 hp-dv5 pulseaudio[19495]: alsa-util.c:   hw_ptr       : 212640

```

should this really be reported, or am I worrying too much?
Audio works, despite messages.

these reports were printed even before 1.0.20

---

### Post by yelo3 on 2009-05-29
I also have this problem, please tell me the bug link you filed

---

### Post by taavikko on 2009-05-29
> **yelo3 said:**
> I also have this problem, please tell me the bug link you filed

i haven't filed one yet nor searched for existing bugs, LP is not responding at the moment (at least for me)

but will inform here when one is either filed or found.

---

