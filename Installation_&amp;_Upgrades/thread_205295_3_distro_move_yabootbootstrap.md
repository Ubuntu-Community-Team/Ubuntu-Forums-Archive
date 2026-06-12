---
title: "3 distro move yaboot/bootstrap"
date: 2006-06-28
forum: Installation &amp; Upgrades
---

### Post by Uta on 2006-06-28
I have 3 distros, 2 are on my iBookG4 (Mac OS X and Ubuntu dapper) and the third is on my attached firewire drive (Kubuntu dapper). Everything works perfect, wifi, printers etc... but the issue is I installed to the FW HD last and when the installer installed the bootloader it of course installed it on the firewire drive. The problem with that is if I unattach the FW HD to be mobile with my laptop, the system has lost it's bootloader, so the question is how do I move it back to the laptop HD where it was as a dual boot previous. By previous I mean, the bootloader was on the Ubuntu partition (hda4). Thanks in advance to helping me move the bootloader!

---

### Post by Uta on 2006-06-29
Ok, I foraged ahead  and I now have my bootloader back on my iBook's main HD with the 3 boot options that had been called (previously) from the FW HD. 

I copied the FW HD boot information (boot info only for the FW HD)
and added it to my previous yaboot.conf that was on my iBook's HD, and from the terminal "sudo ybin -v" got my blessing, restarted and my issue was solved. Now if I don't have my firewire HD attacted my iBook can still boot.

---

