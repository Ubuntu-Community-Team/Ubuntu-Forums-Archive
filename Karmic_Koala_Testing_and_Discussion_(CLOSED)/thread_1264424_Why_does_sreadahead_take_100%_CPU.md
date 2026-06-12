---
title: "Why does sreadahead take 100% CPU?"
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Robin Nixon on 2009-09-12
It used to be pulseaudio thrashed my system fan at 80% CPU usage, but now sreadahead beats it at 100% CPU. Is it a disk caching program or something? - if so it's strange because the hard disk light isn't flashing.

I know it goes away after a few minutes but... Surely it can't be right?

---

### Post by isecore on 2009-09-12
> **Robin Nixon said:**
> It used to be pulseaudio thrashed my system fan at 80% CPU usage, but now sreadahead beats it at 100% CPU. Is it a disk caching program or something? - if so it's strange because the hard disk light isn't flashing.

I know it goes away after a few minutes but... Surely it can't be right?

As you said, it's probably a cache. It does the same on my computer. I believe it's related to preload (not sure though) and preload fetches commonly used apps for quicker start.

Like I said, my machine does the same. Upon login sreadahead runs heavily and then after maybe 30-45 seconds it's done whatever it is supposed to do.

---

### Post by jocko on 2009-09-12
> **isecore said:**
> As you said, it's probably a cache. It does the same on my computer. I believe it's related to preload (not sure though) and preload fetches commonly used apps for quicker start.
It's not like preload. It's like readahead. It keeps a list of the files that are read at boot, and reads them into memory *before* they are needed, to speed up the boot process. After some updates that affect the boot process (like kernel, initramfs-tools etc) it profiles the boot to update the file list, and after reboot you will notice it running for a while. It does not run after every boot, but as you are using an alpha that keeps being updated you get updates that trigger a profiling on next boot pretty often. So after karmic is released, this will not happen often.

I'm not sure that it really needs to use 100% cpu, though...

---

### Post by froggyswamp on 2009-09-14
I also think (I'm sure!) this sreadahead thing is not tested enough and isn't good enough.

I'd say that Karmic is a bit slower to boot than Jaunty, yet we get the extra "bonus" of trashing the CPU for like a minute (not 10 seconds like some report).

Now about the "cache" thing - if it's caching something then why can't I hear the HDD working? - when the HDD works I always hear it, but when sreadahead works the only thing being trashed is the CPU. What's that? Somebody trying to downgrade the desktop experience covering itself by a fake noble reason?

The bug on sreadahead has been marked as "won't fix" without explaining since when is caching done by CPU "alone":
[https://bugs.launchpad.net/ubuntu/+source/sreadahead/+bug/421116](https://bugs.launchpad.net/ubuntu/+source/sreadahead/+bug/421116)

---

### Post by psyke83 on 2009-09-14
> **froggyswamp said:**
> I also think (I'm sure!) this sreadahead thing is not tested enough and isn't good enough.

I'd say that Karmic is a bit slower to boot than Jaunty, yet we get the extra "bonus" of trashing the CPU for like a minute (not 10 seconds like some report).

Now about the "cache" thing - if it's caching something then why can't I hear the HDD working? - when the HDD works I always hear it, but when sreadahead works the only thing being trashed is the CPU. What's that? Somebody trying to downgrade the desktop experience covering itself by a fake noble reason?

The bug on sreadahead has been marked as "won't fix" without explaining since when is caching done by CPU "alone":
[https://bugs.launchpad.net/ubuntu/+source/sreadahead/+bug/421116](https://bugs.launchpad.net/ubuntu/+source/sreadahead/+bug/421116)

Read Scott's actual response:

> 

This is quite normal, it takes a few minutes after the first boot to generate the lists - it's operating as a "very low priority" so shouldn't affect system performance.

If you don't let it finish, it will be slow every time you boot ;-)


He then marked the bug as Won't Fix. Only later do some users complain that sreadahead is still using excessive CPU, so if your boot is slow after 27 uninterrupted boots, it's a bug, and the bug needs to be reopened.

I suggest you try to purge the sreadahead package and re-install.

---

### Post by jpeddicord on 2009-09-14
If sreadahead is being run after *every* reboot regardless of updates, then a new bug should be filed. That bug is complaining about 100% use. It uses the CPU to profile your boot and figure out what it needs to load. As stated in the bug, it's running at a low priority (nice 19). If other applications need to use your CPU, sreadahead will be slowed down. You shouldn't notice any big performance issues.

---

### Post by isecore on 2009-09-15
FWIW I have no annoyances with sreadahead. Sure, occasionally depending on updates does it run upon login - but I barely notice it.

Also, my boot-times on Karmic are exceedingly better than under Jaunty. Calling the difference day and night would be excessive, but the boot-speed under Karmic is quite impressive compared to Jaunty. I suppose it's thanks to optimized boot-routines as well as EXT4 and various other things working in harmony.

---

### Post by jpeddicord on 2009-09-15
> **isecore said:**
> FWIW I have no annoyances with sreadahead. Sure, occasionally depending on updates does it run upon login - but I barely notice it.

Also, my boot-times on Karmic are exceedingly better than under Jaunty. Calling the difference day and night would be excessive, but the boot-speed under Karmic is quite impressive compared to Jaunty. I suppose it's thanks to optimized boot-routines as well as EXT4 and various other things working in harmony.

I agree.

Also, this isn't completely related to sreadahead, but a bunch of new boot stuff should be landing today which could provide some interesting twists (hopefully for the better).

---

### Post by dslink on 2009-09-20
this is really getting to be a big pain in the butt. More so on a laptop.

---

### Post by xebian on 2009-09-20
Isn't this what should be? At rocket launch use as much power as you have - 100% is very good.  This is over in just about 15 secs.  What else needed cpu anyway during boot?

---

### Post by hugmenot on 2009-09-20
The frequency of the regeneration of the pack file is directly related to the number of dist-upgrades you do. Every time a package with an init script is installed a dpkg hook will delete the pack file to let sreadahead profile your next boot. After all, the boot sequence might have changed, right? So, each time pulseaudio or cups or samba or anything is upgraded, the next time you boot it will reprofile. And not speed up the boot, it is in either profile mode or read ahead mode.

Solution? Just don&#8217;t upgrade every two hours. Once Karmic is out and your boot sequence is stabilized it will stop reprofiling all the time anyway.

---

### Post by keybuk on 2009-09-20
It's also really crap at sorting its lists, which is what it's doing when it's appearing on the top of the run queue ("100% CPU").  I tried to fix this a while back but borked it, someone else has just tossed a patch that probably fixes it properly.

Note that it's not preventing any other process from using the CPU, the Linux scheduler is far more clever than that.  It's just spoiling your System Monitor app.

---

### Post by dslink on 2009-09-21
it doesnt happen right at boot, it goes on about 10 or 15 mins after booted up and logged in and starting to do work.  And it cripples a system and I'm on a core2 4 gigs of ram. so its not some crappy P4.

---

### Post by MacUntu on 2009-09-28
This is fixed with sreadahead 1.0-4.

---

