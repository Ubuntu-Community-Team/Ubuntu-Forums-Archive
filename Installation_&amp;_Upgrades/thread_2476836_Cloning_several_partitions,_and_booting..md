---
title: "Cloning several partitions, and booting."
date: 2022-07-09
forum: Installation &amp; Upgrades
---

### Post by hornetster on 2022-07-09
Have an existing system that is dual-booting Win10 + Ubuntu 22.04.

Partitions (MBR)
1 - Win boot
2 - Win main
3 - Ubuntu 22.04
4 - Extended
     4a - Home
     4b - Data

Want to add a new SSD to the system, so have cloned 1 + 2 + 3 + 4 + 4a.
All OK, but will not boot (obviously..)
How do I setup this drive to boot?
Would like to be able to setup from another computer, connected as an external drive, until I know it boots (ie Have cloned partitions, but original machine being used, and can't play with it until new disk working...)
Realise I need to set a boot flag (by itself, doesn't work), what else do I need to do, to get it to boot? (Also realise I need to set as boot drive in BIOS.)

All suggestions welcome.
Thanks.

---

### Post by tea for one on 2022-07-09
> **hornetster said:**
> All suggestions welcome.
Hopefully, my suggestion will be welcome but it will involve a lateral arabesque (sideways move).

You have old style Legacy installations of both Windows 10 and Ubuntu 22.04.
You will eventually have two disks on your PC.
Back up personal data.
Install Windows10 on one disk and Ubuntu 22.04 on the other disk.
Install both in UEFI mode with GPT
Boot independently via UEFI.

---

### Post by hornetster on 2022-07-10
Thanks, but not an option.. (if it was for myself - yes!)
Just want to know how to set to boot...

---

### Post by TheFu on 2022-07-10
> **hornetster said:**
> Thanks, but not an option.. (if it was for myself - yes!)
Just want to know how to set to boot...

The easiest way to boot is through UEFI which requires using GPT.  Retaining msdos partitioning is a mistake at this point.  Linux doesn't care, but MS-Windows does. UEFI+GPT are required for Windows-64bit to work.

That's the best solution.

But if you insist on keeping msdos partitions, then you'll need to run the **boot-info** script for smarter people than I to look over to see what is really on the system. Google 'boot-info ubuntu github" to find it.  Post either the full output or the URL it will generate.

---

### Post by yancek on 2022-07-10
You cloned only the partitions so you have no Grub code which was on the MBR of the original drive so you need to install Grub on the external or new drive you have cloned to.  Also set the boot flag on the windows partition with the boot files/  For a Legacy install such as yours, you can install Grub with:

 # sudo grub-install --target=i386-pc --recheck --boot-directory=/mnt/external/boot /dev/sdb

Before doing this from a 'live' USB, you need to create the mount point (/mnt/external/boot) and change sdb to whatever drive you are installing to.

You may need to chroot, so if that is the case, assuming the external drive you want to install to is sdb: You need to create the mount point ubuntu first and this assumes your / filesystem is on sdb2 so change to suit and run the grub-install command above.

sudo mount /dev/sdb2 /mnt/ubuntu
sudo mount -o bind /dev /mnt/ubuntu/dev
sudo mount -o bind /proc /mnt/ubuntu/proc
sudo mount -o bind /sys /mnt/ubuntu/sys
sudo chroot /mnt/ubuntu /bin/bash

---

