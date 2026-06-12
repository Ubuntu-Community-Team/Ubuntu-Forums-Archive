---
title: "Install with GRUB or LILO"
date: 2005-05-13
forum: Installation &amp; Upgrades
---

### Post by mmeijer on 2005-05-13
I tried the default 5.04 install with GRUB
and when booting stage1.5, got error 21.

I tried an 5.04 expert install with LILO
and when booting after install, LILO isn't
triggered, the boot goes straight to Windows.

My system is
  Dell Dimension 4550
  two 40GB drives, one master (hda), the other slave (hdb)
  using Intel 82801DB Ultra ATA Storage Controller
  (both drives seen in Windows XP until I formatted the slave
  during the ubuntu install)

In both cases I was writing to the MBR.
In the first case, I had to recover my MBR using the Windows XP
install CD and fixmbr.

Any ideas?
I've seen some posts of people installing other distros to
get the MBR right.  Is there another way?

Thanks a lot!!
Looking forward to trying Ubuntu.  I've used Slackware before,
but on another machine.


cheers

Mark

---

### Post by mmeijer on 2005-05-13
I found a newer BIOS version at dell.com.

Last time I tried, the Ubuntu installer wouldn't let me skip
ahead to just install the boot loader (expert mode), so
I'll try reinstalling everything.

---

