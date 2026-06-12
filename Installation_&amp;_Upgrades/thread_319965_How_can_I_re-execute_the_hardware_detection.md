---
title: "How can I re-execute the hardware detection?"
date: 2006-12-16
forum: Installation &amp; Upgrades
---

### Post by DRGuy on 2006-12-16
Hello,

I had a Dell laptop (Inspiron 3800) with Ubuntu installed.  It overheated (I think) and died.  I had it modestly configured for my use, with some web pages and some software source code that I'd been working on.  I have another Dell laptop, slightly newer and different (an Inspiron 4000).  I tried to just put the hard disk from the old machine into it, and it comes close to working (as far as I've been able to test so far), but the video isn't quite right (I may discover other issues after I resolve that - if I can).  I can see that the system boots up, and I can enter my login/passwrd and navigate with the mouse, but there are some vertical bands of disrupted video.  I assume if I had the proper video driver that would fix the problem.

When I installed Ubuntu on the original machine, it just installed and worked like a charm.  So I didn't have to bother with any video configuration.  I further assume (and may have tried at the time, but I don't recall for sure right now) that if I wanted to reformat/reload onto the newer machine it would come out working as well.  But, I was hoping that maybe if I could somehow rerun just the hardware detection, and get it to set up the proper drivers for the newer machine, I wouldn't have to go through all the efforts involved in backing up my web pages and source code, reloading, reinstalling all the additional packages (the software development stuff, Apache2, GTK+ development stuff and remembering whatever other configuration I had done).

I could probably do some things manually, such as boot from the CD, do an lsmod to see what modules are installed, and then boot from the hard drive and try to rmmod/insmod (or perhaps modprobe) to get what is needed.  It may work well enough that I could accomplish that at least for the video issue without too much difficulty (assuming it can even be done that way), but there may be other incompatabilities (network problems or who knows what).  So I was hoping that doing whatever the install process does can be accomplished on an existing system.

Perhaps another way to approach it might be to just use the CD to install over what is there, if it could be done without reformatting, and leave my home directory and other installed packages in place?

If the most robust way would be to make my backups, and start over from scratch, I can do that.  But if there is a more expedient approach, I'd appreciate the advice.

Thanks,
--
DRGuy

---

### Post by taurus on 2006-12-16
Boot into recovery mode from GRUB menu ant reconfigure your X again with

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by DRGuy on 2006-12-16
Thanks, tarus, for the almost instantaneous response!  Amazing.  If there turn out to be other issues (such as not recognizing the built-in ethernet port, where I had a PCMCIA card ethernet port for the older machine), how could I know the appropriate commands to resolve such issues?

I assume the '-phigh' argument means 'do this at a high priority' (?), so I'd just need to know the appropriate package name(s) to reconfigure.   Where might one determine such information?  I assume the man page for dpkg-reconfigure wouldn't spell out such detailed info, and that I should somehow know package names.

Is there a more general argument for dpkg-reconfigure that would redo all the hardware detection?  Or perhaps a different command to run to do that?

I guess it also occurs to me that if the dpkg-reconfigure command requires the network to access a proper driver or something, I might have a problem doing it if the existing network driver isn't right.

Am I overthinking this?

Thanks again,
--
DRGuy

---

### Post by taurus on 2006-12-16
You need to be a little more specific what PCMCIA card do you have!

Your computer doesn't have to be connected to the network to reconfigure X!!!  You can either go through the list of options if you want with 

```
dpkg-reconfigure xserver-xorg
```

---

### Post by DRGuy on 2006-12-16
OK - the dpkg-reconfigure command (the original -phigh version) has done the trick!  My display is now proper, and the networking works (without having done anything special for it).  I can access my local web pages, as well as the internet.  As far as I can tell now, everything is working.  I may find out more as I use it, of course.

Thank you taurus, for the essentially instant resolution to my problem!  Just one more reason why Linux is amazing (it isn't the mirrors ;-)

--
DRGuy

---

### Post by taurus on 2006-12-16
Try to reboot to make sure everything works the way it's supposed to...

---

### Post by DRGuy on 2006-12-16
Yes, I have rebooted - all is well.  I also had 10 "updates" (according to the little icon).  I accepted them, they installed, and it wanted to reboot again, so I did.  Everything seems to be working properly.

Thanks again,
--
DRGuy

---

### Post by taurus on 2006-12-16
Glad to hear everything is back to normal again.  Happy computing.  ;)

---

### Post by biocyberman on 2007-12-06
Hi!
I am having problems with my DVD drive, What similar command can I use to reconfigure it?

---

