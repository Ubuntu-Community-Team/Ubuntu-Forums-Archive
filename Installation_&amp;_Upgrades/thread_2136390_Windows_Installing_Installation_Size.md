---
title: "Windows Installing Installation Size"
date: 2013-04-17
forum: Installation &amp; Upgrades
---

### Post by isaac7 on 2013-04-17
I am making the switch from Windows Vista to Ubuntu.  I downloaded the windows installer but it is asking me for an installation size.  Once I install Ubuntu I am planning to delete Windows entirely.  From what I understand this is the hard drive space that is saved for Ubuntu? Can I change this to be the whole hard drive once i install Ubuntu?

---

### Post by Cheesemill on 2013-04-17
You can't use the Windows installer if you want to be able to remove Windows after you have installed Ubuntu.

This is because Wubi (the Windows installer) doesn't do a normal installation of Ubuntu, instead it installs it into a file on the Windows drive. If you then remove Windows you remove Ubuntu as well.

Instead you should do a normal installation of Ubuntu by downloading the iso file from [here]("http://www.ubuntu.com/download/desktop") and following the instructions to burn this image to a DVD/USB. You then restart your machine and tell it to boot directly from the DVD/USB.

If you are sure that you don't want to keep Windows and you have any important data backed up then you can just select the 'Use entire drive' option in the installer and it will delete the Windows partitions from your drive and install Ubuntu using the entire drive.

---

### Post by fantab on 2013-04-17
> **isaac7 said:**
> I am making the switch from Windows Vista to Ubuntu.  I downloaded the windows installer but it is asking me for an installation size.  Once I install Ubuntu I am planning to delete Windows entirely.  From what I understand this is the hard drive space that is saved for Ubuntu? Can I change this to be the whole hard drive once i install Ubuntu?

I would advice you NOT to Delete Windows just yet. Instead Dual-Boot both, Windows and Ubuntu, until such time that you are throughly comfortable with Ubuntu. Otherwise you might get frustrated. Keep Windows for now but Boot Ubuntu.

By Dual-Boot I mean "true" dual-boot and NOT booting with WUBI. [Instructions Here]("https://help.ubuntu.com/community/WindowsDualBoot"). Also [Here]("http://www.liberiangeek.net/2012/10/dual-booting-windows-7-and-ubuntu-12-10-quantal-quetzal/").

---

