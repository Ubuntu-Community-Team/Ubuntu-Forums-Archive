---
title: "HDD Crashed, New HDD, Switching To Linux - Won't Install"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by TruthElixirX on 2007-01-09
I recently had a Windows XP computer, it crashed, couldn't find recovery CDs, blah blah blah; decided to go with Ubuntu.

I installed the new hard drive (250 gigs if it matters), put in the install CD, let it load up, format the drive, enter time zone, enter username, etc.

It finishes installing and asks me if I want to restart now or continue using the live CD, I hit restart now, it starts the shut down process and has a long list of stuff. I then hit enter after it has auto ejected the CD. 

I turn the computer back on, the HP splash screen shows up, goes off, then it says

"Please reinsert boot disk and hit a key or restart."

I have no idea what else to do. I did check the integrity of the CD and it was fine...

---

### Post by meng on 2007-01-09
Try using the Live CD to install/reinstall grub, as described here:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
(yes your problem is different, but if you're lucky the solution is the same).

Also (well first) check that your hard drive is listed in the BIOS as part of the boot sequence.

---

### Post by TruthElixirX on 2007-01-09
Okay, I turned it back on, (with the CD in).

Click "Install or Run Ubuntu". Unpacked everything, took me to the desktop. I followed the instructions on that page, restarted, turned it back on, same error as before.

Turned it on, disk in, again, reinstalled completely (reformatted and all), then tried running those instructions before restarting. I get this at step #6:
[quote=terminal]
grub> setup (hd0,3)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,3)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,3) /boot/grub/stage2 p /boot/grub/menu
.lst "... failed

Error 22: No such partition

[/quote]

I'm currently posting while running the live CD, I'm not sure if I should restart now or not...

EDIT::

Wait.. I think I did something wrong. One second..

EDIT2:: Still no luck.

---

### Post by TruthElixirX on 2007-01-10
Bump.

Problem is still the same as before I followed meng's instructions.

Could it possibly be another hardware problem in addition to the crashed HDD?

---

### Post by dcstar on 2007-01-11
> **TruthElixirX said:**
> Bump.

Problem is still the same as before I followed meng's instructions.

Could it possibly be another hardware problem in addition to the crashed HDD?

Possible, but if you have the time you may want to try installing with manual partition setting and just use 20 GB for the Ubuntu install.

You can subsequently format the remainder of the HD and use it after you get your base install going.

---

### Post by TruthElixirX on 2007-01-11
> **dcstar said:**
> Possible, but if you have the time you may want to try installing with manual partition setting and just use 20 GB for the Ubuntu install.

You can subsequently format the remainder of the HD and use it after you get your base install going.

I am new to this, and I don't mean to sound arrogant, but how is that any different from what I have been doing? Or does the size of the partition affect things?

---

