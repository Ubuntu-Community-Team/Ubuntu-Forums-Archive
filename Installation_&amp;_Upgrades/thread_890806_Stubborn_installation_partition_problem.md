---
title: "Stubborn installation partition problem"
date: 2008-08-15
forum: Installation &amp; Upgrades
---

### Post by rocketssss on 2008-08-15
I'm trying to throw Xubuntu on an older system, which is being stubborn. It is a 500Mhz, 256MB RAM machine with a BIOS that Ubuntu says is from 1999 and fails the ACPI cutoff (which is fine seeing as that only seems to disable sleep mode, which I didn't expect to work anyway). The system has been stubborn in that even when I tell it to boot from the CD, it still boots into Windows 98, so I used the Ubuntu Wubi installer to add a boot option, and I plan to turn it into Xubuntu later.

My problem is, it gets through the installation setup, then fails at 5% saying it failed to create the swap partition. I tried going to manual mode and having only one partition w/o swap space, but then it failed on creating the main partition. It sees my hard drive in auto mode (IDE3 13.6GB IBM-DJNA-371350), but can't partition it.

I found this was similar to this [thread]("http://ubuntuforums.org/showthread.php?t=857599"), and I followed the advice of using gparted before installation, but with the partition editor it cannot see my hard drive. Any ideas?

---

### Post by rocketssss on 2008-08-15
Oh, also - before entering the boot menu to boot into Ubuntu or windows, the Windows 98 start up screen appears briefly. Not sure if that matters.

---

