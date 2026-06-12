---
title: "Init scripts aborting or failing after upgrade to 10.04"
date: 2010-05-07
forum: Installation &amp; Upgrades
---

### Post by oblib on 2010-05-07
I did an upgrade from 9.10 to 10.04 and something broke the init scripts. When I boot, most of the startup scripts don't run (cron, anacron, courier imap, apache, lirc, smbd, for example), and 'runlevel' reports "Unknown." However, if I run 'sudo init 2' everything starts up just fine.

In an effort to fix the problem, I did a clean 10.04 install on another partition and installed all my packages. Everything seemed to be working, but I didn't check thoroughly because I thought it should. I then went ahead and compiled and installed ffmpeg, mplayer, lirc, and mythtv and added my custom init scripts and rebooted. 

It failed init again. So I figured it must be one of my init scripts. So I removed them again and rebooted. Everything started again, so I started testing one script at a time. What I discovered was that even with none of my scripts installed (so basically a virgin /etc/init.d/), every once in a while, the init process would still fail. 

On the new partition, when it failed, modules would fail to load as well, so I had no sound or video capture devices. This is not fixed by "sudo init 2". 

This does not happen on my original partition. It fails every time on the original, but I always have all of my devices.

I'm willing to admit that it's something wrong I did, but the system worked perfectly under 9.10, so something happened with 10.04 to break it. I just don't know how to debug it.

What is the easiest way to find out what's happening with the init sequence? Why would it fail to acheive runlevel 2?

BTW, it seems similar to this thread: [http://ubuntuforums.org/showthread.php?t=1471004](http://ubuntuforums.org/showthread.php?t=1471004) which is where I learned to do 'init 2' to band-aid it.

Thanks in advance.

---

### Post by picbits on 2010-05-11
Out of curiousity, when your machine doesn't boot properly, do you have this line in the syslog (/var/log/syslog) ?

```
Failed to spawn rc main process
```

---

### Post by oblib on 2010-05-11
No. that message does not show up at all.

---

### Post by blas.lopez on 2010-06-09
I have this problem too and I noticethat every time the init script fails I get this lines in the dmesg:

[    0.000000] HPET: 4 timers in total, 0 timers will be used for per-cpu timer
[    0.000000] Fast TSC calibration failed
[    0.000000] TSC: Unable to calibrate against PIT
[    0.000000] TSC: using HPET reference calibration
[    0.000000] Detected 1994.959 MHz processor.
....
[    0.514332] tty tty28: hash matches
....
[    0.849208] ATL1E 0000:09:00.0: enabling device (0000 -> 0003)
[    0.849490] ATL1E 0000:09:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    0.849689] ATL1E 0000:09:00.0: setting latency timer to 64
....
[   46.072567] ov519: Can't determine sensor slave IDs
[   46.072570] ov519: OV519 Config failed
[   46.072584] ov519: probe of 2-4.4:1.0 failed with error -16

This not solves the problem but I posted it expecting give some clues.

TIA

---

### Post by picbits on 2010-06-09
There is a possible solution where you comment out the "console output" lines in 4 of the files in the /etc/init directory.

If you have a quick search on my other posts, you'll find a link posted by someone to the solution.

---

### Post by trigggl on 2010-06-15
Why not just post the link here?

---

### Post by anantshri on 2010-06-15
> **trigggl said:**
> Why not just post the link here?

looks like picbits is refereing to this 

[https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/543506)

hope it helps.

---

### Post by picbits on 2010-06-15
> **trigggl said:**
> Why not just post the link here?

Because at the time I didn't have time when I posted that to search through my previous posts to find it :lolflag:

---

### Post by picbits on 2010-06-15
Heres some reading for you :)

[http://ubuntuforums.org/showthread.php?t=1489535](http://ubuntuforums.org/showthread.php?t=1489535)
[http://ubuntuforums.org/showthread.php?t=1471004](http://ubuntuforums.org/showthread.php?t=1471004)

---

### Post by picbits on 2010-06-18
As an update, a few days ago I commented out all of the "console output" on my revo and HP server in the /etc/init files and haven't had a failed boot since.

---

