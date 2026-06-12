---
title: "Accidentally installed Ubuntu inside C drive without creating a partition"
date: 2014-04-05
forum: Installation &amp; Upgrades
---

### Post by Timothy_Su on 2014-04-05
Hey guys. So I'm really really new to Ubuntu and did my very first dual boot with Windows 8 and Ubuntu 12.04 yesterday (and it worked great, btw :D). However, when i booted windows, I found out that i installed ubuntu inside my C drive (which is where windows is installed), in a folder named 'ubuntu'. I checked my disk manager to confirm and the partition I allocated for ubuntu was indeed empty.

I really don't know if uninstallation instructions on the internet work in my situation because most (if not all) are about ubuntus installed in a separate partition. Is there any way i can remove ubuntu from the C drive safely without affecting my existing windows files?

---

### Post by oldfred on 2014-04-05
Did you install wubi. If so that is similar to an application and you just un-install it like any Windows application. If it modified BCD and does not remove the choice from Windows you have to edit the Windows BCD file to remove the extra boot menu entry. Use Windows tools for all of that.

If you overwrote Windows, that is a bigger issue. Stop using hard drive, but you will not recover all of Windows, but may be able to recover some data.

Linux only installs to Linux formatted partitions which you cannot create from Windows. And if you create partitions with Windows it may convert to dynamic partitions which will not work with Linux and does not even work with some Windows repair tools.
Only use Windows partition tools to shrink Windows and immediately reboot, so Windows can run chkdsk and make repairs for its new size.

---

### Post by Timothy_Su on 2014-04-06
Thank you so much! :D Though I installed Ubuntu using Linux Live for the bootable usb, i checked Control Panel and ubuntu was simply installed like an ordinary app. Uninstalling it was a piece of cake and fixing the boot load thing was pretty easy too. :) Installing it again because ubuntu is awesome XD

---

