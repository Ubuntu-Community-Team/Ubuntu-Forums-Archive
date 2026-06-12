---
title: "file system question and reusing an old hard drive"
date: 2013-11-29
forum: Installation &amp; Upgrades
---

### Post by Dennis McClary on 2013-11-29
I am going to reuse an old hard drive to do a clean install of 12.04 LTS 64 bit. I have copied needed files to an external hard drive. The hard drive currently has 32 bit Ubuntu 12.04 with ext3 filesystem(the result of multiple upgrades). Will a clean install of 12.04 LTS 64 bit convert it to ext4 filesystem? Do I need to do anything to the old drive prior to clean install? Thanks in advance.

Dennis McClary

---

### Post by Bashing-om on 2013-11-29
Dennis McClary; Hello .

The "new" install onto the old hardrive no problem. The install wizard will take care of everything if you want it to. Just choose "erase disk and install ubuntu". The default is now the ext4 file system.

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by fantab on 2013-11-30
The install wizard will only do a basic management of the HDD; it only creates two partitions '/' and 'swap'. If you need more control then either use Gparted from Live DVD or use 'Something Else' option in the Installer to mannually manage the HDD partitions and Ubuntu install to the partitions.

It is an excellent idea to keep your DATA separated from the 'system files'. Keep system files on '/' partition and create a separate '/home' partition for your DATA.

---

