---
title: "How to put grub on a floppy?"
date: 2008-04-20
forum: Installation &amp; Upgrades
---

### Post by fbaerkir on 2008-04-20
I've been trying all sorts of ways to install Ubuntu for a dual-boot setup with Vista. The straightforward methods won't work because I run Vista on a RAID 5.
So here's what I'm trying now: Putting Ubuntu (7.1, 64-bit) on a separate HD. I've downloaded the alternate install CD, and can install Ubuntu onto the drive just fine. But the bootloader gets lost in the process; it goes to one individual drive in the RAID, and then I have to repair the Windows boot record, which means I can't boot Ubuntu.
I'm new to all this, but it looks to me like the simplest fix would be to load a floppy with grub. Then, since my floppy is first in my boot order, it would boot to Ubuntu with the floppy in, or to Vista with no floppy. Of course, I am new to this so maybe I'm overlooking something.
If that will work, how can I get grub onto a floppy to begin with? I see several nice tutorials on how to copy it to a floppy from Ubuntu. But that requires the OS to already be up and running. Is there somewhere I can go to get a generic copy of grub and install it to a floppy, then change its locations (I wrote down the disk assignments during install)?
It seems to me that some people get options on where to install grub. I didn't get to that (again, alternate install CD for 7.1, amd64 version). Is there a set of commands I need to follow to get that option?
I've been trying to do this for a couple months now, and it feels like I'm getting really close to Linuxy goodness. Any help would be vastly appreciated!

---

### Post by Pumalite on 2008-04-20
In step 8, press 'Advanced Tab' and change (hd0) for /dev/fd0. (I havent tried it, but it should be feasible)(Live CD)

---

### Post by fbaerkir on 2008-04-21
Thanks for the advice. I moved to the regular install CD and found that option. It looked like everything went fine. But then when I tried to boot, I got a message about a grub HD error.
Does this mean grub is counting my disks differently than the install CD did? Is it now a matter of tweaking the grub settings?

---

### Post by Pumalite on 2008-04-21
Post the exact error message.

---

### Post by fbaerkir on 2008-04-21
The exact error message is simply "GRUB Hard Disk Error." The screen just hangs early in the boot process. I'm going to play with editing GRUB from the live CD and see if that goes anywhere...

---

### Post by fbaerkir on 2008-04-24
OK, that didn't work either. I followed instructions from another thread on this forum for editing the GRUB boot record, with no results.
This is getting really frustrating. I can't seem to get Ubuntu installed on that one drive without mucking up my Windows boot record. I think I saw an option to use LILO with Ubuntu on the alternate install CD and I guess I'll try that as a last shot...

---

### Post by fbaerkir on 2008-04-26
I could swear I once saw an option to use LILO as the boot loader. Now that I'm trying to go back and find it, I can't though. Anyone know where it is?

---

