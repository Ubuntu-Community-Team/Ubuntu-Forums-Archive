---
title: "Installing Ubuntu 9.10 into a RAID mirror with XP.  XP not recognised, so no GRUB."
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by padnoter on 2010-04-25
Hi,

Having got used to Ubuntu 9.10 on my laptop (grub dual boot with winXP), I am now trying to install a similar setup on my main PC.

The PC has an ABIT AS8 motherboard with RAID controller (INTEL 82801ER). Dual harddisks are installed in a RAID volume (mirror) using a combination of BIOS settings & drivers (intel 82801ER SATA RAID) provided. Windows XP (dirty word I know!) is installed. This setup has worked fine for years.

Now when I try to install Ubuntu 9.10, I was hoping to be offered the choice of installing it alongside XP using the GRUB loader to choose on bootup (as on my laptop - no raid). But this time, the partitioner can see the RAID volume space, but doesn't recognise any OS (the XP) inside it, and only offers to use all the space or specify the partitions manually.

I really need to keep the XP, so I'm stuck at this point.

Any ideas how I can get the Ubuntu install to recognise XP is installed and offer the dual-boot grub option?

Any help appreciated.

Thanks
PN

---

### Post by urey on 2010-04-25
I have the same question. follow here

---

### Post by padnoter on 2010-04-25
> **urey said:**
> I have the same question. follow here

follow where?

---

### Post by padnoter on 2010-04-27
ok I found a solution that worked for me (& hopefully will help others).

try ubuntu before installing
in a console confirm that ubuntu recognises raid volume (mine does);
```
sudo dmraid -r
```(should show something if it does)
run system/admin/GParted and reduce the winXP raid volume to less that half the total volume space. i.e. so that over half the volume is free & unused (for ubuntu)

then run the ubuntu install, and at the disk partitioner part, select
"use largest continuous free space"
option.
when you do this, suddenly winXP is recognised and shown, alongside the ubuntu to be installed.

After the install (assuming all is well!), reboot.
Grub doesn't have winXP as option so you can only go into ubuntu initially.
In ubuntu in a console;
```
sudo gedit /boot/grub/menu.lst
```and add to the end something like;
```
title WinXP
root (hd0,0)
makeactive
chainloader +1
```save and reboot and I then have ubuntu & winXP as options in the grub.

now go ahead and install all the ubuntu updates (incl. later grub etc)

---

