---
title: "Had Ubuntu 9.10 working until MOBO upgrade"
date: 2010-06-24
forum: Installation &amp; Upgrades
---

### Post by bcatanzaro on 2010-06-24
Hi,

  I had Ubuntu 9.10 working great (single O/S PC), but on an old MB.  I upgraded another PC and scavenged an:  ASUS P5B-E MB w/3 GB RAM.  I hooked up my IDE drive and booted.  I got the infamous GRUB error:

GRUB Loading stage 1.5.
GRUB loading please wait...
Error 21

  Booting off of the LiveCD, I can see my old drive.  I can identify the boot partition.  I cannot repair the GRUB.

1.  Is it true that GRUB doesn't work with this MB + IDE drives?
2.  Can I repair GRUB?
3.  Should I replace GRUB with LILO?
4.  Can I recover without trashing my files?

Thanks!

---

### Post by sikander3786 on 2010-06-24
Hi.

After upgrading the mother board you should reinstall ubuntu. Even if you succeed in booting it and getting a display, I think the performance will be too low.

You should be able to backup your data. Boot the live cd, copy everything you want to save to a safe location and reinstall.

I have only this solution in my mind. Otherwise wait for wiser heads than mine.

Regards.

---

### Post by bcatanzaro on 2010-06-24
Hi,

  Thanks for the advice.  I was optimistic because others seemed to have been successful with an MB upgrade wo/reinstalling the O/S.

  Is there a utility to list/capture/backup the installed packages?  How do I keep track of what I installed previously to mirror this in the new install?

---

### Post by sikander3786 on 2010-06-24
There is a software called aptoncd which burns all the downloaded packages to cd for future installations. But that will not be helpful to you coz you have no gui.
There should be some command-line way of keeping record of packages but I don't know.

Wait for someone else to reply.

Regards.

---

### Post by sanderj on 2010-06-24
> **bcatanzaro said:**
> Hi,

  I had Ubuntu 9.10 working great (single O/S PC), but on an old MB.  I upgraded another PC and scavenged an:  ASUS P5B-E MB w/3 GB RAM.  I hooked up my IDE drive and booted.  I got the infamous GRUB error:

GRUB Loading stage 1.5.
GRUB loading please wait...
Error 21

  Booting off of the LiveCD, I can see my old drive.  I can identify the boot partition.  I cannot repair the GRUB.

1.  Is it true that GRUB doesn't work with this MB + IDE drives?
2.  Can I repair GRUB?
3.  Should I replace GRUB with LILO?
4.  Can I recover without trashing my files?

Thanks!

Changing the mobo shouldn't be a problem. Try to repair GRUB; see [http://ubuntuforums.org/showthread.php?t=1146056](http://ubuntuforums.org/showthread.php?t=1146056)

EDIT: most important if you use the same (number) IDE-connector: connector 0 or 1. That determines hd0 versus hd1.

---

### Post by bcatanzaro on 2010-06-24
I figured I should be able to upgrade MB wo/new install or loss of GRUB.

Tried [http://ubuntuforums.org/showthread.php?t=1146056 .]("http://ubuntuforums.org/showthread.php?t=1146056")
No errors were generated.  Same result when rebooting:  Err 21...

---

