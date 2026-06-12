---
title: "Regression detected! Cannot complete installation with software RAID 0 with beta 1!"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by RJARRRPCGP on 2010-03-26
After telling the alternate installer to write the changes, I got a message claiming the kernel couldn't reread the disk possibly until reboot and then it claimed the mounting of sda3 failed, IIRC.  (the swap partition) 

Then when it offered to go back to the partitoning menu, it froze at "Detecting file system". (or similar message)

This is even when the CD checking passed and even when I created a /boot partition on sda1.

Anyone else having this problem.

Beta 1 should have been delayed to fix the partitioning problem.

---

### Post by NCLI on 2010-03-26
No, it should not. The entire point of a beta is to have more people testing and finding regressions like this. Have you reported a bug?

---

### Post by RJARRRPCGP on 2010-03-26
> **NCLI said:**
> No, it should not. The entire point of a beta is to have more people testing and finding regressions like this. Have you reported a bug?

I'm gonna try to. In fact, it seemed to give a message about the attempt to mount the swap at mountpoint "none". (Like it's not even formatting when it's supposed to!) Seems to fail on format. 

Concerned, because this is a beta for an LTS!

Also concerned, because this is with the alternate installer!

---

### Post by nanog on 2010-03-26
Known bug. Its in the beta1 release notes and is targeted to be fixed in beta2.

---

### Post by RJARRRPCGP on 2010-03-26
OK, just made a bug report on the debian-installer package, because this is with the alternate installer.

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/549258](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/549258)

---

### Post by Eclipse. on 2010-03-26
> **RJARRRPCGP said:**
> OK, just made a bug report on the debian-installer package, because this is with the alternate installer.

[https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/549258](https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/549258)

Its been fixed already, see:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/527401](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/527401)

---

### Post by RJARRRPCGP on 2010-03-27
[COLOR="Red"]!! I'm not even at the GRUB installation stage when the error occurs. !![/COLOR]

---

