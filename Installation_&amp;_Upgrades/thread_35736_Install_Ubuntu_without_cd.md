---
title: "Install Ubuntu without cd"
date: 2005-05-20
forum: Installation &amp; Upgrades
---

### Post by CrustyDOD on 2005-05-20
Question/problem is connected with this topic: [http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948)

How on earth do you edit boot.ini in Windows 98 if there is no boot.ini file?

Trying to install ubuntu (server) on some old machine where there is a CD-ROM but its not bootable, floppy is hardly working... but lan is working and it has Win98!

my editing/trying ended here: **B) ~ editing the boot.ini**

Inserted that line (C:\grldr="Start GRUB") into autoexec.bat, msdos.sys and system.sys and nothing happens.. invalid command is the output.. tried running grldr command in dos, unknown command..

Basically i want to install Ubuntu over win98, not on some different partition as i don't need win98, what a shock eh :) But how do i start Grub?!?

I think i just rode into dead end.. help wanted..

---

### Post by Zelut on 2005-05-20
Any reason why the CDROM isn't bootable?  Is that not an option in the BIOS to set the CDROM as bootable?  I'm not sure of any options to ask the installation to install over a network, but you may take a look.  If you press F1 (I believe) at the install prompt it'll give you additional options.

Also, you wont be able to run GRUB from a windows command like that.  GRUB is loaded into the MBR of the HDD & simply gives an option to which partition to boot into.  Its not going to resend you to ubuntu once you're in windows.

My best guess would be to check out the BIOS (usually DEL, F1 or F2 at first boot).  There will be boot options and there shouldn't be any reason you can't move the CDROM to the top of the list to boot before the HDD.

---

### Post by CrustyDOD on 2005-05-20
Stupid me!
It's Pentium 1 200Mhz and i fool though that it's not possible to boot from cd..

Changed it in BIOS and now it boots from CD..

thx!

---

