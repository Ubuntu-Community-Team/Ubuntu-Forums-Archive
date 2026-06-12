---
title: "Reinstall while preserving dual boot with vista?"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by photonic on 2008-05-27
Hi forum,

In the past, I successfully dual-booted Ub7.04 with Vista, which I later upgraded to Ub7.10. Since I messed some things up, I'd rather do a complete reinstall of 8.04 instead of upgrading. Obviously, I want to preserve my Vista installation, my shared data partition and the ability to dual boot.

What is the recommended way of doing the reinstall? I assume that grub is located on the bootable vista partition, so if I simply reformat the old swap and Ubuntu partition, will the installer overwrite the old Grub and make a new one? I read some forum posts of people not being able to boot windows and having to repair the MBRs and grub. I'd rather do it in a clean and simple way ...

My partions:
sda1  2 GB swap (former vista recovery partition, couldn't be moved so I used it for swap)
sda2 35 GB NTFS vista, boot partition
sda3 60 GB fat32 shared data between vista/ubuntu
sda4 15 GB ext3 ubuntu

Thanks,
Bas

---

### Post by IgnorantGuru on 2008-05-27
Hi,  grub is not located on the Vista partition (grub ignores what partition is 'bootable'.  It looks like this...

MBR  (contains grub boot code)
sda1 2 GB swap
sda2 35 GB NTFS vista
sda3 60 GB fat32 shared data
sda4 15 GB ext3 ubuntu  (grub's root - contains grub files)

So sda2 is not your boot partition.  The MBR uses the files located in /boot/grub on sda4 to generate your boot menu and boot the various systems.

When you do your install, select manual partitioning, and set it up like this...

sda1 2 GB swap   FORMAT
sda2 35 GB NTFS vista   KEEP  /mnt/windows
sda3 60 GB fat32 shared data  KEEP  /mnt/user
sda4 15 GB ext3 ubuntu  (grub's root - contains grub files)  FORMAT  /

Allow the installer to install grub to the MBR again, and it should recognize Vista so it will be bootable.

I have a guide on this here...
[http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems](http://en.wikibooks.org/wiki/How_To_Backup_Operating_Systems)

If you have your doubts about grub, make a backup of your MBR and a backup copy of /boot/grub/menu.lst

---

### Post by photonic on 2008-05-27
Thanks for the quick and informative reply. It worked without any problems: I formatted only the swap and linux partition and after installation there was a new grub that correctly boots vista and ubuntu.

This is better than commercial support: I ask a question, an hour later I have a relevant answer and another hour later I have my system reinstalled :).

---

### Post by IgnorantGuru on 2008-05-27
Glad to hear it.  That's one thing I like about the linux community - one tends to get some genuinely helpful answers.  MUCH better than any commercial tech support I've encountered.  :)

---

