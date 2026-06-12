---
title: "Installation on windows 7 and win xp computers"
date: 2011-06-14
forum: Installation &amp; Upgrades
---

### Post by Rich L on 2011-06-14
Hello, This is the problem i have with my installation of Ubuntu 11.04 on both pc's. I have an image using Acronis of both win xp and win 7 on two different pc's. I boot up the live cd and do an install of next to windows. The install will go as far as saying ready when you are then stops. If i re-boot from the hard drive it will boot to windows and not see Ubuntu. The partition and files are there for Ubuntu. Thank You for any help you might be able to give. The install of inside windows works fine.
 
Rich L

---

### Post by Herman on 2011-06-14
Does your BIOS have a setting called something like 'MBR write-protect' or 'boot sector antivirus' enabled? That setting is used to try to prevent Windows viruses from writing to the MBR. I have read that some Windows viruses do that so they can take over control of the PC at boot time and load before the antivirus. I have also read that they actually in some cases can even employ the antivirus and use it for their own mischievous purposes, but that's another subject. 
You may need to temporarily disable the MBR write-protect feature in your BIOS, it isn't needed for GNU/Linux operating systems, but you can re-enable it after Ubuntu (and GRUB) are installed if it makes you feel more comfortable.

Does your PC have more than one hard disk or do you have an external drive of some kind (USB or eSata etc) plugged in during your Ubuntu installation?
Due to vaguaries in the BIOS of some PCs,  it is sometimes possible for GRUB to end up being installed in the MBR of a non-first hard disk. If you think that could be a possibilty, you might try booting with your BIOS boot menu to see if you can boot from some other drive.

Another possibility to think about is whether or not your PC might have some kind of non-standard MBR that the Ubuntu installer is detecting and not wanting to write to. (I'm not sure if there are actually any safety features like that built into the Ubuntu installer, as far as I know the user needs to be careful, but it would be conceivable that such a feature would be a nice thing for an installation CD to have built in). So, if you have some kinds of RAID or LVM or Entire Disk Encryption or some special kind of MBR replacement or enhancement then I'm not sure and would need to do some testing first before being confident to give any advice. It would be best to check first before disabling the MBR write-protection in your BIOS, (read your PC manufacturer's documentation).

It's normally best to install GRUB to MBR in your first hard disk in 99% of PCs, but you can also choose to install GRUB to some other disk if you want, like a non-first hard disk or removable USB drive. The MBR of the first hard disk is normally best for most PCs and suits most users, (results in the most convenient way to dual or multi boot).

---

### Post by Herman on 2011-06-14
I forgot something.

There's no need to re-install Ubuntu just to install GRUB.

If you have the full Ubuntu operating system installed in your HDD, you should be able to do it more easily from a Ubuntu Live CD or USB.

All you need to do is boot your Ubuntu CD or USB, mount your hard-disk installed Ubuntu partition, and run the 'grub-setup' command from terminal.

---

### Post by Rich L on 2011-06-14
Thank You Herman for all your help and information. I found out what the problem was. I needed to use a password from the menu to finish the install. When i put in a password the finish was highlighted and i could continue with the install. It is all good now.

---

