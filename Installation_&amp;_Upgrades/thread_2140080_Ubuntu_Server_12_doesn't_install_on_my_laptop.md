---
title: "Ubuntu Server 12 doesn't install on my laptop"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by jon80 on 2013-04-28
I tried to install Ubuntu Server on my Fujitsu Siemens Amilo Pro laptop, however, for some reason, although the installation is successful, the operating system does not load up, and, walking through the recovery options seems to have the laptop hang.  I cannot provide more specific details, one would have to reproduce the issue to identify the reasons.

---

### Post by MAFoElffen on 2013-04-28
- How much memory installed? I think I remember that only coming installed with 128MB...
- What version of Server Edition did you install? Your title said "12", which could mean 12.04 or 12.10...
- What server app's did you install?

Next would be to stop at the Grub2 menu... at the end of the BIOS post messages, press the left shift key repeatedly. At the grub menu display, hit a down arrow key. On server edition, you only have 2 seconds to do that.... That will lock the menu from disappearing. Then arrow back to the top line.

Press "e" to edit. Arrow down to the line that begins with "linux". Arrow over to the end of that line. Append it will "--verbose single"... Press <Cntrl><b> to boot...

That would boot the kernel to a single user mode with verbose boot messaging turned on, with the meesages show to screen instead of in background. Messages will fly by. Please try to look for errors.

---

