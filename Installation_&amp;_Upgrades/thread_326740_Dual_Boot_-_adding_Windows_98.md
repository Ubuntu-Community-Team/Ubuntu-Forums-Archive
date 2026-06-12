---
title: "Dual Boot - adding Windows 98"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by rossnixon on 2006-12-28
I want to have a Dual-Boot system: Windows 98 & Ubuntu.

Ubuntu 6.10 is currently installed and running well. The 2nd, 3rd and 4th partitions are ext3 and I'm using GRUB.

I want to install DOS (from Windows 98 ) on the 1st partition (FAT32) which is currently empty. I guess I will need to run FDISK to make the 1st partition active. **Will the partition table still point to my ext3 partitions?**

Then I will install a slave drive and xxcopy my old Windows 98 installation over. Then SYS c: should get it going.

I found these instructionss [http://doc.gwos.org/index.php/Restore_Grub](http://doc.gwos.org/index.php/Restore_Grub).  Does this also work for Ubuntu 6.10? If it does, I should get Ubuntu booting up OK - but then how do I add Windows 98 as an boot option?

---

### Post by kidders on 2006-12-28
Hi there,

You seem to have acted with great foresight, leaving your boot disk's first partition available for "fussy" operating systems. :-) I'm not altogether sure what you mean by "point" to your Ext3 partitions though.

Your plan sounds like it should work. Once you've tweaked the "active" flag and copied over your Win98 system, you can reinstall your bootloader with an extra option for Windows. Depending on which one you're using, you can Google for specific instructions, but it's straightforward.

**Edit:** How about re-labelling this thread "How to install Windows and only have to reboot once" lol.

---

### Post by rossnixon on 2006-12-29
Well, that was rather easy!
FDISK ( from Windows 98 ), format c: and sys c: did no damage whatsoever,
so GRUB ran and loaded Ubuntu.
Note: FDISK did not see the partition order correctly, and got the size of one wrong.

I had to add Windows 98 as a boot-up option by manually editing /boot/grub/menu.lst (is there meant to be a GUI for this?)

I also had to mount my fat32 drive by editing a file (can't remember which one).
Does everyone else have the "Administration > Disk" option visible?  I don't :-(
Any clues on fixing this?
UPDATE: (I found this alternative program) sudo apt-get install pysdm

---

### Post by kidders on 2006-12-29
> **rossnixon said:**
> I had to add Windows 98 as a boot-up option by manually editing /boot/grub/menu.lst (is there meant to be a GUI for this?)I imagine there are a few, but you did it the way I would have. :-) Far quicker.

---

