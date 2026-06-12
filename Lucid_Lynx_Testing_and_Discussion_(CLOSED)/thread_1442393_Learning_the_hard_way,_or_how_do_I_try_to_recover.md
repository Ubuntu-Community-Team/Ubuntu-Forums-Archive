---
title: "Learning the hard way, or how do I try to recover?"
date: 2010-03-29
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Arla on 2010-03-29
I started an update today, ran into some issue (synaptic package manager closed on me reporting it couldn't write to a log), next boot I got a message about the / file system being corrupt, running check on it from gparted (maybe the wrong thing to have done) fixed a bunch of inodes issues, now I can sort of boot, but get a message about ubuntu running in low-graphics mode, and can't seem to do anything (can't move the mouse, can't click anything) I've tried running prior kernels, nothing seems to work.

Any way I can get to a terminal? Alternatively, can I boot a live CD and try to repair the / partition, if so how would I even go about doing that? I've only JUST got done installing all my software, I can always do it again, just wondering if it's possible to avoid re-doing it.

---

### Post by QLee on 2010-03-30
[QUOTE=Arla]I started an update today, ran into some issue (synaptic package manager closed on me reporting it couldn't write to a log), next boot I got a message about the / file system being corrupt, running check on it from gparted (maybe the wrong thing to have done) fixed a bunch of inodes issues, now I can sort of boot, but get a message about ubuntu running in low-graphics mode, and can't seem to do anything (can't move the mouse, can't click anything) I've tried running prior kernels, nothing seems to work.

Any way I can get to a terminal? Alternatively, can I boot a live CD and try to repair the / partition, if so how would I even go about doing that? I've only JUST got done installing all my software, I can always do it again, just wondering if it's possible to avoid re-doing it.[/QUOTE]

There is this sticky thread about "partial upgrades' which may have something you could use to work out what state your system is in and what you need to do to fix it.
[http://ubuntuforums.org/showthread.php?t=1343434](http://ubuntuforums.org/showthread.php?t=1343434)

 It might be easier to restore from your backup and try the updrade again after determining what cause the inability of Synaptic to write a log, so it doesn't error out again. You might be able to chroot into the partition and finish the upgrade, or not. There are a couple of options to try.

---

### Post by sdowney717 on 2010-03-30
you can boot the live CD and chroot into your hard drive installation. Then you can try and fix it.
But it might be easier to just start over.

Like this here
[http://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation](http://superuser.com/questions/111152/whats-the-proper-way-to-prepare-chroot-to-recover-a-broken-linux-installation)

---

