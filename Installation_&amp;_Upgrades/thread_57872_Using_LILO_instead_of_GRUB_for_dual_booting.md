---
title: "Using LILO instead of GRUB for dual booting"
date: 2005-08-18
forum: Installation &amp; Upgrades
---

### Post by vimo on 2005-08-18
I would like to use LILO instead of GRUB on a system with Win XP installed.
As I did previously with an installation of SUSE Linux, I try to set the system to boot from a floppy disk using LILO (avoiding to write the MBR). But it seems impossible to do. The only option for LILO is the installation on the hard disk.
Is there a way to do what I want?
If it is not and I have to write the MBR, is there a way to uninstall the boot loader (GUB or LILO) restoring the WinXP boot?

---

### Post by beebelo on 2005-08-24
I can't give you the specifics, since I'm not that expereinced myself, but what you can do with LILO is install it to the boot partition of your Linux system.  I had an installation like that with a previous distro, and used a commercial boot loader (Acronis Disk Director) in the MBR to boot Windows or Linux.   (I never determined if this was necessary, but Acronis booted LILO, which in turn booted Linux.)

I just remember it was a choice during the LILO installation to install it to the Linux boot (or was it root?) partition.  Sorry I don't have the specifics.  Hopefully someone will notice your question hasn't been answered yet...

---

