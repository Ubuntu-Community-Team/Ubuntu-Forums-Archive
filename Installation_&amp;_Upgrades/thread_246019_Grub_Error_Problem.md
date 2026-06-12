---
title: "Grub Error Problem"
date: 2006-08-28
forum: Installation &amp; Upgrades
---

### Post by hdmorris on 2006-08-28
I've read a couple of other threads related to dual boot problems and grub errors and can't decide how they are related so here goes my story:

My system has two 80 MB SATA drives, and I moved averything Windoze related to the first drive and reformatted the second to devote it to Ubuntu. I installed 6.06 from the live CD. Everything seemed to work fine for a couple of days. Then I got an error message from grub while booting (can't remember which error), but on a reboot Ubuntu booted fine, and later so did Windows. The next day I got multiple intermittent errors from grub in stage 1.5. Errors seemed to all be 15, 18 or 25. It finally locked on error 25 so that I could no longer get into anything. I could boot from the live CD but couldn't figure out how to get to the two hard drives (I'm new here!). I finally used the Windows repair console (Windows CD) to reinstall the MBR which got me Windows back but left me with no way to access Ubuntu. A Google search gave the the following information concerning the grub errors:
-----------
15 : "Error while parsing number"

This error is returned if GRUB was expecting to read a numbur and encountered bad data.

18 : "Invalid or unsupported executable format"

This error is returned if the kernel image boing loaded is not recognized as Multiboot or one of the supported native formats (Linux zImage or bzImage, FreeBSD, or NetBSD).

25 : "Unrecognized command"

This error is returned if an unrecognized command is entered into the command-line or in a boot sequence section of a config file and that entry is selected.
-----------------
I have reformatted the second drive and run the full suite of Norton System Works utilities on both hard drives and can find no problems there. Any suggestions before I reinstall Ubuntu would be appreciated!

---

### Post by jerry_c on 2006-08-28
Dear Morris,

This is probably the thread you want. [http://ubuntuforums.org/showthread.php?p=1431609]("http://ubuntuforums.org/showthread.php?p=1431609")

Catlett really knows this stuff well. You'll see how stuck I was on this yesterday, and by last night I was posting a solution. Posting to an active existing thread related to your problem is far more likely to get you the help you want than hoping somebody will find your brand new thread.

Good luck.

---

### Post by hdmorris on 2006-08-28
Thanks Jerry! I have found lots of good information branching off that thread. Your tip about posting to an existing thread is probably a good one. The problem is that there are SOOO MANY threads, how does one find time to review them all?

Jack

---

### Post by confused57 on 2006-08-28
I'm not familiar with SATA drives, but you might want to consider using the Ubuntu as the 1st hard drive and Windows as the 2nd hard drive(#2 controller?)...using this method:

[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

Here's someone(Cariboo1938), who had success doing it this way:
[http://www.ubuntuforums.org/showthread.php?t=229909&page=2](http://www.ubuntuforums.org/showthread.php?t=229909&page=2)

---

