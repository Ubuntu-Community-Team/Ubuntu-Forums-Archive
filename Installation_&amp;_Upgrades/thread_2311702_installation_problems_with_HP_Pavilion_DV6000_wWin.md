---
title: "installation problems with HP Pavilion DV6000 w/Windows XP"
date: 2016-01-29
forum: Installation &amp; Upgrades
---

### Post by CBJFanGirl on 2016-01-29
I'm have done a dual boot Windows XP/Ubuntu installation (quite a few years back though) but this one gave me problems so far this morning.

I have come into possession of an HP Pavilion DV6000 laptop with Windows XP installed, and would like to install Ubuntu 14.04 LTS alongside it (for now).  I would like the computer safe enough for writing and internet research/blogging (basically a laptop I can carry around with me that in the case it gets stolen, my life on it isn't stolen either, and that is somewhat more secure than ).  I've attempted it this morning, but in the midst of the installation the DVD drive popped out.  The partition for it was already created during the installation.

A couple questions regarding my next attempt:

1) Has anyone tried to install on the HP DV6000 via the USB drive? I think the DVD drive has its quirks as it seems to randomly want to pop open even in Windows XP, so installation via DVD may be problematic.  Hitting [esc] at initial power-up only gave me the options of DVD drive & hard drive for boot-ups.  Hitting [f10] didn't yield much more than that as options.

2) Since the partition has already been created in this first attempt, how can I go back and try installing Ubuntu on that already-created partition?

3) Is installing Ubuntu 14.04 LTS on this laptop a waste of time (with 2gb ram)? Should I try Lubuntu or Xubuntu instead?

I should say I'm a bit more tech savvy than most of my ilk (liberal arts degree) but probably not as much as y'all, so keep it somewhat easy to understand :)  

Thanks.

---

### Post by ajgreeny on 2016-01-29
You probably need to have a bootable USB attached to the machine for it to show as a boot device when you hit Esc, or whichever button you use to show the boot devices.

You will possibly get Ubuntu to run but it may be very slow with old hardware so I would personally suggest you try Xubuntu, and if that still seems slow try Lubuntu.

Both are very good OSs with DEs that need lower resources than Ubuntu.

---

### Post by ubfan1 on 2016-01-29
USB install should work fine on that machine, no issues at all.  Definitely try the lower resource distros, unity on that machine will be unacceptable.  You can use the "something else" to select existing partitions.  You might have issues with the Nvidia graphics (?) so nomodeset might be needed initially until you get the proprietary drivers.  Wifi is probably Broadcom based, so do NOT select any updates in the install, wait until you get the right drivers installed (see the many questions/threads on this issue).  I had an older V3000 which was pretty solid, but tended to overhead on graphics intensive usage.

---

