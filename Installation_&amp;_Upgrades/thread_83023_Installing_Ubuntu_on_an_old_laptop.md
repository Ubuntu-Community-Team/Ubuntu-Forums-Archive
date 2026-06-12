---
title: "Installing Ubuntu on an old laptop"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by denkedran on 2005-10-27
Ok. This is the Situation.
I have an old dell-laptop. There is the possibility in Bios to boot from cdrom. But i can't change the boot-order cause of an existing admin password I don't know.
Order is: Floppy,HD,CDROM
I installed smartbootloader an a floppy and bootet, installed the bootmanager on mbr of hd and rebootet. Bootmanager comes up but when I try to boot from CD which is listed, it gives me an error. ( error 0xaa )
when i remove ther harddrive and boot the ubuntu setup comes up and i could install if there was a harddrive.
could i use loadlin or any other bootmanager i don't know of ?

thanx

---

### Post by jasmuz on 2005-10-27
Check this out: [https://wiki.ubuntu.com/Installation]("https://wiki.ubuntu.com/Installation")

---

### Post by az on 2005-10-27
1.  Can you open the laptop and set the jumper to clear the password?

2.  You can write SBM (Smart Boot Manager) onto a floppy and boot the floppy.  SMB is in /install on the cd...

README.sbm

About the Smart Boot Manager image
----------------------------------

  The file `sbm.bin' that is available in this directory may be useful
  to you if you are not able to directly boot the first CD because your
  BIOS may be too old and may not support ISOLINUX.

  Then, instead of booting on the CD directly, you create a Smart Boot
  Manager floppy image by using the sbm.bin disk image. You can create this
  floppy with rawrite (under DOS) or with dd (under Linux). Now you can
  boot on this floppy disk and it will detect your CDROM and let you boot
  on it bypassing any BIOS limitation.

What is SBM ?

  Smart Boot Manager or briefly SmartBtmgr (SBM), is an OS independent
  Boot Manager - a program that is loaded by the bios before any
  operating system and allows you to choose which operating system to
  boot.

  SBM is included in Debian in two ways, the package bmconf allows us to
  install and configure an old version of SBM and sbm wich is the latest
  version of SBM with an installer.

What's the use of SBM on the CD then ?

  SBM includes an IDE driver that allows us to boot the cds even on
  machines with a BIOS that wouldn't support booting from CD, provided our
  CDROM is an IDE one, that is, so you can make a SBM floppy and boot from
  it and then tell it to boot from your CDROM.

  Also, there are some cases where the BIOS would allow booting from the CD
  but isolinux fails to boot from there, in this case you can either boot
  using a CD other than the first, as the others don't use isolinux, or you
  can make a SBM floppy and boot from this floppy and then tell SBM to boot
  your CDROM.

How do you make a SBM floppy ?

  If you have SBM installed on a box you can run sbminst. Otherwise you can
  put the sbm.bin floppy image that we provide with our cds onto a floppy
  just like you would do with a rescue image.

---

### Post by denkedran on 2005-10-27
[LIST]
[*]i already installed smb on a floppy.
[*]i booted with it.
[*]installed on harddrive.
[*]shutdown
[*]put my cdrom into the laptop instead of floppy ( they can't be inside a the same time)
[*]booted
[*]within smb i choosed cdrom with ubuntu breezy inside --> error 0xaa
[/LIST]
you could say, the cdom is corrupt or my bios can't recognize my drive or the medium, but like I said above, when i remove the harddrive, booting from cdrom works fine, and the ubuntu-installer starts. :confused:

---

