---
title: "Jack won't start under Ubuntu 12.04"
date: 2012-05-11
forum: Installation &amp; Upgrades
---

### Post by cx1964 on 2012-05-11
Since Ubuntu 10.04 I use Jack with my Midisports2x2 midi adapter.
In Ubuntu 11.10 I could start jack.

Two weeks ago I upgraded my Ubuntu from 11.10 to 12.04 64bits
I use a Sony vaio laptop vpcF1.
Today I found out I cound not start jack anymore.
I saw several Youtube instructions on howto setup jack, but it won't help.

I hjave jackd and jackd2 installed.

QJackctl gives following messages:

20:37:56.309 Patchbay deactivated.
20:37:56.460 Statistics reset.
20:37:56.480 ALSA connection change.
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
20:37:56.494 ALSA connection graph change.
20:38:10.560 Startup script...
20:38:10.560 artsshell -q terminate
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
sh: 1: artsshell: not found
20:38:11.226 Startup script terminated with exit status=32512.
20:38:11.226 JACK is starting...
20:38:11.227 /usr/bin/jackd -t2000 -dalsa -r44100 -p128 -n3 -Xseq -D -Chw:2 -Phw:2
20:38:11.247 JACK was started with PID=3596.
20:38:11.452 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
20:38:11.458 JACK is stopping...
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started
20:38:11.587 JACK was stopped successfully.
20:38:11.588 Post-shutdown script...
20:38:11.588 killall jackd
20:38:11.589 JACK has crashed.
jackd: no process found
20:38:12.022 Post-shutdown script terminated with exit status=256.


How can Help me?

Claude

---

### Post by cx1964 on 2012-05-18
After some experiments with QJackctl settings I was able tot start Jack finally.

I used following aettings:
Server path:  /usr/bin/jackd
Driver: alsa
Realtime: check on
Verbose messages: check on
Remaining check options check off
Midi Driver: seq
Start Delay (secs) 2
Priority: 1
Frames/Periode: 128
Sample Rate: 44100
Periodes/Buffer: 2
Port Maximum: 512
Timeout (msec): 500
Interface hw:0
Dither: none
Audio: Duplex
Remaing settings: default value

My Latency is 5.8 msec

After this setting these settings, I am able to start Jack.
So, problem solved

---

### Post by Vereinfachen on 2012-05-18
then mark your thread solved ;) :guitar:

---

### Post by Stuz719 on 2012-05-21
I need to try this.  I'm unable to get din to start jack under 12.04 which is particularly annoying as to get it installed on my A3850 desktop with video drivers I had to install 11.04 and then upgrade through 11.10 to 12.04.

Hope this works!

---

