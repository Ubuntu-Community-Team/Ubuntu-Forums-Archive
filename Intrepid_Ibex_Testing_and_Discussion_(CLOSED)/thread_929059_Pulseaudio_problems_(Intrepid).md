---
title: "Pulseaudio problems (Intrepid)"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by 68pontiac on 2008-09-24
Hello all. I'm still pretty new with Linux and probably shouldn't be using an alpha release, but the newest kernel fixes the networking issue I've been having. But with the newest Intrepid Alpha 6 I don't have any sound. I think I've traced it to a Pulseaudio problem. I've uninstalled and reinstalled it with Synaptic and I get this message when I run "pulseaudio" from command line.

```
W: ltdl-bind-now.c: failed to find original dlopen loader.
E: pid.c: Daemon already running.
W: main.c setrlimit (RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c setrlimit (RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
E: socked-server.c: bind(): Address already in use
E: module.c: Failed to load module "module-esound-protocol-unix" (argument: ""): initilization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
E: pid.c: PID file '/tmp/pulse-christopher/pid' not mine!
```

I'd love it if somebody could help sort out my sound/pulseaudio issues. Keep it simple if you could, I'm still getting this whole Linux thing down. THANK YOU!

---

### Post by cjm5229 on 2008-09-24
Try This. [http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)
Check the Intrepid Testing Forums, if you have more questions.

---

### Post by 68pontiac on 2008-09-24
I've been following that thread for several days. The original post there didn't seem to help much, but I haven't repeated those instructions since I uninstalled and reinstalled. Will it make a difference? I'm not at home to try now.

---

