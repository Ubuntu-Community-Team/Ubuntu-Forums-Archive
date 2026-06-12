---
title: "Package authentication failure in upgrade manager"
date: 2007-08-21
forum: Installation &amp; Upgrades
---

### Post by odonnell on 2007-08-21
I have a pretty standard Feisty Fawn installation. I was away for a week, so I'm not sure when this problem arose.

When I booted this morning (Tuesday 21 August 2007) after a week of absence, I found a notification of updates. I invoked update manager. It presented me with some backports, all of which succeeded, and some other updates, all of which produced a "NOT AUTHENTICATED" warning. The packages were rsync, libjasper* (1 package) and libvorbis* (3 packages). I have cancelled the update for now, but the "Changes" report classifies them as "SECURITY UPDATE"s, so I take some risk either way.

I have another host, with a Feisty Fawn ubuntu-server installation, and no X. On that host, I ran "apt-get dist-upgrade" from the command line, and the same packages were updated.

I *suspect* that there is some error in loading signatures, and I *hope* that this will be fixed by the archive soon. I *suspect* that the signature check is performed by the update manager, and not by apt-get. But there are a number of other possibilities, including different signatures stored on my two hosts, and a very small chance that there is an attack using a bogus version of rsync, libjasper* and/or libvorbis*.

If anyone has an explanation, I will be very grateful to read it.

Thanks,

Mike O'Donnell
[http://people.cs.uchicago.edu/~odonnell/](http://people.cs.uchicago.edu/~odonnell/)

---

### Post by odonnell on 2007-08-22
My package authentication problem was resolved somehow overnight. Today (Wednesday 22 August) I invoked the update manager, it presented the same 5 packages rsync, libjasper*, and libvorbis* as "other updates," and performed the updates without complaining about authentication.

I won't pursue the issue any more, but it *may* be a clue to some intermittent problem in the synchronization of updates and signatures, or (unlikely but conceivable) an attack.

Mike O'Donnell
[http://people.cs.uchicago.edu/~odonnell/](http://people.cs.uchicago.edu/~odonnell/)

---

