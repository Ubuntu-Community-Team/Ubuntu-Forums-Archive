---
title: "Cannot Boot In To Ubuntu"
date: 2011-09-29
forum: Installation &amp; Upgrades
---

### Post by LegoAddict on 2011-09-29
I have a computer with two hard drives.  Windows was already installed on one when I installed Ubuntu.

The first time I tried (11.10 Beta 1) it screwed everything up (I partitioned manually and set the bootloader manually, which made me unable to boot in to any operating system).  I wiped everything and reinstalled Windows.

This time, I used the "Install Alongside Windows" option.  Everything went well except that Ubuntu does not appear as an option in the (non-existant) boot list.  Neither MBR nor GRUB show their faces.

How can I get Ubuntu to show up?

---

### Post by Idefix82 on 2011-09-29
What hard drive did you install Ubuntu on? I suspect that Grub was installed on the second hard drive, while BIOS first looks in the MBR of the first drive. Since it finds a valid boot loader there (the windows one), it never checks the second drive. Try changing the boot order in the BIOS and see if that brings up the grub menu.

---

### Post by LegoAddict on 2011-09-29
So I believe you're right, but I've come up against another snag:  The BIOS doesn't recognize the 500GB drive I have Ubuntu installed on as bootable.  It's there, the boot flag is on, but it doesn't appear in the boot menu.  How might I go about fixing this?

---

### Post by Idefix82 on 2011-09-30
That depends on your BIOS. Normally, the bios shouldn't even care whether anything is installed in the MBR of the drive. That's checked during startup, not during bios configuration.

You have two options: either open the computer and swap the connectors of the hard drives, or (and I would rather recommend that) install grub in the MBR of the first drive. Ubuntu itself can still be on the second drive. Googling will give you tutorials on how to install grub (note that this is grub2, so don't follow old tutorials).

---

