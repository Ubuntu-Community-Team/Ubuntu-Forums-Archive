---
title: "Ubuntu, XP box, add SUSE 12.1"
date: 2011-12-13
forum: Installation &amp; Upgrades
---

### Post by LMHmedchem on 2011-12-13
I have a Ubuntu/XP box that I want to add openSUSE 12.1 to. I set up a partition under windows and left it un-formatted. Once I got to the partition section of the SUSE installer, I tired to set up the new partition as root, but there was no option for "/" in the list. There were options for /boot, /home, /usr, etc, but no plain / for root. I didn't want to proceed by guessing, so I aborted the install.

I have grub2 on the mbr of the the drive, so I was planning to install without grub and just do update-grub in Ubuntu. I'm not clear on how to get the install done, so if anyone has a tutorial on how to set up a dual boot Ubuntu and SUSE, I would appreciate a link. I know there are some different ways to configure the file system for linux, but I have always just set up a root partition and a swap.

LMHmedchem

---

### Post by zvacet on 2011-12-14
Does your installation look like [http://doc.opensuse.org/products/opensuse/openSUSE/opensuse-startup/art.osuse.installquick.html . ]("http://doc.opensuse.org/products/opensuse/openSUSE/opensuse-startup/art.osuse.installquick.html")

I never installed Suse but I believe you can go without grub and after finishing installation let Ubuntu grub find Suse with 

```
sudo update-grub
```
[]("http://doc.opensuse.org/products/opensuse/openSUSE/opensuse-startup/art.osuse.installquick.html")

---

