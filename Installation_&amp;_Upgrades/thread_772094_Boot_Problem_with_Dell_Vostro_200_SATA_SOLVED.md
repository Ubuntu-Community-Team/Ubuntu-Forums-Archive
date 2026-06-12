---
title: "Boot Problem with Dell Vostro 200 SATA SOLVED"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by haz2a on 2008-04-28
I just installed Ubuntu 8.04 Hardy (LTSP Server) on to a Dell Vostro 200. The installation went OK but then it wouldn't boot from the hard disk.

I then tried to boot Knoppix 5.1.1 and that failed too saying "Can’t find Knoppix filesystem...". I found the fix for this was to use the boot options 'linux all-generic-ide irqpoll'. I then used Knoppix to edit /boot/grub/menu.lst in Ubuntu on the hard disk, and added just 'all-generic-ide' to the 'kopt' line, and to the 'kernel' line in the default (top) kernel entry. Ubuntu then booted OK.

Finally, from Ubuntu, I did  'sudo update-grub' to fully update grub.

Some other threads suggest changing the BIOS SATA Mode to RAID, but I just left it at IDE since I'm not using RAID.
See also: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/153702)

---

### Post by rom_zzz on 2008-09-03
Just in case, one might want to have a look at a deeper analysis of this issue [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635").
Also, the kernel option to add is all_generic_ide, with "_" instead of "-"

---

