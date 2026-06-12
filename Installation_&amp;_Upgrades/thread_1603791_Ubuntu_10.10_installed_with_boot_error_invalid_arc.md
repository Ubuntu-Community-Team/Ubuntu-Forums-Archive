---
title: "Ubuntu 10.10 installed with boot error: invalid arch independent ELF magic"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by AndreLeComte on 2010-10-23
Please tell me how to resolve this boot error message after installing Ubuntu 10.10:

> invalid arch independent ELF magic
Aborted. Press any key to exit.

Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key

This was a fresh installation of Ubuntu. I have two hard drives with Windows Vista on one of them.

Thank you....

---

### Post by AndreLeComte on 2010-10-26
Is there any way to get the Grub menu to load?

---

### Post by AndreLeComte on 2010-10-26
Do I need to somehow fix Grub using the Ubuntu CD?

---

### Post by AndreLeComte on 2010-10-26
I held down the Shift key while booting which revealed the following text:
> 
GRUB loading.
invalid arch independent ELF magic
Aborted. Press any key to exit.

invalid arch independent ELF magic
Aborted. Press any key to exit.

Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key

---

### Post by AndreLeComte on 2010-10-26
When running GParted Partition Editor from the Ubunutu CD, the first hard drive sda has the warning 'Can't have a partition outside the disk!' and the second hard drive sdb has the warning 'unrecognized disk label'.
Should I install Ubuntu 10.10 again?

---

### Post by AndreLeComte on 2010-10-26
After installing Ubuntu again the same error appears when it tries to boot:
> GRUB loading.
invalid arch independent ELF magic
Aborted. Press any key to exit.

invalid arch independent ELF magic
Aborted. Press any key to exit.

Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key 
Is it possible that I have allocated the swap or ext4 partitions incorrectly or that the boot loader has been installed on the wrong device?

---

### Post by AndreLeComte on 2010-10-26
Should I physically remove the Windows hard drive and install Ubuntu again?

---

### Post by AndreLeComte on 2010-10-26
How can I physically determine which drive has Windows on it?

---

### Post by AndreLeComte on 2010-10-27
Ubuntu 10.10 is installed on the sdb hard drive. When trying to reinstall GRUB the following error is returned:
> grub-setup: warn: Attempting to install GRUB to a partitionless disk. This is a BAD idea..
How can the partitioning be fixed?

---

### Post by AndreLeComte on 2010-10-27
How can I get Ubuntu 10.10 working on the sdb hard disk without losing Windows from the sba hard disk?

---

### Post by AndreLeComte on 2010-10-27
The Windows Vista CD only detects one hard disk and that hard disk is all unallocated space. Will the Rescatux CD or Super Grub2 Disk be able to fix the partitions?

---

### Post by AndreLeComte on 2010-10-27
Windows Vista is detected by Super Grub2 Disk and needs to be repaired. The Windows Vista CD cannot start the repair because it can not detect Windows Vista. Any ideas?

---

### Post by AndreLeComte on 2010-12-16
I downloaded Active@ Boot Disk from [www.ntfs.com](www.ntfs.com) and I can see that my files still exist. I will try install an operating system on the empty drive and recover the files manually.

---

### Post by HarrisonNapper on 2011-08-23
Your thread indicates solved. I'm having the same problem and given the treatment this thread has gotten, I'm guessing no one has an answer. Could you give us the details on how the problem was solved?

---

### Post by AndreLeComte on 2011-08-23
I am not sure what specifically caused the boot error and the only way I managed to recover from it was by downloading Active@ Boot Disk from [www.ntfs.com](www.ntfs.com) 
I bought a new hard disc, installed an operating system on it and recovered my files manually.

---

### Post by HarrisonNapper on 2011-08-24
Ah, no worries, thanks for the info! Luckily I had no files to recover so I just mosey'd over to another install. I think it's that Ubu 10.10+ bootloader (grub2,plymouth? haven't been keeping up lately) doesn't like being installed to anything other than the first disk on a given system. So for me, installing to /dev/sda worked (sort of, long story), but installing to /dev/sdb resulted in this error. For googlers out there, try moving the bootloader to your primary hard disk and see what happens.

---

### Post by AndreLeComte on 2011-08-24
As a last resort after transferring recovered files, formatting the drive and running a clean installation of Ubuntu 10.10 fixed the problem.

---

### Post by Jive Turkey on 2011-11-22
> **AndreLeComte said:**
> Should I physically remove the Windows hard drive and install Ubuntu again?

That is always a good idea, I always do.  you can run update-grub later to get it in the boot menu.  IMHO you should always back up or disconnect disks/partitions you don't want to lose when running partitioning/formatting on a drive.

I heard it said that there are two types of users, those who haven't lost their data before, and those who do backups.

---

