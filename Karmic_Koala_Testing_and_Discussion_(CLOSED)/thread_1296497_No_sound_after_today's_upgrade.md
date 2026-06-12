---
title: "No sound after today's upgrade"
date: 2009-10-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cuby on 2009-10-20
Ok. Sound stopped after today's upgrade. I have this massages:

messages:
[SIZE="4"][SIZE="3"][SIZE="2"]Oct 20 22:36:50 newton pulseaudio[1990]: ratelimit.c: 79 events suppressed
Oct 20 22:37:02 newton pulseaudio[1990]: ratelimit.c: 115 events suppressed
Oct 20 22:42:58 newton pulseaudio[1990]: ratelimit.c: 4 events suppressed
Oct 20 22:43:03 newton pulseaudio[1990]: ratelimit.c: 6 events suppressed
Oct 20 22:43:13 newton pulseaudio[1990]: ratelimit.c: 6 events suppressed
Oct 20 22:46:41 newton pulseaudio[1990]: protocol-native.c: Failed to push data into queue
Oct 20 22:46:41 newton pulseaudio[1990]: protocol-native.c: Failed to push data into queue
Oct 20 22:46:41 newton pulseaudio[1990]: protocol-native.c: Failed to push data into queue
Oct 20 22:48:49 newton pulseaudio[1990]: protocol-native.c: Failed to push data into queue
Oct 20 22:48:49 newton pulseaudio[1990]: protocol-native.c: Failed to push data into queue
Oct 20 22:48:49 newton pulseaudio[1990]: protocol-native.c: Failed to push data into queue

syslog:
Oct 20 22:36:50 newton pulseaudio[1990]: ratelimit.c: 79 events suppressed
Oct 20 22:37:02 newton pulseaudio[1990]: ratelimit.c: 115 events suppressed
Oct 20 22:37:09 newton pulseaudio[1990]: alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
Oct 20 22:37:09 newton pulseaudio[1990]: alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_hda_intel'. Please report this issue to the ALSA developers.
Oct 20 22:37:09 newton pulseaudio[1990]: alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
Oct 20 22:42:58 newton pulseaudio[1990]: ratelimit.c: 4 events suppressed
Oct 20 22:43:03 newton pulseaudio[1990]: ratelimit.c: 6 events suppressed
Oct 20 22:43:13 newton pulseaudio[1990]: ratelimit.c: 6 events suppressed
Oct 20 22:46:41 newton pulseaudio[1990]: protocol-native.c: Failed to push data into queue
Oct 20 22:46:41 newton pulseaudio[1990]: protocol-native.c: Failed to push data into queue
Oct 20 22:46:41 newton pulseaudio[1990]: protocol-native.c: Failed to push data into queue
Oct 20 22:48:49 newton pulseaudio[1990]: protocol-native.c: Failed to push data into queue
Oct 20 22:48:49 newton pulseaudio[1990]: protocol-native.c: Failed to push data into queue
Oct 20 22:48:49 newton pulseaudio[1990]: protocol-native.c: Failed to push data into queue

I don't know their meaning.
Sound, as usually, continues to be a disgrace.

---

### Post by cuby on 2009-10-20
Problem found... Freesh instalation config setted internal audio to muted while everything else was ok. This should not happen. If something this important is muted, it should be evident everywhere.

---

