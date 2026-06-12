---
title: "ubuntu after faulty debian"
date: 2005-05-31
forum: Installation &amp; Upgrades
---

### Post by anatole on 2005-05-31
Hi,
my partitions look like the following:
- hda
------ hda1 (Windows XP on ntfs)
- hdb
------ hdb1 - linux swap
------ hdb2 - debian on xfs
------ hdb3 and hda4 are storage partitions (one with ext3, one with fat32)

what i want is, to erase debian (it has some major faults since it was installed when my comp had ram problems so let's say it's unusable) and install ubuntu to its partition. 
in ubuntu install, i selected to reformat the hdb2 partition, and it seemed like ubuntu installer did it. i rebooted (at the part where the installer said to remove the cd and reboot, so ubuntu will boot and install some remaining packages), and _debian's lilo_ started up, with my previous settings. xp  loads now, but when i want to load Linux, some strange hybrid of debian and ubuntu loads... (and stops at the 50th line or something...) it's like the partition was not erased but debian remained there and ubuntu has installed itself on top of it... really strange. 
i would like to erase debian somehow and install ubuntu onto a pure partition. i attach my lilo.conf if it helps with anything. thanks for the help in advance.

---

### Post by kuleali on 2005-05-31
Try to wipe out the lilo boot loader an then install ubuntu.

---

### Post by anatole on 2005-05-31
[QUOTE=kuleali]Try to wipe out the lilo boot loader an then install ubuntu.[/QUOTE]
umm, how? the problem is, ubuntu install does not format the partition correctly.
if i wiped out only the lilo and the rest of debian remained, ubuntu's lilo would load the same hybrid linux which is unable to function.

---

### Post by anatole on 2005-06-01
solved. for some reason, it worked with the third try.

---

