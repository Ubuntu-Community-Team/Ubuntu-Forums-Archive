---
title: "LIRC and 8.04.1 and Nova-T500"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by richard.e.morton on 2008-10-18
LIRC doesn't work on 8.04.1 mythbuntu with Nova-t500
Hi,

I have a new system that I ahve been building slowly. it's nearly there except for a few minor things and that I can't get the IR to work, which makes it pretty hard to use as a mediacenter.

So I have built a system around Mythbuntu 8.04 (played with linuxMCE first, but it wasn't for me, and then evaluated MythDora). It is configured to auto update, so it's now 8.04.1. The system is quadcore q6600 with Asus p5q motherboard, asus geforce 8500 512mb pcie card and most importantly an hauppauge nova-t500 pci dual tuner card with IR remote.

So I havea plain install with a few extra apps (MAME, GTK_GNUTELLA). I have tries to use the Control Centre to configure the remote but whenever I use the remote the last button it receives is repeatedly indefinitely (I only know for sure that the arrow keys work like this, the other buttons don't do much on the screens I have managed to get to).

If I start up irw to look to see what is happening it says connection refused.

I have tried to stop the daemon with sudo /usr/sbin/lircd stop
and although the app doesn't throw an error, when I try to start lirc it thinks a process is already running. I used:
/usr/sbin/lircd -n
to make it a foreground process, but it tells me lirc is running with pid .... so I remove the pid file lock in var/run/lircd.pid
sudo rm /var/run/lircd.pid
and start the process but it doesn't fix it... it starts but as soon as I start irw it bombs.

lircd-0.8.3pre1[2423]: lircd(userspace) ready
lircd-0.8.3pre1[2423]: accepted ew client on /dev/lircd
lircd-0.8.3pre1[2423]: cound not get file information for /dev/lirc
lircd-0.8.3pre1[2423]: default_init(): No such file or directory
lircd-0.8.3pre1[2423]: caught signal
Terminated.

where as the shell where I entered irw just silently and immediately returns to the shell.

any ideas?

thanks for your help in advance

Richard

---

