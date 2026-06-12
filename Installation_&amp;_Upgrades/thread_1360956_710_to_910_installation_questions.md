---
title: "710 to 910 installation questions"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by Wabasha on 2009-12-21
Hello all,

I run version 7.10LTS Ubuntu on a PC that is set up as a dual boot machine. I would like to install version 9.10 over my old installation of Ubuntu, but want to retain my /home folder in Linux.

I have 2 drives, hda (Windows only) is partitioned into 2 drive letters, the first (hda1) 27.54GB contains W98SE and the second (Hda5) 65GB has XP Home.

Hdb (Linux only) has 3 partitions, (hdb1) 14.65GB Ext3 and set as /, (hdb3) 96.96GB Ext3 is the /home partition, and (hdb5) 2.89GB is the swap.

Legacy Grub is in the boot sector of hda1.  I will post screenshots of partitions

I still want to continue to Dual Boot this computer.

These are my questions:

1. Will the install of 9.10 replace the Legacy Grub bootloader without messing up things, or will I need to run Windows repair first and do fixboot and fixmbr? I assume Grub2 with all its problems will be installed over the Legacy Grub.

2. I would like to retain my home partition in Ubuntu and without it messing up configurations of Gnome on the new install. 

I believe that can be done by installing 9.10 and just finding the /.gconf directory after installation and renaming it and 
restarting the window manager to create a new /.gconf. Am I correct?

3. Will the 9.10 installation allow me to retain the current Ext3 formatting of the / and /home partitions?

---

### Post by SlugSlug on 2009-12-21
> **Wabasha said:**
> Hello all,

I run version 7.10LTS Ubuntu on a PC that is set up as a dual boot machine. I would like to install version 9.10 over my old installation of Ubuntu, but want to retain my /home folder in Linux.

I have 2 drives, hda (Windows only) is partitioned into 2 drive letters, the first (hda1) 27.54GB contains W98SE and the second (Hda5) 65GB has XP Home.

Hdb (Linux only) has 3 partitions, (hdb1) 14.65GB Ext3 and set as /, (hdb3) 96.96GB Ext3 is the /home partition, and (hdb5) 2.89GB is the swap.

Legacy Grub is in the boot sector of hda1.  I will post screenshots of partitions

I still want to continue to Dual Boot this computer.

These are my questions:

1. Will the install of 9.10 replace the Legacy Grub bootloader without messing up things, or will I need to run Windows repair first and do fixboot and fixmbr? I assume Grub2 with all its problems will be installed over the Legacy Grub.

2. I would like to retain my home partition in Ubuntu and without it messing up configurations of Gnome on the new install. 

I believe that can be done by installing 9.10 and just finding the /.gconf directory after installation and renaming it and 
restarting the window manager to create a new /.gconf. Am I correct?

3. Will the 9.10 installation allow me to retain the current Ext3 formatting of the / and /home partitions?


1. Legacy grub will be the default when _upgrading_ (a fresh install has grub2),  you can then after upgrade / reboot install grub2 - both will aauto detect your win boots,

2. for this I tend to move /home/username to /home/username.old then mkdir /home/username and chmod it accordingly.

3. yes

---

### Post by Wabasha on 2009-12-21
> **SlugSlug said:**
> 1. Legacy grub will be the default when _upgrading_ (a fresh install has grub2),  you can then after upgrade / reboot install grub2 - both will aauto detect your win boots,

2. for this I tend to move /home/username to /home/username.old then mkdir /home/username and chmod it accordingly.

3. yes

I do not plan on upgrading from 7.10LTS to 9.10, (I dont think it can be done), I want to install 9.10 over the old install, and retain my current home data, thus the question on Grub2, will it delete and replace Legacy grub without me needing to run fixboot and fixmbr?

---

### Post by SlugSlug on 2009-12-21
> **Wabasha said:**
> I do not plan on upgrading from 7.10LTS to 9.10, (I dont think it can be done), I want to install 9.10 over the old install, and retain my current home data, thus the question on Grub2, will it delete and replace Legacy grub without me needing to run fixboot and fixmbr?

It will replace your current grub and add the windows to the grub menu

at least I know it will for XP -- pretty sure it would for 98...

---

