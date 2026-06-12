---
title: "Can't start the X server"
date: 2005-06-06
forum: Installation &amp; Upgrades
---

### Post by twoseids on 2005-06-06
Just a few days ago, successfully installed Ubuntu on my Inspiron 4100.  Now doing the same on wife's Inspiron 1100.  Got through the install, did the reboot, and during the post-reboot stuff, I got this error message:

"I cannot start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

When selecting "Yes" and hitting Enter, I get a page of Ubuntu information (version, build date, kernel info, etc.).  I eventually end up at a command prompt - while still on black screen.

Any ideas?  I googled the message above and didn't really find anything out.

---

### Post by twoseids on 2005-06-06
Never mind, I found the answer, which I'll post here for future readers:

There was a problem with the BIOS that was fixed with version A29. The latest version is A32.

I got the following file and ran it from Windows: [ftp://ftp.dell.com/bios/I1100A32.exe](ftp://ftp.dell.com/bios/I1100A32.exe) and it booted up just fine.

---

