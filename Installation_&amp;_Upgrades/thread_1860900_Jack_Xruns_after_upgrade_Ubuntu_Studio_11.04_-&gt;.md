---
title: "Jack Xruns after upgrade Ubuntu Studio 11.04 -&gt; 11.10"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by JBeardie on 2011-10-15
Hi!

Something has happened to QJackctl after upgrade. Previously with 11.04 I had only few Xruns in and hour, but now I seem to get hundreds in just couple of minutes. It doesn't matter which applications I am running. Xruns are coming massively even if i have only Jack running. Is someone else having similar problems or a solution for this?

Jack Messages:
 p, li { white-space: pre-wrap; }  [COLOR=#999999]09:28:04.347 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]09:28:04.628 Statistics reset.[/COLOR]
 [COLOR=#cccc99]09:28:04.660 ALSA connection change.[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 [COLOR=#66cc99]09:28:04.739 ALSA connection graph change.[/COLOR]
 [COLOR=#999999]09:28:24.845 Startup script...[/COLOR]
 [COLOR=#990099]09:28:24.846 artsshell -q terminate[/COLOR]
 Cannot connect to server socket err = No such file or directory
 Cannot connect to server socket
 jack server is not running or cannot be started
 sh: artsshell: not found
 [COLOR=#999999]09:28:25.249 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]09:28:25.250 JACK is starting...[/COLOR]
 [COLOR=#990099]09:28:25.251 /usr/bin/jackd -S -P10 -p128 -t5000 -dalsa -r48000 -p128 -n2 -S -D -Chw:1 -Phw:1,0[/COLOR]
 [COLOR=#999999]09:28:25.301 JACK was started with PID=2751.[/COLOR]
 no message buffer overruns
 no message buffer overruns
 jackdmp 1.9.7
 Copyright 2001-2005 Paul Davis and others.
 Copyright 2004-2011 Grame.
 jackdmp comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK server starting in realtime mode with priority 10
 control device hw:1
 control device hw:1
 audio_reservation_init
 Acquire audio card Audio1
 creating alsa driver ... hw:1,0|hw:1|128|2|48000|0|0|nomon|swmeter|-|16bit
 control device hw:1
 configuring for 48000Hz, period = 128 frames (2.7 ms), buffer = 2 periods
 ALSA: final selected sample format for capture: 24bit little-endian
 ALSA: use 2 periods for capture
 ALSA: final selected sample format for playback: 24bit little-endian
 ALSA: use 2 periods for playback
 [COLOR=#9999cc]09:28:27.369 JACK connection change.[/COLOR]
 [COLOR=#999933]09:28:27.371 Server configuration saved to "/home/jbeardie/.jackdrc".[/COLOR]
 [COLOR=#999999]09:28:27.373 Statistics reset.[/COLOR]
 [COLOR=#999999]09:28:27.397 Client activated.[/COLOR]
 [COLOR=#cc9966]09:28:27.420 JACK connection graph change.[/COLOR]
 [COLOR=#cc66cc]09:28:27.478 XRUN callback (1).[/COLOR]
 [COLOR=#cc66cc]09:28:38.559 XRUN callback (2).[/COLOR]
 [COLOR=#cc66cc]09:28:41.058 XRUN callback (3).[/COLOR]
...

---

### Post by JBeardie on 2011-10-21
Status update.

I managed to solve this problem by using classic desktop. It seems that ubuntu's new desktop is too much for my old HW: Intel® Pentium(R) 4 CPU 2.80GHz

-JB

---

