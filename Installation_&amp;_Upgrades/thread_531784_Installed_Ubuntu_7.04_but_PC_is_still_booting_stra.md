---
title: "Installed Ubuntu 7.04 but PC is still booting straight into XP"
date: 2007-08-22
forum: Installation &amp; Upgrades
---

### Post by MegaSvensk on 2007-08-22
Hi,

I'm totally new to Linux but I wanted to try Ubuntu because a friend of mine recommended it. Anyway, I shrunk one of my NTFS partitions and installed Ubunto but after the reboot, the PC booted straight into Windows XP.

The Ubuntu installation program did install Grub but I think it installed it into the drive I installed Ubuntu to (Disk 0) and I guess it has to be on the same drive as Windows (Disk 1). 
So how do I go about fixing this so I can boot into Ubuntu?

---

### Post by heimo on 2007-08-22
> **MegaSvensk said:**
> Hi,

I'm totally new to Linux but I wanted to try Ubuntu because a friend of mine recommended it. Anyway, I shrunk one of my NTFS partitions and installed Ubunto but after the reboot, the PC booted straight into Windows XP.

The Ubuntu installation program did install Grub but I think it installed it into the drive I installed Ubuntu to (Disk 0) and I guess it has to be on the same drive as Windows (Disk 1). 
So how do I go about fixing this so I can boot into Ubuntu?

You could try to just change boot order in BIOS so that it'll take you to Grub on Disk 0, which hopefully has also entry for Windows. Otherwise, you'll probably need to reinstall Grub. EDIT: Or if booting to Ubuntu works after changing BIOS setting, but there's no entry for Windows, you could easily add that one to Grub config.

---

### Post by jfinkels on 2007-08-22
> **heimo said:**
> You could try to just change boot order in BIOS so that it'll take you to Grub on Disk 0, which hopefully has also entry for Windows. Otherwise, you'll probably need to reinstall Grub. EDIT: Or if booting to Ubuntu works after changing BIOS setting, but there's no entry for Windows, you could easily add that one to Grub config.

Ditto. Change your boot order in your BIOS to boot from the disk that has the Ubuntu partition BEFORE the disk that has the Windows partition.

---

### Post by MegaSvensk on 2007-08-22
> **heimo said:**
> You could try to just change boot order in BIOS so that it'll take you to Grub on Disk 0, which hopefully has also entry for Windows. Otherwise, you'll probably need to reinstall Grub. EDIT: Or if booting to Ubuntu works after changing BIOS setting, but there's no entry for Windows, you could easily add that one to Grub config.
Thank you, that did the trick. I'm posting from Ubuntu right now and I saw Windows XP listed in Grub.

I would like Windows to be the default OS though. How can I do that?

---

### Post by merlinus on 2007-08-22
```

gksudo gedit /boot/grub/menu.lst

```Look for a line near the top -- default 0.

Change that to your windows entry.  Counting starts at zero, so if there are three entries for ubuntu, then windows is number four, and change the line to:

default 3

-merlin

---

