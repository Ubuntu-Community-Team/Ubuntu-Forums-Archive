---
title: "wubi install no root file system"
date: 2011-04-22
forum: Installation &amp; Upgrades
---

### Post by wrwrainbow on 2011-04-22
I downloaded the wubi installers for both 10.04 and 10.10 and then downloaded the 32bit 10.10 desktop installation iso. Forced wubi 10.04 to download and install 32bit version of ubuntu and after the download completed I restarted as requested and selected ubuntu to continue the install.  Message said that it was completing the installation and then while verifying the install config I got the message "No Root File System defined" Please correct from partioning menu and I could go no further so powered off the system.

Restarted and started Windows and uninstalled ubuntu then ran wubi 10.10 which used the already downloaded 10.10 iso.  I restarted as requested and selected ubuntu to continue the install with the same result.

Any suggestions:

The following files were created:

c:\ubuntu\disks\root.disk
c:\ubuntu\disks\swap.disk

---

### Post by bcbc on 2011-04-22
This problem can be caused by a mix of GPT and MBR partition table info, as well as leftover fakeraid metadata (or an unsupported raid environment).

I suggest burning one of those ISOs to a CD and booting it as a live CD (Try without installing). Then run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results.

---

