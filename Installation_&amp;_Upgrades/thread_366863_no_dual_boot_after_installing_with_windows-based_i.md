---
title: "no dual boot after installing with windows-based installer"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by gippo333 on 2007-02-21
Hi. I have a laptop pc with windows xp installed. I wanted to install ubuntu from windows because my cd-rom drive doesn't work very well. 
I launched the installer from [https://blueprints.launchpad.net/ubuntu/+spec/windows-installer]("https://blueprints.launchpad.net/ubuntu/+spec/windows-installer")
, the installation procedure worked well but after the rebooting there was no dual-booting. The system started as usual with windows xp, as if I didn't install ubuntu. I tried to re-launch ubuntu installer but it said me that the system was already installed. I rebooted several times with the same result.

Any idea?

---

### Post by logos34 on 2007-02-21
Never tried installing that way, but i'm thinking there's a possibilty that grub is installed (either  to the mbr or root, but for some reason it is defaulting to windows and the timeout is set to 0 (in which case you won't see grub menu at all before it chainloads windows).  Or something went wrong and grub didn't install at all.  

If you have a floppy drive (even usb) you could get SuperGrub and put it on a diskette.  That should get you into ubuntu and restore grub.

---

### Post by Bakerconspiracy on 2007-02-21
It seems as if the boot loader didn't install, the windows boot loader is still installed on the MBR (master boot record). You need to look up "installing grub" in the forums and follow the instructions.

Edit: Even if grub was set to 0 you would still have a second to press escape. (I have it set on 0, and I dual boot)

---

### Post by logos34 on 2007-02-21
then maybe 'hiddenmenu' is enabled (no #) AND timeout is set for 0, in which case all you'll see 'Grub loading stage 1.5' blip on the screen before it loads windows

---

### Post by Jouke74 on 2007-02-22
Usually Grub is installed in the MBR of the first harddisk. If it is somewhere else, then please specify where.

If you have two harddisks (bit strange in a laptop) and grub is installed on MBR of the wrong non-booting disk, then change the boot order of your disks in your BIOS en turn them around.

Other problem could be that the MBR of your only HD is protected by the BIOS virus protection. Therefore Grub failed to install. Then turn off the protection and reinstall Grub.

---

### Post by tuxcantfly on 2007-02-25
edit your C:\boot.ini and make sure that timeout is set above 0 sec. and that the last line says:

C:\grldr="Ubuntu"

don't go by the other instructions to install grub to the mbr; the windows-based installer uses grldr, not grub, as the bootloader

---

