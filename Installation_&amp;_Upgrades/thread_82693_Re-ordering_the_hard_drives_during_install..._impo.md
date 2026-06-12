---
title: "Re-ordering the hard drives during install... impossible??"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by hostile on 2005-10-27
Hello everyone,

I have been banging my head against the brick wall which is the Ubuntu installer.

I am trying to install to a system with 5 hard drives:

1) Boot drive on an Adaptec 29160
2) 2 x 120 GB on a vanilla Promise ATA 133 controller (Linux software RAID)
3) 2 x 250 GB on the motherboard's Intel ICH5 SATA controller (Linux software RAID)

Here's the issue:

The BIOS orders everything like it should:

IDE, SCSI, SATA

I then disable booting from IDE in the BIOS, and change it to SCSI. The BIOS on this board will actually identify each hard drive separately, so you can choose which to boot from.

The Ubuntu installer, however, for some asinine reason identifies the drives in a completely backwards order!

So my SCSI drive which should be /dev/sda is labelled as /dev/sdc in the installer!!

Red Hat 9 and all derivatives thereof actually have an option when configuring the boot loader to re-order the drives, so you can put /dev/hda ahead of /dev/sda, thereby changing your device.map for you.

How can I do this with Ubuntu during install??

I came over to Ubuntu a few months ago from the Red Hat world after installing Ubuntu on my latop, falling in love with it, then building a couple of servers with Ubuntu.

This whole process is frustrating me, and turning me off *very* quickly.

Does anyone know how I can work around this issue? I don't want to go back to RPM hell...

Thanks in advance,

 - Lance

---

### Post by hostile on 2005-10-27
Well, after much research, it would appear this is a major failing of the Debian installer.

Here's my solution:

[http://www.ubuntuforums.org/showthread.php?p=446812#post446812](http://www.ubuntuforums.org/showthread.php?p=446812#post446812)

---

### Post by hostile on 2005-10-27
OKAY... 

I'm ready to tear my teeth out here...

It would appear that after a kernel upgrade, things go RIGHT BACK to where they were...

SO, you need to apply my method each time you upgrade the kernel. That is a bloody JOKE.

Still, this seems to be the only way around this problem for now.

I think I'm about to file my first bug report EVER.

---

### Post by hostile on 2005-10-27
Upon further inspection... the root of the problem is still not fixed...

Yes, you can re-arrange grub to see your SCSI drive as hd0, but the system itself still sees my SCSI boot drive last in the chain (/dev/sdc).

So now I have to figure out how to force the OS to see /dev/sdc as /dev/sda.

If anyone knows how I can do this... please let me know.

---

