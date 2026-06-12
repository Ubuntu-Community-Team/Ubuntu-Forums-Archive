---
title: "install 24.04 in encrypt partition!"
date: 2024-07-05
forum: Installation &amp; Upgrades
---

### Post by justaskingty on 2024-07-05
Hey all :o

i try to install 24.04 in my pc (only 1 os )  but my hard drive have partitions in use for saveing files . so after im in manual partition install there is nothing to encrypt the partition that have install ubuntu in it! 

is there a way or did i mess something?

---

### Post by currentshaft on 2024-07-05
You're trying to encrypt the Ubuntu partition from the installer on one disk? Unless you know exactly what you're doing, I would not recommend that for risk of losing other partitions.

Can you post a screenshot of what you're seeing?

---

### Post by Rubi1200 on 2024-07-06
There is no option to encrypt in manual installation mode.

You can only do it by erasing the entire disk and choosing the advanced option to use LUKS.

Since we do not know your system or current layout, please post the information asked for by [B]currentshaft.

[/B]Better still, on the live USB open a terminal and post the output of ```
sudo fdisk -l
```

Please use code tags when replying so we can read the output.

---

### Post by guiverc on 2024-07-06
You mention Ubuntu 24.04, but not which product & thus installer.

Ubuntu 24.04 LTS Server uses `subiquity`, and Ubuntu 24.04 LTS Desktop uses `ubuntu-desktop-installer`, and some 24.04 *flavors* also use `calamares`.

You also don't mention what encryption; LUKS1, LUKS2 & other encryption methods are available; I've re-installed on an old encrypted partition install as was used by 17.10 & and earlier; however as that encryption method is *deprecated* (LUKS is superior), the packages required for that haven't been included for some time on Ubuntu ISOs, but were still available and can be added to install media prior to starting the installer if that's what you're asking about.

You may find [https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019](https://help.ubuntu.com/community/Full_Disk_Encryption_Howto_2019) helpful if you're wanting full disk encryption (LUKS) though its technical in nature.

By far the easiest way to install using encryption (*both LUKS1 & especially LUKS2; you can't select which, the ISO/installer used will choose this*) is just using the installer's built in tools, which will format the disk, so you'll need to just restore your data post-install  (*thus ensure you've backed up all data before install*).

---

### Post by cvs-ut on 2024-08-29
I am also having an issue with this on the new Ubuntu 24.04 Desktop installer.  The previous installers had an option to choose the mounted LVM to install / when doing a manual install.  Now that option is gone and I can only choose the partition itself.  I use the manual installer to put Ubuntu on a bootable external ssd, which must be encrypted per our organization's requirements.  Is there a workaround?  I don't want to risk deleting the other OS on my pc.

You can see /dev/sda blocks - sda is the external drive.  /dev/sda5 is encrypted with LUKS2 and mounted at /dev/mapper/vgroot-lvroot.

---

