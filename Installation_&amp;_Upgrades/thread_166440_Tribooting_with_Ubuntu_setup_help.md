---
title: "Tribooting with Ubuntu setup help"
date: 2006-04-26
forum: Installation &amp; Upgrades
---

### Post by cheetahman on 2006-04-26
Currently my system triboots with Windows XP,SuSE Linux 10 and Fedora Core 5.I am wondering if Ubuntu can format the Fedora Core 5 default partition and can be installed on the /hda instead of MBR since this is there SUSE and Windows XP are stored.Then for the Ubuntu bootloader has 

Ubuntu--goes to Ubuntu

SuSE Linux 10-goes to the MBR and gives the option SuSE Linux 10 and Windows XP

Windows XP goes to Windows XP

And it would use the same swap SuSE Linux 10 uses

---

### Post by Sef on 2006-04-26
> Currently my system triboots with Windows XP,SuSE Linux 10 and Fedora Core 5.I am wondering if Ubuntu can format the Fedora Core 5 default partition

Yes.  What I would do when I get to the partitioning is manual partition the disk.  Delete Fedora Core 5, then install Ubuntu on on the free space that was Fedora Core 5.  If you select the Ubuntu GRUB, it should detect Windows XP and SUSE Linux 10, so on boot you'll have the choice of what to boot into.  Ubuntu would be the default.

> And it would use the same swap SuSE Linux 10 uses

Yes, it would.

---

### Post by cheetahman on 2006-04-26
Does Ubuntu format LVM and ext3 partitions and can the GRUB bootloader be installed to hda.

---

### Post by hellfried on 2006-04-29
sorry for piggybacking here. i have been dualbooting ubuntu and winxp for the past few weeks but am now itching to try suse 10.0. is it possible for me to install suse and keep my current grub loader? it would be great if suse also pops up as an option in the grub. is there any option for that when i am installing suse?

---

