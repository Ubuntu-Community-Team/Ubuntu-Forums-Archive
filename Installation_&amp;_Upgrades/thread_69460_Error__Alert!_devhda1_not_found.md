---
title: "Error:  Alert! /dev/hda1 not found"
date: 2005-09-27
forum: Installation &amp; Upgrades
---

### Post by dvgrhl on 2005-09-27
I installed Ubuntu on an old Toshiba 320cdt laptop.  It installs fine and grub loads and everything.  It is the only OS on the HD.  However, when you let Ubuntu load, I get the splash screen, then that error:  Alert!  /dev/hda1 not found.  Dropping to a shell.

Then it hangs.  When I installed it I choose to erase the HD and let Ubuntu choose the partitions.  When I look at the partitions from the install CD, hda1 is set to /media/hda1.

Any ideas on what is causing this or how to resolve it?  If you need more info, I will be happy to supply it.

Thanks.

---

### Post by greenstar on 2005-09-27
at the shell, run: ```
sudo cp /etc/fstab /etc/fstab.bak
sudo gedit /etc/fstab
```

is /media/hda1 the OS partition? if so change the mount point for /dev/hda1 in fstab to / , save, then reboot.

If that doesn't work, post the fstab contents here, and I'll try to help.

greenstar

---

### Post by dvgrhl on 2005-09-27
Well, unfortunately it hangs at shell, so I cannot do that.  Also, I can boot to rescue mode from the cd and recovery mode from grub, however neither gedit nor nano work from there.  And in recovery mode I cannot see all the files.

Any idea how to do this in rescue mode?

---

### Post by greenstar on 2005-09-27
I'm gonna try booting from the live cd and see if that gives me access. I'll post my findings.

greenstar

**edit:**

The Ubuntu does not allow access to an installed filesystem - at least not easily. Do you have any other linux livecd's? Knoppix, DSL, Beatrix, Dynebolic? You can gain access to your fstab on the hard disk with one of those livecd's I mentioned, as the aforementioned distros will automount your hard disks.

greenstar

---

### Post by dvgrhl on 2005-09-27
I have a knoppix cd which I can give a shot, that is an excellent idea.  Thank you for taking the trouble to look into this for me.  Ubuntu is by far the best Linux distro I have tried, and the quality of the people on the forums here matches it.  Thank you.

---

### Post by greenstar on 2005-09-27
You're welcome.:D  I appreciate your gratitude, that's what makes it worthwhile to those of us who help. If you have more problems, I'll try to help as much as I can.

greenstar

---

### Post by dvgrhl on 2005-09-27
:( Knoppix won't let me save changed to the fstab, even with sudo.  Seems it makes all the files read only.  Any ideas around this?

---

### Post by greenstar on 2005-09-27
use ```
su root
``` instead of ```
sudo
``` I beleive the knoppix root pass is: toor but I can check that out.

greenstar

**edit:**

Sorry, wrong distro I was remembering above.

According to [this]("http://www.knoppix.net/forum/viewtopic.php?p=47430&sid=0bc19ae6379ffe579150018b6aa432dd#47430") post on knoppix.net forums the command for root privileges is:
```
su
``` no (blank) password, you'll know you're root when the $ turns into a #.

---

