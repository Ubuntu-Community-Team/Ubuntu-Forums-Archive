---
title: "How to cleanup mess after two installations of 22.04"
date: 2022-05-03
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2022-05-03
Please see output of GParted shown in the attachment.  Original 22.04 installation is on sda12.  How best to remove.  Ubuntu Unity 22.04 is on sda13.  I want to keep that.  Main data file is on sda5.  I want to get rid of sda/6 and merge sda5 with sda10. Everything else can remain the same.  According to Grub, the first line goes to the original installation of 22.04 on sda12.  

Windows 10 Pro is on the ntfs partitions.  I need to keep that for clients who want to see my reports only in Adobe Acrobat DC and/or MS PowerPoint.

Thank you in advance.  All help will be appreciated.  

John

---

### Post by ubfan1 on 2022-05-03
I see an extended partition, implying MSDOS partitioning, implying legacy Windows.  I see an EFI partition in a logical partition, not even sure that will work when not a primary.  How are your Ubuntus installed? Should be legacy to match Windows.  If both your new Ubuntu and Windows in legacy mode, just boot the new Ubuntu and grub-install -- Should pick up Windows, and release all grub dependency upon the old Ubuntu.

---

### Post by cigtoxdoc on 2022-05-03
Thank you.  Getting to Win 10 Pro is not a problem.  It shows in the grub menu on sda2 as expected.  I am using it to write this reply.  Indeed, Win 10 Pro was the original OS on this PC and was installed from a thumb drive purchased from MS.  Ubuntu was added somehat later.  The FIRST problem I need help with is getting rid of the original 22.04 installation.  It is on sda12 and shows in the first line of the grub menu.  The only Ubuntu I want to keep is Ubuntu Unity on sda13.  The SECOND problem is "cleaning up" the ext4 partitions as, for example, sda9 is empty.  I would really appreciate some step-by-step help on this.

John

---

### Post by ubfan1 on 2022-05-03
Step one, (well step 0 backup everything), boot the sda13 root, which should be offered on the grub from sda12.  If sda13 is not on the existing grub boot menu, maybe sda13 was installed after the last sda12 grub.cfg update, so run sudo update-grub from sda12 root -- that should find the sda13 install and add it to the grub boot menu. Now reboot, select the sda13, and from there, run grub-install.  That should change the grub to boot from sda13, with its grub.cfg, putting the sda13 root ubuntu first in the list.

---

### Post by cigtoxdoc on 2022-05-03
Thank you very much. Run grub-install wants a destination name.  Currently, grub is on \boot (according to nemo files).  Is that the correct?  BTW Ubuntu Unity was already on the grub menu, just not at the top.

If I can get Ubuntu Unity at the top of grub, how to I get rid of the old 22.04 installation on sda12?

John

---

### Post by ubfan1 on 2022-05-03
I think sudo grub-install /dev/sda should work to set up a legacy boot, assuming the grub-pc package it the one installed and not the grub-efi one for UEFI.  No additional options needed, the defaults are all good for you (/boot/grub is the default location for grub files).  See that the first ubuntu from sda13 is at the top of the /boot/grub/grub.cfg menu item list. Reboot to ensure it works.  If there's nothing you want (all backed up) from sda12, you may simply format and run sudo update-grub (which rewrites the grub.cfg file) to get rid of the unwanted boot to sda12. Posting this before I lose it (again).

---

### Post by ubfan1 on 2022-05-03
On the reparttioning, if you can first copy everything you want off sda6 and sda10 onto sda5, you can simply then delete the 6 and 10 partitions and grow the sda5 partition to the right.  gparted (?) then runs the resize2fs to increase the filesystem size on the new, larger sda5.  If your partitioning tool does not grow the filesystem size for you, you can run resize2fs yourself. Left moves/growth is much harder.

---

### Post by cigtoxdoc on 2022-05-03
Thank you again for your help.  Here is what the grub menu looks like (just with boot lines)
Ubuntu (the one I want)
Windiws 10 on sda1 (don'use as it give garbage)
Ubuntu 22.04 LTS on sda10 (crashes then goes to Unity logon
Ubuntu Jammy Jellyfish (development branch) (22.04) on sda12 (this works)
Windows 10 on sda 2 (this works)

So, it looks like sda10 and sda12 can be reformatted.

BTW, all my real data is on other partitions.

John

---

### Post by cigtoxdoc on 2022-05-03
Thanks to all for your help.  This prtoblem is now solved.  Thank you to ubfan for his step-by-step instructions.  Grub menu is now normal for a dual-boot installation of Ubuntu Unity and Windows 10 Pro.  Everything works.  I also used GParted to expand one partition where more space was neeed.

John

---

