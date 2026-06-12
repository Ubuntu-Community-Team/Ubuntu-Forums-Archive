---
title: "Ubuntu Server 8.04 installs, won't boot"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Leomania on 2008-06-28
I just downloaded and installed Ubuntu Server 8.04 for amd64 on my ASUS A8V Deluxe based computer. This motherboard uses the VIA K8T800Pro chipset and VT8237 southbridge. The processor is a Athlon64 4400+. Initially I installed it on an IDE drive, and later tried it on a SATA drive. Everything appears to go normally during the install, but after rebooting I'm faced with just a blank screen after the BIOS messages. There is a blinking underscore type cursor, and I see it do what looks like one carriage return, and there it sits... no Ubuntu Server joy.

I've checked settings for boot order and such in the BIOS; everything looks fine. It does appear that it tries to boot from the hard drive, and that something is borked with grub or something like that. I'm hoping someone has run into a similar issue and knows what might be going on.

This system is meant to be a replacement for my four-year old P3-based home server, and I'd really like to be able to use Ubuntu Server since it has the best long-term support bar none. Any help would be greatly appreciated so I can get this project off the ground!

Thanks in adavance...

---

### Post by cdtech on 2008-06-28
May need to use your live cd, go to a prompt and type grub-install /dev/sda (if it's the primary drive) this will set up grub properly to the primary drive.

Hope this helps......

---

### Post by Leomania on 2008-06-28
> **cdtech said:**
> May need to use your live cd, go to a prompt and type grub-install /dev/sda (if it's the primary drive) this will set up grub properly to the primary drive.

Hope this helps......
Okay, I'm in with the live CD and it's interesting; during install, the SATA drive was enumerated as sdb and the data drive (primary master on the IDE cable) was sda. But in BIOS I had previously set up the SATA drive to be the main boot drive, so I thought that strange. Still, everything installed normally so it must have been enumerated that way properly at the time.

Now with the live CD booted, the SATA drive is considered to be sda and the IDE drive is sdb.

Since the fstab uses that UUID method to identify the hard drives, perhaps I just need to run grub-install to sda and see how that goes?

---

### Post by Leomania on 2008-06-28
That got me closer! Now I've got a grub boot menu. But I get this error when I select one of the kernels:

Error 15: file not found

I edited one of the entries, and saw it was set to "root (hd1,0)" instead of "root(hd0,0)". Changed that interactively and now I'm booting happily!

Thanks for the suggestion, looks like it got me to a booting system.

---

### Post by Leomania on 2008-06-28
Just to capture the specific command I had to use when booted into the live CD to get grub to work properly.

First, I browsed the disk using the "Computer" menu item which mounted /dev/sda on /media/disk. Then I opened a terminal window and ran the following command.

# sudo grub-install --root-directory=/media/disk /dev/sda

Rebooted and all was right with grub.

---

### Post by Leomania on 2008-06-29
One more note for the archives...

I have done one additional reinstall, and had no problems with grub. What I found was the second drive (primary slave on the IDE interface) had its partition marked as bootable. I changed that to not bootable, and everything worked as expected upon reboot. Why this might have caused an issue, I do not know; but since it was the only thing I did differently compared to a previous installation attempt, I must assume it had some bearing on things.

Hope this helps someone.

---

