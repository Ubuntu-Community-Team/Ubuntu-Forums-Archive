---
title: "Boot repair W10 - Ubuntu 16"
date: 2016-09-11
forum: Installation &amp; Upgrades
---

### Post by diego61 on 2016-09-11
Hi , I have a laptop with W10 and recently I tried to install Ubuntu 16.04. I've succesfully done it , but now I can't start W10. I've tried to repair the boot with boot-repair  ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) , but the recommended option did not work. Boot-repair gave me the following link: [http://paste2.org/c1mOfFpz](http://paste2.org/c1mOfFpz)

Anyone can help me ? Thanks!

---

### Post by oldfred on 2016-09-11
You should be able to directly boot Windows from UEFI boot menu. Often f10 or f12 shows you a boot menu, check your manual for correct key(s).

Grub used to not boot Windows if Secure Boot was on. One user reported it worked, but not sure if he knew if configuration was Secure boot or not.

Also grub only boots working Windows. Or Windows cannot be hibernated which Windows fast startup uses, nor can Windows need chkdsk which after file corruption of any type it may need.

Best to have Windows repair/recovery drive.
       How to: Create a Recovery Drive for reinstalling Windows 10 from Windows 10
[http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5](http://answers.microsoft.com/en-us/windows/wiki/windows_10-win_upgrade/how-to-create-a-recovery-drive-for-reinstalling/58df9c7d-84de-4652-9952-8bac34abc6c5)
[http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/](http://www.howtogeek.com/239312/how-to-restore-system-image-backups-on-windows-7-8-and-10/)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

---

### Post by diego61 on 2016-09-12
Thanks oldFren , I didn't realize I had to change the option from the boot menu.

---

