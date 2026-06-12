---
title: "Uninstalling from within vista"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by Brennagan on 2008-10-01
I installed ubuntu as a program within vista to see what it was like and then tried to uninstall it through the change/add programs and the uninstall in the folder in program files, it seemed to work and the files are gone but my MBR still shows Ubuntu butt fails when i click it. I have super grub disk but that seemed to mess it up even more unless someone else knows how to do it? Thanks in advance

I did something with super grub disk now i always have a "test memory" "test system" and exit thing when trying to boot no operating systems no nothing

---

### Post by Brennagan on 2008-10-01
anyone?

---

### Post by Mark Phelps on 2008-10-01
Looks like WUBI overwrote the MBR when it installed Ubuntu and failed to restore the original version when it was uninstalled.

You could do a forum search on WUBI and see if anyone else has figured out how to solve this problem, but barring that, you'll have to do a 'startup repair" of Vista by booting from your Vista DVD.  You DO have a Vist DVD, right?

Unfortunately, MS is not very forthcoming about the details in their new boot process or in the changes they have made in NTFS for Vista.  Thus, tools not specifically written for Vista (Gparted, SystemRescueCD, SuperGrubDisk) have various degrees of success or failure when tampering with Vista stuff.

---

### Post by Brennagan on 2008-10-01
i do have the vista disk and tried startup repair but it doesnt seem to really do like anything. am i doing something wrong?

---

### Post by xj0hnx on 2008-10-05
Have you tried using EasyBCD to remove the entry?

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

