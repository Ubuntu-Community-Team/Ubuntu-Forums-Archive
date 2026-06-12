---
title: "Grub2 prevents Windows 7 from suspend"
date: 2011-07-03
forum: Installation &amp; Upgrades
---

### Post by oryan_dunn on 2011-07-03
I've got the same problem as this thread:
[http://forums.linuxmint.com/viewtopic.php?f=46&t=38092&p=443236#p443236](http://forums.linuxmint.com/viewtopic.php?f=46&t=38092&p=443236#p443236)

Basically, I've got Ubuntu Lucid on one drive, and Windows 7 on another.  Both can be booted by the BIOS to their respective systems.  On the Lucid machine, I re-ran update-grub to add the Windows 7 entry.  Grub will boot Windows 7 just fine.  However, when Windows is booted by Grub, it is unable to go to sleep.

It looks like Grub directly boots to the Windows 7 partition.  I wonder if Windows can detect that "it's" MBR didn't boot it and can prevent the suspend.  Is it possible to tell Grub to pass off to another MBR instead of a partition?

---

### Post by YesWeCan on 2011-07-03
Interesting. Which is another way of saying "I don't know".
I am disinclined to think it is the way Grub is booting Windows because AFAIK it essentially does it the same way the MBR boot code does. Both load and execute the Windows partition boot code. How could Windows tell which way it had been booted?

This is conjecture but I guess that one thing it probably can tell is which disk was booted first. It may interrogate the bios to check the boot priority. Windows has a history of complaining when it is not the first boot disk, sometimes updates fail.

You might try a quick experiment. Set Windows to be the first in boot priority in the bios. But when you boot use the special function to choose the Ubuntu disk on the fly (is it F11?). Then choose Windows in Grub and see if it can hibernate. If it does, the problem is the boot priority setting in the bios rather than the boot sequence.

None of this will solve the problem, tho. :sad:

---

### Post by oryan_dunn on 2011-07-04
> **YesWeCan said:**
> You might try a quick experiment. Set Windows to be the first in boot priority in the bios. But when you boot use the special function to choose the Ubuntu disk on the fly (is it F11?). Then choose Windows in Grub and see if it can hibernate. If it does, the problem is the boot priority setting in the bios rather than the boot sequence.

None of this will solve the problem, tho. :sad:

I gave this a shot, and even when selecting the Ubuntu disk on the fly, the Windows machine still wouldn't suspend.

---

### Post by Mark Phelps on 2011-07-04
> **oryan_dunn said:**
> Grub will boot Windows 7 just fine.  
GRUB is UNABLE to boot Windows; instead, all it does is handoff the boot function to whatever is in the partition you setup using GRUB.  The Win7 boot loader does the rest.

I have Win7 being booted in just the same manner, and SLEEP works fine.  SUSPEND does not work, but then, it never did.

If you have each drive as bootable (which you should), then try a test with the Ubuntu drive disconnected.  In that case, it's likely that SLEEP will still not work.  But, if it does work, then it's more likely a BIOS setting problem with both drives connected -- rather than GRUB.

---

### Post by oryan_dunn on 2011-07-04
With only the WIndows 7 drive connected, suspend works.  With both drives connected, and the Windows 7 drive directly booted by the bios, suspend works.  With both drives connected, grub handing off boot to windows 7, suspend does not work.  Ubuntu setup the grub boot command to set root hd1,1.  I've also tried just hd1 with no partition number, that also works.  I've tried experimenting with the grub2 drivemap command, but have yet to find a sequence of commands that will boot windows 7.

---

### Post by YesWeCan on 2011-07-04
There are at least two things changing at the same time, the use of Grub and the disk boot order. In either case you are stuffed. :p

Unless you boot Ubuntu from Windows, of course. Windows then reciprocates by chain loading Grub. This is doable and I predict it will eliminate your hibernation issue as it eliminates both possible causes. You'll have to search for the details of adding a boot menu entry to W7. A free program called EasyBCD may help.

---

