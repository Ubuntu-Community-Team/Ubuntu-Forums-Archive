---
title: "jack"
date: 2005-04-28
forum: Installation &amp; Upgrades
---

### Post by jrincon87 on 2005-04-28
Hey. I wanna use ardour-gtk or audacity to edit and play sound waves and midi files. I installed the jackd and libjack 'cause the software ask me to do so. I also downloaded "qjackctl", to have a graphic view of the jack server. But the server won't start. When I execute qjackctl, it shows the following error messages: "Could not open sequencer as a client, Midi patchbay will not be available", "Could not connect to Jack Server as a client." Here is what the log file shows:

16:51:12.690 Statistics reset.
16:51:12.711 Could not open ALSA sequencer as a client. MIDI patchbay will be not available.
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No existe el fichero o el directorio
16:52:05.114 Startup script...
16:52:05.115 artsshell -q terminate
sh: artsshell: command not found
16:52:05.433 Startup script terminated with exit status=32512.
16:52:05.436 JACK is starting...
16:52:05.437 /usr/bin/jackd -R -doss -r48000 -p1024 -n2 -w16
16:52:05.464 JACK was started with PID=10228 (0x27f4).
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
loading driver ..
jack_create_thread: error 1 setting scheduler parameters after thread creation: Operation not permitted
cannot start watchdog thread
cannot load driver module oss
16:52:05.683 JACK was stopped successfully.
16:52:07.677 Could not connect to JACK server as client.

I don't have any idea on how does it works or what should I install, 'cause I used to have SuSE and I didn't have that problem.
PD: Sound Card: Sound Blaster Live 24-bits external.
Thanks for your help.

---

### Post by racter on 2005-05-11
i'm struggling with jack also, but i have discovered at least that i can run "sudo modprobe snd-seq" which takes care of the "Could not open ALSA sequencer" issue.  also, be sure to start qjackctl as root ("sudo qjackctl").  you also may need to disable the "realtime" checkbox in qjackctl under setup->parameters.

i seem to have the server running fine but jack is just not working!  xmms says "couldn't open audio" (i have xmms-jack installed).  puredata won't even open (running the command "pd" does nothing).  jack-rack says "could not create jack client: is the jackd server running?"

has anyone been able to set up hoary for music work with jack?  what did you do?

thanks,
jake

---

