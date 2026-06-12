---
title: "want 'another one' just like 'this one' -- packages that is"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2010-03-01
Folks,
    Now that I have installed and patched my distro then found and installed all of my favorite packages, what can I do so that I might make another system just like the one I just made -- maybe with slightly different hardware?

    My thinking involves install the distro on each machine and complete the initial update cycle -- that sorts out the hardware differences for the most part. Now I want to grab my handy pile of preferred packages and auto-magically install all of them onto the raw distro.

    I tried using Synaptic to "Generate Package Download Script".  All I get is an empty file following the sh-bang line. There must be some way to do this.

~~~ 8d;-D

---

### Post by wkulecz on 2010-03-01
I've simply "cloned" the desired box to a second drive with Rsync.  Edited /etc/fstab and /boot/grub/menu.lst to account for the drive mapping differences and never had any real problems after moving the clone to the new machine.  The hardware detection is now good enough that everything pretty much fixes itself after a second rebood if you get dropped into busybox initially. Changing video card class/brand seems to be the biggest hassle, that and wireless internet.

This is way better than the situation with windows.  Until they switched to grub2, I'd say Ubuntu was clearly moving in the right direction, with windows going the opposite, making it effectively impossible to clone a system to be ready for a dead motherboard.  Grub2 throws up a new set of obsticals for zero user benefit that I can see.

--wally.

Edit.  I've cloned, 9.10 but I put it into a new machine that was already using grub.  I don't know how to fix boot issues with grub2 and what docs I've found make me think the whole thing is overly complicated to no net user benefit.  Maybe some day it'll do something beneficial, but so far all I see is pain no gain.

---

### Post by julianb on 2010-03-01
Remastersys is a highly useful program for creating "another one" just like "this one". It does not suffer from the same problems as the "rsync" cloning method.

---

