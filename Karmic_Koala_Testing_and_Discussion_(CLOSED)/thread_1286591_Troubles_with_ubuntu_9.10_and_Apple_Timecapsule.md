---
title: "Troubles with ubuntu 9.10 and Apple Timecapsule"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Dareus on 2009-10-09
I started using an Apple Timecapsule about one year ago.

I was able to use it painless until I upgraded my ubuntu 9.04 to 9.10 beta, I knew it was a beta but you know...

I always used [this thread]("http://ubuntuforums.org/showthread.php?t=288534") to configure my share.

I've no problems using the Timecapsule as a router, the problem is about using it as an external storage!

This is what I'm experiencing:
- Mount errors on boot (trying to mount it when there's no network);
- Unreadable files.
- Umount errors on shutdown (even if I've changed the order of umount scripts in shutdown and reboot RCs)

This second point needs more explanations.
When in the mount point (/media/timecapsule) and ls the result is:
```
dario@dario-laptop:/media/timecapsule$ ls -l
totale 0
```
the strange fact is that I know that files are there and i can even navigate through them if I remember the path
```
dario@dario-laptop:/media/timecapsule$ cd Musica
dario@dario-laptop:/media/timecapsule/Musica$ pwd
/media/timecapsule/Musica
```
Not even nautilus can show me my files (but explorer in windows can).

With this problems is almost impossible to use my Timecapsule and I don't know what to do. I'd like to use zeroconf to easily and painless configure my share, but I'm not able in getting hints.

Thanks for your time, and [Pliz pliz vizit auar cauntri :P](http://www.youtube.com/watch?v=w0P-gl4zlvU&feature=related)

---

