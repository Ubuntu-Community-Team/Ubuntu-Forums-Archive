---
title: "Target Dual Boot, Windows gone after boot-repair"
date: 2014-07-30
forum: Installation &amp; Upgrades
---

### Post by Puneet_Agarwal on 2014-07-30
My laptop has SSD + HDD also.

It came with Windows 7 pre-installed in SSD (/dev/sda)

Then I installed Ubuntu 14.04 in the SSD (/dev/sda). Then installed Windows in HDD ( /dev/sdb)
Then I could not boot using Ubuntu.
Then I followed the instructions given in "https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"

After this, I am able to see Windows and Ubuntu both in the boot-menu and if I choose Ubuntu it works fine.
However if I choose Windows 7 (/dev/sdb1) nothing happens I only see the Ubuntu blue screen

Is windows gone? What should I do to set-up my machine for dual boot?

Boot-Repair had given me following URL for details of my machine - [http://paste.ubuntu.com/7906078](http://paste.ubuntu.com/7906078)
(This URL will give you detailed description of my machine.)

Thanks in anticipation.

- Puneet

---

### Post by oldfred on 2014-07-30
Your sdb the 120GB is your SSD?
It still shows a small NTFS partition that looks like a Windows boot partition. But it also looks like you have all the Windows boot files, bootmgr & BCD in sda1 in your install on sda1.

Boot-Repairs auto fix auto installs grub to every MBR. With mulitple drives better to use advanced options and choose to install Windows boot loader to Windows drive or sda/500GB drive and just have grub on sdb.

Boot-Repair did do this, so now you should be able to directly boot Windows from sda:
Copied Win boot files from sdb1 to sda1

Then if grub is not correctly booting Windows you still should be able to choose to boot Windows directly from BIOS or one time boot key often f12 but varies by vendor.

Can you boot the sda1 entry in grub? And it may make a difference if booting grub from sda or grub from sdb?
Often when booting from one drive and Windows is on another drive, grub usually needs to do a drivemap to make Windows think it still is the boot drive. So if from sda, it may not need it, but from sdb it may.  But I prefer to have Windows boot loader on sda, so you can directly boot it.

Grub really only boots working Windows, so if chkdsk or hibernated then grub will not boot it.

---

### Post by Puneet_Agarwal on 2014-08-02
Thanks. It worked. Thanks for all the help.

First thing I did was removed the extra system partition.
then went into the advanced options of boot-repair and installed grub where Ubuntu is installed and MBR where Windows is installed.
Done. It works.

Thanks Again.

---

