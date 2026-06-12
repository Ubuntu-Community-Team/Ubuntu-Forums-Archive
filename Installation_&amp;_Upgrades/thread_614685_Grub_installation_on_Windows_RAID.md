---
title: "Grub installation on Windows RAID"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by cabber on 2007-11-16
I went to install Ubuntu 7.10 and all went well.  However, when I reboot the system, the grub does not show up.  The system boots right into Windows Vista.  I'm positive this has something to do with the RAID set up I have.  Vista is installed on a RAID set up while I going to put Ubuntu on a stand alone drive.

Is there a way to manually install the grub?  Or can I install it on the stand alone drive?  Please advise on any suggestions you may have.  Thank you.

cabber

---

### Post by Returner on 2007-11-18
I'm a new user to ubuntu...anyway, I think the reason, why it didn't boot using GRUB, is that the Master Boot Record (MBR) of the RAID disk set wasn't changed at all, which is not bad for the moment...

What happens, if you temporarily set BIOS to boot from the drive, that contains the GRUB and the ubuntu installation? Does this solve your problem?

I plan to do something similar, which is: keep my RAID 1 using Widows for instance and start with some other Harddisk the GRUB

---

