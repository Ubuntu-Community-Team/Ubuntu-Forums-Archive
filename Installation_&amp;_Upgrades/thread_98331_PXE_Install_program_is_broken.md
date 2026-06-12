---
title: "PXE Install program is broken"
date: 2005-12-03
forum: Installation &amp; Upgrades
---

### Post by nicheware on 2005-12-03
Hello,

Installing ubuntu via PXE boot would appear to me to have a fatal flaw in the install program.  The machine boots via TFTP but once the install starts up it is unable to detect the already functioning network card.  This problem exists in all modes- just pressing enter at the install prompt, linux, expert, server, or server-expert.  My hardware may have something to do with it- being a Thinkpad X21 with a 3Com 3C9X nic.  

Has anyone solved this problem with adjustments?  I think the problem is in the installer...

Thanks!
Thomas Hutton

PS: Debian installs just fine via PXE on the same hardware, from the same tftp server

---

### Post by Leviathan05 on 2005-12-28
I have the same problem.  IBM Thinkpad X20.  The machine boots via PXE, and the installation begins.  However, when you get to the section on hardware detection, it fails to find the already functioning network card.

I have no CDROM or Floppy drive, but really want Ubuntu installed.

Anyone have any suggestions?

---

### Post by Littlehawk on 2008-05-09
I know this is an old thread, but I have the same problem. Maybe someone has come across this in the last 2-1/2 years and knows what to do.

I can boot my laptop using PXE. I have a pico-itx I'm trying to bring up and it hangs at the point of opening the archive. I think it may have something to do with the error message "No Network Interfaces Detected"

It also says something about "You may need to load a specific module for your network card, if you have one. For this, go back to the network hardware detection step"  What does this mean and what can I do about it? 	](*,)

Thanks,
Jim

---

