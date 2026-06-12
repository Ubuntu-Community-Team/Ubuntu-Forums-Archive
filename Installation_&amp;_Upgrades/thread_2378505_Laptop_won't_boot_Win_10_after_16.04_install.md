---
title: "Laptop won't boot Win 10 after 16.04 install"
date: 2017-11-23
forum: Installation &amp; Upgrades
---

### Post by newbierb on 2017-11-23
I installed Ubuntu 16.04 (32 bit) on a Win 10 (64 bit) laptop. Now it wont recognize the presence of Windows on the internal HD.

My intention was to create a dual boot machine.

   [http://paste.ubuntu.com/26026313/](http://paste.ubuntu.com/26026313/)

Thanks for any help you can provide

---

### Post by Dennis N on 2017-11-23
Doesn't look like Windows exists on your disk. Perhaps you made a wrong choice of selecting an installation type which erased the disk before installing? Note that line 502 of the boot info summary states what it detects: 1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

---

### Post by newbierb on 2017-11-23
I did notice that, once I looked at the Boot Repair file.  I think there is more to it, though.  There are still a whole lot of Win files on the Hard Drive though.

The Installer didn't seem to see there was another OS on the HD already, when I was going through the install process.

---

### Post by yancek on 2017-11-24
You did an LVM installation according to the boot repair output which overwrites the disk so if you had data on the windows partition, stop using the drive and use a Live system to try to recover data.

If you had windows 10, it most likely was pre-installed and was thus an EFI/GPT system and Ubuntu is not installed EFI/GPT.

One reason the installer did not see there was another OS on the disk might be that it was left hibernated (default on windows 10).  You might be able to recover some windows data but will likely need to re-install windows if you still want it.  Carefully reading the Ubuntu documentation at the site below 'before' installing would have saved you a lot of trouble.  Good luck.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

