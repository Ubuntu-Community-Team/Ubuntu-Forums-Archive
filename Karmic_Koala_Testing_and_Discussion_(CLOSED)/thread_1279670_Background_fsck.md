---
title: "Background fsck"
date: 2009-10-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bobince on 2009-10-01
Is this new in Karmic? I've never seen it happen before.

Ubuntu seems to be delaying the fscking of my main documents partition (/dev/sda3). Instead of slowing down the boot progress, it goes on to gdm and lets me log in, whilst checking it in the background.

I guess this is an improvement, but there really needs to be some kind of feedback that this is happening. I almost had a fit when I tried to open the mount point where all my work is and saw nothing inside!

(Although really I don't want startup-fsck and usually remember to disable it. On modern large drives it takes far too long to check and 30 boots is much too often for a machine that boots a couple of times a day. I like the idea of moving the full fsck scan to a shutdown option.)

---

### Post by moviemaniac on 2009-10-01
That's interesting. My drive got checked while booting this morning and it was done the "usual" way - i.e. at the boot process before loading GDM.

---

### Post by ljrmorgan on 2009-10-01
> **moviemaniac said:**
> That's interesting. My drive got checked while booting this morning and it was done the "usual" way - i.e. at the boot process before loading GDM.

As did mine. As I was sitting there watching it I couldn't help but think it slows everything down a little bit, having it going on in the background would be great, though is that even possible?

---

### Post by bobince on 2009-10-01
> **ljrmorgan said:**
> is that even possible?

I don't know, but it happened!

```
    fsck from util-linux-ng 2.16
    fsck from util-linux-ng 2.16
    /dev/sda1: clean, 132823/655360 files, 1095861/2620595 blocks
    * Setting up preliminary keymap... [OK]
    * Setting up console font and keymap... [OL]
    * Loading spufreq kernal modules...
    * CPUFreq Utilities: setting ondemand CPUFreq governor
    * CPU0...
    * CPU1...
    * CPU2...
    * CPU3... [OK]
    * Running DKMS auto installation service for kernel 2.6.31-11-generic
    /dev/sda3 has been mounted 26 times without being checked, check forced
    * vboxdrv (3.0.6)... [OK]
    * vboxnetadp (3.0.6)... [OK]
    * vboxnetflt (3.0.6)... [OK]
    * Starting Kernel Oops catching service kerneloops [OK]
        [...many messages later...]
    Ubuntu karmic (development branch) computer tty1

    computer login: /dev/sda3: 243384/59088896 files (1.3% non-contiguous), 74516263/26326190 blocks
```That is, fsck was clearly still running whilst tty1 was at &#8216;login:&#8217; stage (and 7 had started gdm then a user X session).

The machine is up-to-date as of now, and runs upstart, gdm and xsplash (but not usplash).

---

### Post by danwood76 on 2009-10-01
I think its supposed to run in the background and let all other processes load and once complete hit the login.
So really it shouldnt have still been running once you were logged in.

At least I think that was one of the initial plans.

---

### Post by forcecore on 2009-10-02
that manual fsck is still annoyng even on beta

---

### Post by a6jarvi on 2009-10-05
This happened on my machine, too.

I was just testing the GRUB2 chainload, and after I rebooted there was no desktop wallpaper and 1 cpu core was on full load. Well, that is somewhat normal on a beta install, I thought, but my heart relly skipped a few beats when I tried to open my main documents folder - nothing in there! I tried mounting the partition manually without success because the folder was "already in use." Only then it came to me that maybe that suspiciously fast fsck was still running...

IMO this is a great feature, but there definitely should be some kind of information popup about this once logged in.

---

### Post by whoop on 2009-10-05
fsck totally sucks for me at the moment. It just hangs when there is a check forced at boot time... Nothing happens, no disk activity. When a do a hard reset all drives are cleanly mounted which led me to believe nothing is being checked at all.

---

### Post by Forlong on 2009-10-05
Background fsck only works on partitions that are not used for / and /home, of course.
Logically, fsck'ed partitions can't be mounted, thus partitions that are essential still have to be checked *before* booting up.

---

### Post by jocko on 2009-10-10
Still happens here too. I filed this [bug-report]("https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/447816") before I found this thread. Check it out and mark it as "affects me too" and/or post some comments.

---

