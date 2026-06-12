---
title: "Yet another GRUB error after upgrading to 12.04.1 LTS"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by ibates on 2012-11-05
There are so many combinations of problems concerning this aspect of the upgrade to 12.04.1 LTS that I thought I had best itemise this one also.

As was expected, after installing the upgrade (online), the first restart, instead of presenting the option to boot to Ubuntu or to Windows, it resulted in

"error : the symbol 'grub'xputs' not found
grub rescue> "

Neither 'grub-xputs' nor "grub rescue" means a thing to me.

Anyway, using the SuperGrub Disk, I was able to get into the newly installed Ubuntu and run 

sudo grub-mkdevicemap
sudo update-grub2
sudo grub-install /dev/sdX

And I now have a correct grub config file.

But the BIOS does not find the Ubuntu MBR (or any other MBR).  It keeps coming up with the same error message.

Being tricky, I changed the boot order in the BIOS to make the Ubuntu HDD (each OS has its own dedicated HDD), the first-to-boot deevice.  It worked a treat.  Straight into the GRUB page with the required Ubuntu and Windows options.

But then it all came unstick because there was no pointer (mouse) function available.  Ah!  These cyber mysteries!

So not being able to select anything at all in Ubuntu having no touch pad, I was forced to change the BIOS back to the original boot order and now I can boot up Ubuntu by going to the Boot Menu at BIOS level and selecting the Ubuntu HDD.

Although a very clumsy and time consuming method, this works well, but it is not the way it should work.

What am I doing wrong?  Why isn't the BIOS going to the Ubuntu disc as defined in the grub config file (and as it always did in Ubuntu 10.04 1 LTS)?

---

### Post by darkod on 2012-11-05
With multiple disks you have to be careful where you install grub, and to set BIOS to boot from that disk.

And as for the track pad not working, maybe it's not supported (very rare) or something got corrupt during the upgrade (that's why clean installs are always best).

Did you try 12.04 in live mode first to confirm the track pad and everything else works?

---

### Post by ibates on 2012-11-06
By running Boot Repair via its repository, the boot problem was repaired in about 60 seconds flat.

---

