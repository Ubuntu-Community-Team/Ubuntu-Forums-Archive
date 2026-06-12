---
title: "Dual booting two Ubuntus"
date: 2013-07-08
forum: Installation &amp; Upgrades
---

### Post by itlarson on 2013-07-08
I have an old computer that has Kubuntu 8.04 installed on an IDE hard drive.  I put a new SATA drive in it, and installed Xubuntu 12.04 .  I intend to eventually use the Kubuntu drive for backups, but for now I want to dual boot.  To complicate things this computer won't allow a SATA drive to be ahead of the IDE drive in the boot order.  Kubuntu 8.04 can't read ext4, 12.04 can't be booted if the old drive is present, and the old IDE drive can't be hot plugged.  The result is a catch-22 that makes it impossible to transfer data between the two drives.  I need to put grub 2 on the IDE drive, and set it up so that I can still boot 8.04 if I need to.  Can someone walk me through setting this up?

---

### Post by itlarson on 2013-07-08
OK- Obviously I can copy data from the live CD, but I still would like to be able to dual boot.

---

### Post by fantab on 2013-07-08
Now how 'old' is this laptop? what are its hardware specs?
I am sure you are aware that 8.04 has been long dead. There are no Updates and no Support for it anymore. Get rid of it an install any supported version, like 12.04, 12.10 or 13.04.

Why can't you get rid of the IDE disk and use only the SATA disk? I hope someone comes along with a solution for your catch-22 situation. Meanwhile try unplugging IDE drive, then with on SATA plugged in change the Boot priority to boot SATA first then replug the IDE and see if the set boot priority sticks.

Good Luck.

---

### Post by oldfred on 2013-07-09
Can you even boot from the SATA drive? Some old systems only boot from the IDE drive and the SATA is for data only. Some of those were SATA1, but just about everything with SATA is SATA2 or new systems SATA3.

---

### Post by itlarson on 2013-07-20
Ok- I thought I should follow up.  

First about the computer: It's an old AMD Sempron desktop.  It has two SATA connectors, and is perfectly capable of booting form a SATA drive.  However, if an IDE drive is present, there is no way to move the SATA drive to the top of the boot order, and it will never show up as /dev/sda.  

So, I decided I wanted to try a different distro on this machine.  When I did the reinstall I decided I was willing to risk the Kubuntu installation, and picked /dev/sda (the IDE drive) as the boot drive.  When I rebooted, I discovered that the installer had set grub up to dual boot all on it's own.  Problem solved.

---

