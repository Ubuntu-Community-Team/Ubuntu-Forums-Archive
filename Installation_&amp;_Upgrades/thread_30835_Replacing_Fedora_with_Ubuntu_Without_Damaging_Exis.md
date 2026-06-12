---
title: "Replacing Fedora with Ubuntu Without Damaging Existing WinXP Installation"
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by zptak on 2005-04-30
Hi,

I currently have GRUB installed to boot into either Fedora Core 2 and Windows XP. I want to install Ubuntu over Fedore Core 2 (I assume I can just delete/recreate the Linux partitions w/o affecting the NTFS ones during the Ubuntu install). What I'm worried about is that the installation will also replace GRUB, and then I wont be able to boot into WinXP. What exactly should I do so that I can replace FC2 with Ubuntu without damaging WinXP and all of my NTFS/FAT partitions?

Thanks in advance for your help!

---

### Post by jodef on 2005-04-30
During the Ubuntu install process you are prompted to install GRUB if you are installing Ubuntu over the Fedora partition, Ubuntu won't have any problems detecting the WinXp install. You will be installing GRUB to the MBR of your harddrive if you have a single ide drive it's denoted /dev/hda.

Installs can be a little intimidating read twice click once you'll be ok. :)

---

### Post by Bob D. on 2005-04-30
> Installs can be a little intimidating _read twice click once_ you'll be ok. Good advice, to which I would add "backup first."

Bob

---

