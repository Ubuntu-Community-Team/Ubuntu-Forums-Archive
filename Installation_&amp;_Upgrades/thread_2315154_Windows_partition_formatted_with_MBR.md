---
title: "Windows partition formatted with MBR"
date: 2016-02-26
forum: Installation &amp; Upgrades
---

### Post by Macamba on 2016-02-26
I formatted Windows on sdba (or first hard disk). I was planning to install windows again. Sadly, the Windows partition also contained the MBR with Grub. 


When I bring back/re-install Ubuntu, do I need to do anything special to get the MBR on the first harddisk, and not the second one, with the Ubunti partition?

---

### Post by yancek on 2016-02-26
> Sadly, the Windows partition also contained the MBR with Grub. 

No, it didn't.  The MBR is located at a specific point on a harddrive, sector 1 which is and always has been outside any partition.  You neglected to indicate which version of windows you are using which is significant.  If it was windows 8 or later, it probably wasn't using the MBR and was UEFI.  Which are you using?  If you have Ubuntu on a separate disk, do you have Grub installed in the MBR of that disk.  Which are you actually using, MBR or UEFI?  That's pretty significant as you need both either MBR or UEFI or one won't boot.  Are you able to boot Ubuntu?  Have you tried re-installing windows and if so, what happened?

---

### Post by grahammechanical on 2016-02-26
To recap. You have Ubuntu on one disk drive and you are going to re-install Windows on another disk Drive. First, re-install Windows and get that out of the way. From my very limited experience of installing Windows I would expect the Windows installer to write its boot loader into the MBR of both disks. Assuming that the machine has a BIOS boot system & not a UEFI boot system.

So, as I see it, you would have lost the Ubuntu boot loader anyway. Unless you disconnected the Ubuntu drive. You need to become familiar with Boot Repair. It is just the thing for these situations. Run the live session and download & install Boot Repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Select the Create BootInfo summary option. You will be given a URL to where the summary report has been stored online. Post the URL here and then we see what Boot Repair has found.

Boot Repair will give you an option to repair the boot. It usually does this by reinstalling Grub. But be careful. The default option is to install Grub to the MBRs of all drives. You might want to leave the Windows boot loader on the Windows drive. The Ubuntu boot loader will give you the option to load either Ubuntu or Windows. And you can select which drive to load from using the BIOS. It is useful to still have the Windows boot loader on its drive in the event of sonething going wrong with Ubuntu.

Regards.

---

### Post by Macamba on 2016-02-27
Thanks. FWIW, it is a Windows 10 system. However, after installation of Ubuntu I got Grub as boot manager. 

So Windows first, then Ubuntu. And I was hoping to use Ubuntu to format the Windows partition.

---

