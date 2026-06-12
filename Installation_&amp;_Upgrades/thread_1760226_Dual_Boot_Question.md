---
title: "Dual Boot Question"
date: 2011-05-16
forum: Installation &amp; Upgrades
---

### Post by DaveJones on 2011-05-16
Hi guys,

I'm hoping someone can help me. This might seem a bit of a nooby question to some, but I'm a bit cautious about what I'm trying to do. 

Right, I currently have Ubuntu 10.10 installed on my laptop. I have a W7 install disk and I want to install it and achieve a dual boot with my Ubuntu install. Now unless I'm mistaken, there's no option to do this on the W7 installer, so if I run the W7 install it will likely wipe my Ubuntu install - which I do not want.

What is the best way to achieve a dual boot in this situation? I have tried VirtualBox, but it doesn't achieve what I want to do. I need a full Windows install.

Thanks in advance.

---

### Post by Dreigo42 on 2011-05-16
It really is easiest to install windows first. Would you be willing to Re-install Ubuntu? You can simply copy your personal files to a USB Key and restore them afterwards.

---

### Post by oldfred on 2011-05-16
You should have everything backed up anyway, but all you really need is a primary NTFS partition with the boot flag. Windows installer will see that and install to that partition. 

Normal win7 installs to two partitions a 100MB boot/recovery partition and the main install, but if the partition already exists it will install to just one.

Windows will also install to free space but you do have to becareful as windows does not see the Linux partitions and sometimes rewrites partition table incorrectly. 

You may want to document your partition table just in case as part of your backups.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

You will have to reinstall grub2's boot loader to the MBR as windows installs its boot loader automatically and will not boot Ubuntu.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

To get grub2's os-prober to add the win7 install to the menu.

sudo update-grub

---

