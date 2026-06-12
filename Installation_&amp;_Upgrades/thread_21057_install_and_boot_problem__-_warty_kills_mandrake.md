---
title: "install and boot problem  - warty kills mandrake?"
date: 2005-03-20
forum: Installation &amp; Upgrades
---

### Post by alainhenry on 2005-03-20
I just bought a new PC, ASUS motherboard P4P800S-X, Maxtor 120Gb HD, and have troubles with the installation process.  

I installed first win98 (on hda1), then Mandrake (on hda6), using lilo as bootloader on the MBR.  Went fine.  Then I installed Ubuntu, setting GRUB in the root of ubuntu (hda8).  After that, the boot process is corrupted, instead of the lilo start menu, I have just the letter L showing on the black screen (obviously, the first letter of Lilo).  During the ubuntu install, I asked to have the mandrake partition mounted (without formating!) to /distro/mdkroot.  It did not do it, telling me it could not recognised the partitiopning otr something like that.  

Now, even with a GRUB floppy disk, i can't start the mandrake system, it freezes when I issue the command root (hd0,5).  

And now, Ubuntu refuses to install, telling me it can't install the kerbnel package, but that's another story I assume.  (I'll make a new CD with a fresh download to be sure, and yes I checked the Md5sum).

I hope this is clear...  Any suggestion would be appreciated.  

Alain

---

### Post by Xian on 2005-03-20
I would try seeing if you can chroot into your Mandrake partition using a LiveCD, and then perhaps from the command line re-install the bootloader. I've done that in SUSE a few times over a botched effort on my part. I don't know Mandrake but hopefully it has a similar type of functionality.

---

### Post by alainhenry on 2005-03-22
I tried reinstalling the boot loader (grub) from Ubuntu, but result is the same.  Viewing other threads, it seems that Ishould turn HD access to LBA instead of AUTO in the BIOS.  but my bios only proposes an Auto mode, I can't force LBA manually... 
I think I'll try to install ubuntu with Lilo, or better, wait until Hoary gets out.  

Alain

---

