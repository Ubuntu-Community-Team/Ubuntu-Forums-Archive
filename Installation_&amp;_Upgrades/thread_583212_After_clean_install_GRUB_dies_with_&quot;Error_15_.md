---
title: "After clean install: GRUB dies with &quot;Error 15: File not found&quot;"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by matthias_k on 2007-10-20
Just made a clean install of Gutsy and on the first boot GRUB welcomes me with some cryptic error code (Error 15: File not found).

[rant on]
If that is where Ubuntu is heading in terms of usability, then boy, this is the wrong direction people
[rant off]

I installed Gutsy to sda1, but in the boot options it says: root (hd1,0). As I understand hdX are the IDE devices, but it installed to an SCSI device (which is pretty weird, since I don't have any SCSI devices). Maybe that is the problem? Or maybe they screwed up the filename for the kernel image?

Would be great if someone can help. Stuff like this just pisses me off. How can they screw up so bad on something as essential as the bootloader? I was really impressed by the release candidate live DVD, but this is just weak.

---

### Post by matthias_k on 2007-10-20
Okay, I fixed the problem by correcting the root device and partition to hd0,0. Obviously Ubuntu incorrectly mapped /dev/sda1 to the second hard drive, which is hd1.

It's also obvious that a less seasoned Linux user would have never figured out what's wrong. This demands immediate fixing!

If you happen to have the same issue, hit "e" to edit the boot command, fix the root partition parameter to match the partition where you installed Ubuntu, and then hit "b" to boot with the new setting. After Ubuntu has booted, go to /boot/grub and edit menu.lst and set the "groot" parameter to the same value so it won't happen again. After saving the file run "update-grub" as root.

---

### Post by ToyotaDiesel on 2007-10-20
Thanks.  I had same issue.

I have 4 IDE drives, 2 scsi.  I installed the OS on one of the SCSI drives, but apparantly Ubuntu became confused at some point...

I changed to hd0,0 and it is booting now.  thanks.

Using Ubuntu 7.1 btw.

---

