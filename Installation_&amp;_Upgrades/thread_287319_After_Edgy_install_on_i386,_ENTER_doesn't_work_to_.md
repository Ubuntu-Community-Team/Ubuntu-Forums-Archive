---
title: "After Edgy install on i386, ENTER doesn't work to reboot."
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by tedrogers on 2006-10-28
Now...this doesn't seem to have affected the installation of Edgy in any way...or maybe it did because I have had my fair share of problems with my ATI card and fglrx....but that is perhaps a different issue.

Anyway, when I installed Edgy from the Live CD, the installation finishes as expected, then you click REBOOT and Edgy begins to shutdown before starting for the first time. When the CD tray ejects and you get the message to "Press ENTER to reboot" nothing happens! The progress bar also has a little bit extra to go, but it seems that the system has frozen?!

Nothing works, except to press the reset button on the PC....then it boots from Hard Disk as you'd expect.

This seems really weird to me and I wonder if anyone else has experienced this? It also happened with the Release Candidate.

Maybe this is what has caused my fglrx problems (now solved with the help of people on this wonderful forum), but I doubt it.

---

### Post by MmmSkyscraper on 2006-10-28
This happened to me with the 64-bit version. I did a clean install with the final Live CD.

---

### Post by tedrogers on 2006-10-28
Did it all work fine for you, even when the ENTER button failed to work?

---

### Post by frenkel on 2006-10-28
When shutting down or rebooting the AMD64 or PowerPC LiveCD, if it does not automatically power off or reboot when you press ENTER use your computer's power or reset buttons. It is safe to do so at this point. [WWW] [http://launchpad.net/bugs/58503](http://launchpad.net/bugs/58503)

From: [https://wiki.ubuntu.com/EdgyReleaseNotes](https://wiki.ubuntu.com/EdgyReleaseNotes)
You could have found that yourself...

---

### Post by MmmSkyscraper on 2006-10-28
> **tedrogers said:**
> Did it all work fine for you, even when the ENTER button failed to work?

I didn't have any problems.

---

### Post by graysn05 on 2008-02-12
I had this problem after installing the x86 version twice, each time i had to press the reset button on the machine and it didn't load GRUB on restart.  Vista just booted up.  I thought it was because i have a usb keyboard, i'm not sure, but linux doesn't boot...

---

