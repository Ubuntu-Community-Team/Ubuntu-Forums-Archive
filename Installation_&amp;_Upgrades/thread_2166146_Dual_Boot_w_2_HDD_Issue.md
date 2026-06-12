---
title: "Dual Boot w/ 2 HDD Issue"
date: 2013-08-07
forum: Installation &amp; Upgrades
---

### Post by Cody_Sickler on 2013-08-07
Hi all,

I'm having difficulty in getting dual boot working using two HDDs. Ideally, what I would like to happen is for the Windows boot loader to be used instead of GRUB. However, whenever I update the boot record via easyBCD and restart, selecting the Ubuntu option... It boots to GRUB4DOS. 

I'm not sure what I'm doing wrong.

---

### Post by carl4926 on 2013-08-07
People have no end of trouble with not using Grub

---

### Post by fantab on 2013-08-08
Are the OS on different HDD or on one HDD? If you have OS on different HDDs then your first boot HDD must be the one which has easyBCD. You can check the BIOS for this.

---

### Post by Mark Phelps on 2013-08-08
Few points to consider ...

First of all, you must use GRUB (or something like it) to boot Ubuntu.  Windows can NOT boot Ubuntu by itself.

Second, EasyBCD has the option to install a version of GRUB that runs in the Windows filesystem -- known as GRUB4DOS.  So, basically, you ARE using GRUB to boot Ubuntu -- just a different version of it.

Third, if you really have two separate hard drives (not the "drive" in MS terms, which are really just "partitions"), the better way to do this is to have a single OS on each of the drives, with each OS having its own boot loader on that drive.  Since GRUB is able to add the code needed to invoke the Windows boot loader, the simple solution then is to avoide EasyBCD and use GRUB.  You do that by installing GRUB on the Ubuntu drive, booting that drive, and then entering "sudo update-grub" in a terminal.  That will regenerate the default GRUB config file and add an entry for the Windows boot loader.  When you reboot, you will have a GRUB menu with entries for Ubuntu and Windows.

If, however, you want to continue doing this with EasyBCD, then you should go to the NeoSmart Technology forums (the supporters of EasyBCD) and check there for support and tutorials.

---

