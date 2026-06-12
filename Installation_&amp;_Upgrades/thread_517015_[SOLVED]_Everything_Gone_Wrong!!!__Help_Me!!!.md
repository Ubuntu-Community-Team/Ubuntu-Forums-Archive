---
title: "[SOLVED] Everything Gone Wrong!!!  Help Me!!!"
date: 2007-08-03
forum: Installation &amp; Upgrades
---

### Post by MR.UNOWEN on 2007-08-03
Hello, I'm an XP/ new Ubuntu user and unfortunately after an unsuccessful installation, I'm no longer able to even get into xp. So far from what I can tell the, file system is intact. So my only question is how do get Grub (I think that's what it's called) out of my xp partition. Can anyone help me rescue what remains of my computer?

---

### Post by merlinus on 2007-08-04
Try this:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Alternatively, boot from your windows cd, select recovery mode (or something like that), and fixmbr.

-merlin

---

### Post by Blackforge on 2007-08-04
> **MR.UNOWEN said:**
> Hello, I'm an XP/ new Ubuntu user and unfortunately after an unsuccessful installation, I'm no longer able to even get into xp. So far from what I can tell the, file system is intact. So my only question is how do get Grub (I think that's what it's called) out of my xp partition. Can anyone help me rescue what remains of my computer?

Boot off your Windows XP disc.  And boot it into Recovery Console mode.  From the Recovery Console type in:

FIXMBR C:\
FIXBOOT C:\

That should replace grub.  This is assuming your boot drive is the first drive in the system.

If that doesn't do it, you may need to boot back into the Recovery console and rebuild your boot.ini file.

From the console:

bootcfg /rebuild

That will scan all partitions for Windows installations.

If THAT doesn't do it...

FIXMBR C:
FIXBOOT C:
COPY CDDrive:\I386\NTLDR C:\
COPY CDDrive:\I386|NTDETECT.COM C:\
BOOTCFG /rebuild.

How to use Recovery Console:
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

If its still not fixed.  Look around on your drives in the Recovery Console to make sure there are still files on the disk.  You might need some recovery software otherwise.  (I highly recommend GetDataBack from runtime.org).

---

### Post by MR.UNOWEN on 2007-08-04
Yay, I saved xp....   I think I'll give up on  ubuntu for now.  Still needs a little more improvement.

---

