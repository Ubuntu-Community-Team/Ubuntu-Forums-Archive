---
title: "Ubuntu wont boot after load, ntoskrnl.exe error"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by RichieBeebe on 2007-10-26
I have a computer I don't use any more, so I decided to give Ubuntu a try (I'm a newbie). The computer previously had Windows 2000 professional.

I have a disc which has 7.04 on it. I am going for a complete clean install, no partitioning or anything else. It all installed seemingly correctly, but when it shuts down and reboots after installation it displays the error message:

> Windows 2000 could not start because the following file is missing or corrupt:
<windows 2000>\system32\ntoskrnl.exe
Please re-install a copy of the above file.

Anyone know how to fix this problem?

-edit- Sorry for the mistake in the title, i meant "boot after install".

---

### Post by Pumalite on 2007-10-26
DBan the drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/), then use Gparted Live CD and make a large partition of your whole hard drive formatted ext3. Then install.
256 MB of RAM or less> Xubuntu Alternate CD.

---

### Post by paul.matthijsse on 2007-10-26
Hello, your computer still thinks it has to load Windows; I suggest to do a reinstall and tell the installer to wipe all the partitions it sees. That - of course - implies that you will loose all data that are still there. 

Cheers, Paul.

---

### Post by ddrichardson on 2007-10-26
When you say "no partitioning" how are the partitions currently laid out?

---

### Post by wpshooter on 2007-10-26
Use KILLDISK to WIPE that drive completely CLEAN.

[www.killdisk.com](www.killdisk.com)

---

