---
title: "Gutsy Gibbon won't boot times three..."
date: 2007-11-18
forum: Installation &amp; Upgrades
---

### Post by jazzcat on 2007-11-18
Howdy all,

I'm confounded by a trio of machines that run CentOS just fine, but on which Gutsy Gibbon just won't boot.

First machine is an old laptop on which I've spent too much time trying to get my rt73 wireless adapter working under Feisty Fawn.  I figured I'd try GG to see if I get any better results.  Granted, this is a 1999 laptop with 256M of RAM, so I expected some problems, but not the kind I'm getting.  Basically, the kernel never completes booting.  (I understand the 384M ram minimum, but after upgrading FF to GG I have the same problem.)  If I hit F6 and remove the "quiet splash" options and add "acpi=off", the kernel for the most part boots normally.  Then, when it gets to the line "checking if image is initramfs... it is", the machine just stops.  It's been sitting here for the past hour at this line.  Any ideas?

Second machine is a Thinkpad R40.  I had to remove the hard drive because it's a work laptop and they don't allow changing the boot order, which is HD and then CD.  So, without the HD, the CD boots up fine, but then stops and complains about a non-responsive file descriptor for fd0.  There isn't a floppy drive on this machine.  Again, after having left the machine like this for an hour, no dice.   This laptop has 1G of ram, so that isn't an issue.

Third machine is a Shuttle XPC with 1G of ram.  The CD boots up just fine, but ends up in busybox instead of the graphical environment.  I'd think that this is a video issue, but the chipset uses (under CentOS) the same video driver that my wife's Dell 1505N uses.

I know the CD is good because I used it to install a working Ubuntu VMWare session.

This is bad news, I was getting addicted to the extreme ease by which I could use the system and install new apps.  Looks like, for the time being I'll be using C5...

Thoughts?

---

