---
title: "CD-ROM data CDs not recognized by 15.10"
date: 2016-01-11
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2016-01-11
All my PCs run Ubuntu 15.10 with dual boot to Win 10 or Win XP.  I generally do not receive data from my clients on CD-ROM.  Received two CD-ROMs from a client.  Put them in the CD/DVD-ROM drive on my DELL Vostro 3500 laptop: nothing.  Put a USB stick in same PC, and Nautilus finds it.  Next, go over to one of my desktop PC running Win 10 64 Pro.  CD-ROMs read perfectly.  Go to nearly identical PC running 15.10.  CD-ROM not recognized, but USB sticks are.  Reboot PC into Win XP.  CD-ROMs read perfectly and copy to a subdirectory on XP.  Reboot that PC into Ubuntu 15.10 and copy files from XP partition onto a Ubuntu 15.10 partition.

Am I missing something?

Thank you,

John

---

### Post by ubfan1 on 2016-01-11
Could be a "live filesystem" problem. [http://windows.microsoft.com/en-us/windows/which-cd-dvd-format#1TC=windows-7](http://windows.microsoft.com/en-us/windows/which-cd-dvd-format#1TC=windows-7)

---

### Post by cigtoxdoc on 2016-01-11
Thank you for your reply.  Data CD-RW burned from Ubuntu 15.10 ran on all PCs.  Another CD-RW burned from Win 10 64 Pro using the "mastered" format (supposedly compatible with all OS) did not run under Ubuntu 15.10.

John

---

### Post by ubfan1 on 2016-01-11
Did you close the session on the "W10" burn?  That's the necessary part for reading the disk in a different computer (or OS I assume).

---

