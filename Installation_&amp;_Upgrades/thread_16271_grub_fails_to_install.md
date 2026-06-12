---
title: "grub fails to install"
date: 2005-02-20
forum: Installation &amp; Upgrades
---

### Post by jacob on 2005-02-20
I'm trying to load Ubuntu on the same disk as XP. My first attempt it all loaded fine including grub. However, when I tried to boot into XP it hung after the chainloader +1 command. Messing about with sfdisk, fixmbr and fixboot didn't solve it, nor did setting the BIOS to read the disk in LBA (though I had probably messed things up irretrievably by then!).

After a few more attempted installs, I used the Seagate software to nuke my drive (low level format) and partitioned it as follows:
1) 1 GB for boot
2) 38 GB for WinXP (ntfs)
3) 20 GB for Ubuntu
4) 1 GB for Swap

I then installed XP again with no problem. I installed Ubuntu but it refused to install Grub. It did allow me to instal lilo instead. However, it now boots straight to Linux and doesn't give me a chance to boot into XP. 

If I run "lilo" I get:

Warning: '/proc/partitions' does not match '/dev' directory structure.
    Name change: '/dev/dm-0' -> '/dev/evms/hda1'
Added Linux *
Skipping /vmlinuz.old

Its all the tiniest bit frustrating. Any ideas on how I can get Grub to install, or else how to use lilo ? I've tried editing the lilo.conf file but without any sucess.

---

