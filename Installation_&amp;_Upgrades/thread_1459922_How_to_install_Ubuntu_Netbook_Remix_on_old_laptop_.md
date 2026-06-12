---
title: "How to install Ubuntu Netbook Remix on old laptop with no ext. media boot support?"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by Corvinian on 2010-04-22
Hi,

do you have any suggestions how I can install Ubuntu netbook edition on an old Laptop (Fujitsu-Siemens Lifebook 2131) currently running Windows 2000 with all servicepacks (if I recall correctly it is SP5) **without boot-support for USB-Stick/Media, CD-ROM, PXE/netboot; booting is only supported from builtin harddisk and from floppy-disk drive, which is definitely broken.** (with working floppy disk drive all would be fine). I also installed WUBI, but the harddisk is only 4 GB, so I had to use the USB-Stick as the Ubuntu install partition and this is not supported by the Laptop as it cannot boot from it. :(

Has anybody an idea, is it viable to online-resize an NTFS-partition to create a small linux-partition for bootstrapping the install?? I do not want to, it's still useful, so when crashing the NTFS-filesystem is likely I prefer not to take this route and leave the laptop with Win2k installed.

But maybe there are other ways to do this I haven't thought of.

---

### Post by snivitz on 2010-05-09
I was able to install Ubuntu onto an aging Thinkpad in similar condition as yours using the excellent howto [here]("http://marc.herbert.free.fr/linux/win2linstall.html").

---

### Post by Corvinian on 2010-05-11
Thank you for this, it looks very promising. :)

---

### Post by InfectionZero on 2010-05-11
Can anyone confirm that this works for 10.04? I have a netbook with a similar issue and would like to install Kubuntu netbook remix.

---

