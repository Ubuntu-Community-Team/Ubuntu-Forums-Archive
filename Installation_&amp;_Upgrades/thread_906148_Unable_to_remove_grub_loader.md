---
title: "Unable to remove grub loader"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by thirteenlisk on 2008-08-31
I recently uninstalled Ubuntu and now I can't get anything working.

I'm unable to boot from CDs.  I've tried formatting the disk several times.  Every time it just bypasses the boot to CD option, defaulting to the grub loader error 22.

---

### Post by Partyboi2 on 2008-08-31
Make sure that "boot from cd" is first in your bios boot order. What type of cd are you trying to boot? Is it a bootable cd?

---

### Post by kellemes on 2008-08-31
> **thirteenlisk said:**
> I recently uninstalled Ubuntu and now I can't get anything working.

I'm unable to boot from CDs.  I've tried formatting the disk several times.  Every time it just bypasses the boot to CD option, defaulting to the grub loader error 22.

You need to enter BIOS to set the diskdrive to be first in the bootorder.
You can use [Super Grub Disk]("http://www.supergrubdisk.org/") to remove Grub from the MBR and/or restore the Windows bootloader if you wish.

---

### Post by thirteenlisk on 2008-08-31
The CD is set to the first in the boot order.  A message comes up "Boot from CD:" and then the CD does not boot.  I've tried 4 different CDs, and I know at least one of them is bootable for sure.

---

### Post by thirteenlisk on 2008-08-31
Basically, here is a list of the things that I've done:

I went to install another OS, removing Ubuntu.  That installation failed, and I was left with nothing but the GRUB load error.  I tried multiple bootable CDs and none of them booted.  The message came up: "Boot to CD" and the CD just doesn't boot (I do have the boot order correct).  Then the GRUB load error comes up.

I took my hard drive out, put it into another computer, installed Windows Vista.  Then I put it back in, still got the GRUB load error.  Then I downloaded an MBR fix program, ran it from the other computer.  The GRUB load error is gone, but still no CD will boot.  I installed Windows Server Edition from the other computer, and now that will not run when I put it back on the broken computer.  Windows starts to load, and the system crashes.

---

### Post by Partyboi2 on 2008-09-01
Have you tried to change you back to default settings? Have you tried putting in a different cdrom to see if that could be the problem?

---

