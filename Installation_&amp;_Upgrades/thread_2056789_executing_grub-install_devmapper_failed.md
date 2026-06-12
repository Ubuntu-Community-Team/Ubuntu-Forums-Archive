---
title: "executing grub-install dev/mapper failed"
date: 2012-09-12
forum: Installation &amp; Upgrades
---

### Post by cancellic on 2012-09-12
l cant install ubuntu on my dell pc cause of this error after reinstalling windows 7, what can l do?

---

### Post by oldfred on 2012-09-12
If you have a mapper, you have RAID or LVM or something that needs drivers that are not normally in the liveCD. The alternative installer has those drivers. You can add the drivers or run this gui which downloads the drivers in the background.

sudo apt-get install lvm2
sudo apt-get install mdadm

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by cancellic on 2012-09-13
Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/1203740/](http://paste.ubuntu.com/1203740/)

In case you still experience boot problem, indicate this URL to:
[email]boot.repair@gmail.com[/email] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on mapper/isw_dddighfbed_ARRAY0 (1933GB) disk!

The boot files of [Ubuntu 12.04.1 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

---

### Post by cancellic on 2012-09-13
now l can choose between windows and linux, but after selecting linux, it appears the ubuntu writing and the pc freezes here

---

### Post by oldfred on 2012-09-13
What video do you have? With nVidia I have to use nomodeset on linux line in grub menu.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

