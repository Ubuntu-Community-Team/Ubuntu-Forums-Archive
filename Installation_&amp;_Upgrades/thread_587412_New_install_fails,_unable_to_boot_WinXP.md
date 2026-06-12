---
title: "New install fails, unable to boot WinXP"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by krasnit on 2007-10-22
I tried installing 7.10 fresh with new partitions following the on screen instructions, but the install failed twice.  The machine reboots in the middle of the Ubuntu files installation, just past half way.  Now when I try to install Ubuntu, I am no longer asked to partition past the Windows partition but wants to install on the whole 500gb drive.  When I go to manual, I have no idea how to set up the boot partition which is what I am being prompted for.  The Windows XP partition is still there it seems, the first 400gb, but I cannot boot on it.  I have tried grub, root (hd0,0) from the CD but the message I get is that there is no such drive.  At this point all I want is to get back to the Windows partition and save installing Ubuntu for another day.  
I suspect my ECS motherboard is not compatible with Linux.

---

### Post by dagrump on 2007-10-22
You need a windows install disk, get to the recovery console ( watch the prompts) then you into enter fixmbr, that should rewrite the master boot record. You should be able to boot windows then.

---

### Post by krasnit on 2007-10-22
Tried fxmbr, still will not boot to anything.  Will try again

---

### Post by dagrump on 2007-10-22
It's fixmbr not fxmbr. If that doesn't work I'm at a loss as I've used that several times when people didn't feel they wanted to learn to use Ubuntu.

---

### Post by krasnit on 2007-10-22
Sorry yes, fixmbr.  I tried about 10 times, no luck.  It looks like my harddrive has been rendered useless.  My only alternative is to reinstall Windows XP as a repair, and hope that works, but it may not do anything to the boot sector unless it is repartitioned
.

---

### Post by dagrump on 2007-10-22
I would hold off for a few minutes, there are lots of folks that are much smarter then I that might give you a simple fix, that i'm missing. But that could end up being your best option in the end.
Good luck I have done a repair install & managed to back up my stuff, then do a clean install.
Of course had to deal w/ a lady I had a hard time making understand, it was just a reinstall on the same machine.

---

