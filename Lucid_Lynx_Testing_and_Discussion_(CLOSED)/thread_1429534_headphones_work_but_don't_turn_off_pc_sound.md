---
title: "headphones work but don't turn off pc sound"
date: 2010-03-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by buzzmandt on 2010-03-14
I have also asked this question in kubuntu forums but no one has an answer for me so I'll try here

I have a brand new laptop and am loving lucid kubuntu on it.  Only real trouble i've had is with knetworkmanager losing it's setting for wireless activated leaving it giving me the unmanaged message on mouse over, easy fix... and this one.  I plug in headphones and sound comes through them great, but my pc speakers are still on and just as loud as without the headphones.  is there a fix for this?

Compaq presario cq60
Lucid lynx kubuntu 64bit, updates current

```
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
```

```
buzzmandt@my-compaq:~$ cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.21 emulation code)
Kernel: Linux my-compaq 2.6.32-16-generic #25-Ubuntu SMP Tue Mar 9 16:33:12 UTC 2010 x86_64
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA Intel at 0x94700000 irq 22

Audio devices:
0: HDA Generic (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers:
0: Conexant ID 5067
buzzmandt@my-compaq:~$ 

```

---

### Post by SecretCode on 2010-03-14
I had a similar problem in Ubuntu Karmic. The solution was editing /etc/modprobe.d/alsa-base.conf via careful reading of [this thread]("http://ubuntuforums.org/showthread.php?t=1075643") and [this one]("http://ubuntuforums.org/showthread.php?t=1043568") ... and some trial and error.

---

### Post by 6205 on 2010-03-14
> **SecretCode said:**
> I had a similar problem in Ubuntu Karmic. The solution was editing /etc/modprobe.d/alsa-base.conf via careful reading of [this thread]("http://ubuntuforums.org/showthread.php?t=1075643") and [this one]("http://ubuntuforums.org/showthread.php?t=1043568") ... and some trial and error.

rriiightt :/

---

