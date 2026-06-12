---
title: "Install seems to have install GRUB on my Mac Book Pro."
date: 2018-11-21
forum: Installation &amp; Upgrades
---

### Post by KeithSloan on 2018-11-21
A friend and computer shop owner created a bootable version of Ubuntu 18.04 on an extrenal USB drive for my Mac.

Trouble was I don't think he selected the option that mean't the driver for my Mac's broadcom Network adapter got installed.
He gave me a USB wifi dongle, but the performance was terrible and system unusable.

So I resorted to creating Ubuntu 18.04 on a USB memory stick. This seemed to work just fine. So I tried doing an install
Ubuntu 18.04 on the external USB drive. i.e. overwrite the system on the externql USB drive.
This seems to have worked ( Have not had time for a full check ) but it seems to
have created a GRUB partition on my Mac. My Mac now boots to Grub and I have to enter "exit"
to boot to OSX

There are no menu's like I was used to before when I had a PC which dual booted to Windows & Ubuntu.

1) How can I check the partitions on my Mac.
2) How can I create GRUB menu's

I feel VERY hesitant about aksing to delete the GRUB partition and restoreing my Mac, just in case things
go wrong and I end up with an unusable system.

---

### Post by oldfred on 2018-11-21
I do not know Mac, but this may give some info. What version Mac, what I have seen is there is differences between versions.
Did you install in UEFI boot mode, as that is standard with Mac.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

