---
title: "Dual boot install of Ubuntu on system with rocky linux already installed"
date: 2022-11-04
forum: Installation &amp; Upgrades
---

### Post by mazellan on 2022-11-04
Hi, 

I have a Rocky linux 9 installation on my system and I want to install Ubuntu 22.04 LTS (separate HDD) for dual boot. 

My problem is that the Ubuntu installer doesn't recognize the already installed OS. How should I proceed without destroying my other OS installation?

---

### Post by guiverc on 2022-11-04
I don't know Rocky Linux, and you didn't provide specific details on your Ubuntu 22.04 LTS system (ie. `ubiquity` is the default installer for 22.04 Desktop, `subiquity` for 22.04 Server..) but I'd just prepare the partitions yourself as you want them, then install using the "*Something else*" (or "*Manual Partitioning*" if using an ISO with `calamares used by two 22.04 *flavors*..) and have Ubuntu install to the partition(s)/drive(s) you have prepared.

Read the summary before you start install & if it's what you want, let install proceed.  If you don't format partitions (ie. *telling the installer to use prepared partitioning*) you can usually back out if the summary doesn't look correct (*this may not be the case if you're telling the installer to adjust partitions or format, why I do it first before I start the installer*).

Yes you should backup first (*it's easy to make a mistake*), though if unsure, create a setup like what you want to create on a VM or test box (*old pc*), and test out the install you want to do first on something that doesn't matter.  Use the sam*e **filesystems* your Rocky is using (*the file-system matters!*) so you know it works.  We generally don't use installers often, so practice makes perfect.... My 2c.

---

### Post by mazellan on 2022-11-11
sry for late response. My concern is with the boot loader installation. As the ubuntu (desktop) installer doesn't recognize the previous installation I guess the boot loader will be overwritten and not just modified to allow dual boot? Messing with the boot loader is kind of over my head :)

---

### Post by tea for one on 2022-11-11
Isolate, de-activate or remove the disk containing Rocky Linux.
Install Ubuntu on the second separate HDD.
The Ubuntu installer will then not interfere with the bootloader on Rocky Linux. 

Boot either OS by using the dedicated key to access the one-time boot menu.
Make sure that both systems are installed in UEFI with GPT.

---

### Post by oldfred on 2022-11-11
If UEFI and Rocky not one of the versions that uses "ubuntu" as boot entry, you will get two boot entries in UEFI.
If old BIOS, you can have grub boot loader in MBR of each drive.
Is system UEFI or BIOS/Legacy?
Check UEFI boot mode
```
[ -d /sys/firmware/efi ] && echo EFI || echo Legacy
```

Both systems need to be in same boot mode. And since systems since 2012 are UEFI best to use UEFI boot mode on gpt partitioned drives.
Gparted still defaults to MBR, so best to manually partition a new drive and first change to gpt. 

How you boot install media from UEFI/BIOS boot menu UEFI or BIOS boot, is then how it installs.

---

### Post by mazellan on 2022-11-11
Thanks for the input. I took a chance and installed Ubuntu, and the boot loader is fine. I get the option to load either Rocky or Ubuntu at startup.

---

