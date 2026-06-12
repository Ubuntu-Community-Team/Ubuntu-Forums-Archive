---
title: "Pulse audio crashes after a few minutes, Memory block too large for pool"
date: 2008-08-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by dinxter on 2008-08-17
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/258811](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/258811)

Having a problem with pulseaudio crashing after a few minutes or so of a gnome session. Just checking to see if anyone recognizes this bug before i file it.

 I: module-alsa-sink.c: Starting playback.
I: sink-input.c: Created input 0 &quot;Audio Stream&quot; on alsa_output.pci_1002_4383_alsa_playback_0 with sample spec s16le 2ch 48000Hz and channel map front-left,front-right 
D: memblockq.c: memblockq requested: maxlength=144000, tlength=96000, base=4, prebuf=94080, minreq=1920
D: memblockq.c: memblockq sanitized: maxlength=144000, tlength=96000, base=4, prebuf=94080, minreq=1920 
D: memblock.c: Memory block too large for pool: 17328 > 16368 
D: memblock.c: Memory block too large for pool: 16944 > 16368 
Soft CPU time limit exhausted, terminating. 
Hard CPU time limit exhausted, terminating forcibly. 
Aborted

---

### Post by psyke83 on 2008-08-17
[http://www.pulseaudio.org/ticket/207](http://www.pulseaudio.org/ticket/207)

---

### Post by dinxter on 2008-08-17
Thanks, looks like a different bug judging from the -vv output though. The "Soft CPU time limit exhausted, terminating." etc lines seem to be pulseaudio's standard response to a fatal bug crashing the server ( caused by W: module-alsa-sink.c: Got POLLERR from ALSA" in the above ticket and possibly by the memory too large for pool problems in mine.

---

### Post by dinxter on 2008-08-17
Bug filed [here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/258811").

---

