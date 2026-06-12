---
title: "help with Firepod"
date: 2009-05-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sdeyoung on 2009-05-13
Just installed Ubuntu yesterday. I'm having a bit of trouble getting my firepod to work. This is what I get when I run jack.

 p, li { white-space: pre-wrap; }  Could not connect to JACK server as client.
 - Overall operation failed.
 - Unable to connect to server.
 Please check the messages window for more info



p, li { white-space: pre-wrap; } 
[COLOR=#999999]13:58:19.046 Startup script...[/COLOR]

[COLOR=#990099]13:58:19.048 artsshell -q terminate[/COLOR]

sh: artsshell: not found

[COLOR=#999999]13:58:19.451 Startup script terminated with exit status=32512.[/COLOR]

[COLOR=#999999]13:58:19.452 JACK is starting...[/COLOR]

[COLOR=#990099]13:58:19.453 /usr/bin/jackd -R -P70 -p128 -dfreebob -r44100 -p32 -n2 -D -O1[/COLOR]

no message buffer overruns

[COLOR=#999999]13:58:19.472 JACK was started with PID=4661.[/COLOR]

jackd 0.116.1

Copyright 2001-2005 Paul Davis and others.

jackd comes with ABSOLUTELY NO WARRANTY

This is free software, and you are welcome to redistribute it

under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.

cannot use real-time scheduling (FIFO at priority 10) [for thread -1211865408, from thread -1211865408] (1: Operation not permitted)

cannot create engine

[COLOR=#999999]13:58:19.495 JACK was stopped successfully.[/COLOR]

[COLOR=#999999]13:58:19.496 Post-shutdown script...[/COLOR]

[COLOR=#990099]13:58:19.497 killall jackd[/COLOR]

jackd: no process killed

[COLOR=#999999]13:58:19.909 Post-shutdown script terminated with exit status=256.[/COLOR]

[COLOR=#FF0000]13:58:21.634 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]


I've enabled ram1394 for my firewire port.
And the other this is that there is no file when I do this


sudo nano /etc/udev/rules.d/40-permissions.rules[COLOR=#FF0000]
[/COLOR]


This file does not exist on my Ubuntu system.

---

### Post by sdeyoung on 2009-05-13
Hmm, for some reason I can get it working now when I uncheck realtime in the jack setup menu.. but recording seems to be slugish. Do I need a realtime kernel to select this option?

---

### Post by durand on 2009-05-16
You could try ubuntu studio. It has a realtime kernel and jack support built in.

[http://ubuntustudio.org](http://ubuntustudio.org)

---

### Post by mypetjaws on 2009-05-19
What version of ubuntu are you running? I'm running 9.04 (granted it is Ubuntu Studio, but I don't think it makes a difference) and the udev rules file in jaunty is /lib/udev/rules.d/50-udev-default.rules. That is most likely where you'll add permission for your firewire interface.
Here is a link to a post where I got help getting my firepod up and running with jack and ardour, it might be helpful, it explains those issues more concisely and in depth.

[URL="http://ubuntuforums.org/showthread.php?t=1129383&highlight=1394+issues"]http://ubuntuforums.org/showthread.php?t=1129383&highlight=1394+issues
[/URL]

---

### Post by kayosiii on 2009-07-07
Try doing a search on the multimedia production forum - on how to set up jack properly - these questions have been answered many times.

Basically if you want to run jack in realtime mode (and you almost certainly do) you need to allow your audio programs to do something a little bit insecure. You can either use the UbuntuStudio-control tool (you can install it even if you are not using ubuntu studio). Or you can manually edit /etc/security/limits.conf. (search for that file name on these forums and you will find out what to add).

---

