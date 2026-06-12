---
title: "Installation on a swappable IDE disk"
date: 2007-11-10
forum: Installation &amp; Upgrades
---

### Post by _guybrush_ on 2007-11-10
Hello,

I have Windows XP on hda, and I have a second IDE disk (slave), which is in fact a bay in which you can insert disks (not hot-swapable, the disk must be present at boot time). I was using the bay with a 200GB disk as a backup disk. Now I got a second disk for that bay, and I thought I could use it to install Ubuntu on it, which I did.

But I didn't pay attention to the GRUB location and left that option to the default setting (which I think is to write on the MBR part of hd0 (hda), i.e. the windows disk. I was wrongly presuming that all the information for GRUB would go on that disk, and that I would be able to boot without the linux disk in the bay (for example when I want to use the backup disk with Windows)
If hdb was not present, I expected to see the GRUB menu that would allow me to choose the OS to load, and I was thinking to get an error only if I chose ubuntu, because the disk is not present. Alas, hdb contains all the necessary files for GRUB, and I can not get the GRUB menu without the linux disk in the bay, which means that I can not use my backup disk with XP anymore.

What should I do?

I see two possibilities: 

-moving GRUB to the MBR of hdb, and change the bios settings to boot from it first. If there is no disk, or the unbootable backup disk, then the system would boot from the master IDE drive. In that case, I must rewrite the original windows XP master boot information in hda MBR. How do I do that?

-Is it possible to create a small partition on hda that would contain the grub files? In that case, booting can be kept on hda, and the grub files would always be accessible. I would be prompt with the menu and I would only get an error if I choose ubuntu when the ubuntu drive is not present.

Of the two possibilities, which one should I consider? The first one is more elegant, for It would only show me a boot menu when I can choose the OS. If only the XP disk is present, the XP would boot automatically.

Or do you have any other (and better) suggestion?

Thanks in advance for the help

---

