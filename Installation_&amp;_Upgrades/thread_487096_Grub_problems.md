---
title: "Grub problems"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by sinfony on 2007-06-28
I'm having a lot of trouble getting Grub set up properly.  Let me describe my situation:

I recently switched out the hard drive on my laptop (from a 40gig to a 60gig).  After getting Windows back up and running on the 60gig drive, I put the old 40gig in a USB enclosure and installed Ubuntu on it.  During that install, Grub was installed to the 60gig (Windows) drive.  When I tried to boot, I got Grub Error 17.  After looking around for help on that, I restored the Master Boot Record of the Windows drive, installed Grub to the Ubuntu drive, and changed the BIOS boot order so it would boot from that drive.  I managed to configure Grub to boot Ubuntu, but when I try to boot Windows I get Error 13.  I know there's nothing wrong with the Windows drive itself because when I unplug the Ubuntu drive or change the boot order to boot first from the Windows drive, Windows runs perfectly.  In menu.lst, the entry for Windows is:

rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

I'm pretty sure that configuration is right, so I don't know why it doesn't work.  Also, interestingly, I can only get Ubuntu to boot by declaring root (hd0,0) in its entry in menu.lst, even though the Ubuntu drive is actually dev/sdc, which should map to (hd2,0).

Anybody know what's going on here?  I'd really like to be able to dual-boot without having to unplug drives at every turn.

---

### Post by mikewhatever on 2007-06-28
To find out what grub calls your hdds, type
> cat /boot/grub/device.map
Also, if Ubuntu boots with (hd0,0), try substituting (hd1,0) for Windows.

---

### Post by sinfony on 2007-06-28
device.map shows the correct mappings for all the drives.  I'll try changing the Windows entry to (hd1,0) and see how that goes.

---

### Post by sinfony on 2007-06-28
Success!  I changed the Windows entry to:

root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
chainloader +1

Thanks for the tip, Mike!

---

