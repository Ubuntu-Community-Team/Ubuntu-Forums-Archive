---
title: "Can't load Vista after installing Ubuntu"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by ali999 on 2008-04-03
Hi
I recently installed the new Ubuntu 8.04 Hardy Heron beta version to dual boot with Vista already installed. The two operating systems are installed on separate hard disks.Ubuntu runs fine but at first, Vista would not show up in GRUB, so I edited my menu.lst file to detect the disk containing Vista and got that to show up. But now I get an error saying NTLDR cannot be found, and can't load up Windows anymore. I'm thinking this is because my Vista was installed in the hard disk designated as F:/, and the second hard disk that windows had called C:/ is what I reformatted to install Ubuntu. I'm thinking that because windows assumes that C:/ is going to be your system drive, it installed some of its boot files in there. Is there anyway of fixing this without having to reformat? 
Thanks in advance.

---

### Post by darolu on 2008-04-03
If you are sure Windows installed the nt loader in the hard drive "C", and you installed Ubuntu in it, the file was deleted.
Theorically you can manually copy the nt loader on your HD "F", you will also need boot.ini there; just find another Vista computer and copy the file on a memory flash and paste it in your F disk, same if boot.ini is missing, this should fix it.

---

