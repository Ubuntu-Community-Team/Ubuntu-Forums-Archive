---
title: "Can't boot Ubuntu on multi-boot system"
date: 2014-06-01
forum: Installation &amp; Upgrades
---

### Post by asb3 on 2014-06-01
My system hast three hard drives.  Ubuntu is installed on /sda and CentOS6 is installed on /sdc.  I can't boot Ubuntu.  I tried running boot-repair and it failed with some error message about not being able to write the file. 
 I did generate a bootInfo summary, which is located at /paste.ubunt/com/7569961.
I should be able to add an entry by hand to the grub.conf file, but I don't know what the entry should be.

---

### Post by oldfred on 2014-06-01
You are showing Centos on sda using grub legacy?

Ubuntu is on sdc.

Have you tried booting from sdc?

With LVM installs you have to mount the LVM install, you should have lvm2 driver and then os-prober should find the Centos install.

Do not use auto fix in Boot-Repair it wants to write grub to every MBR. Best  to keep your Centos grub legacy boot loader in sda and grub2 in sdc. Use advanced mode and choose system and choose drive to install boot loader.

You also show gpt partitioning in sdb. Grub legacy will not work with that.

---

### Post by asb3 on 2014-06-02
I successfully booted from sdc.

Thanks for the help.

---

