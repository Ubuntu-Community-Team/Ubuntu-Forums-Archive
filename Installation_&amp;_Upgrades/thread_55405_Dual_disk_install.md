---
title: "Dual disk install"
date: 2005-08-08
forum: Installation &amp; Upgrades
---

### Post by Oxide on 2005-08-08
I installed Hoary on a small partition of my IDE drive and everyhting went smoothly.

Now, I want to install Hoary on another disk I bought which happens to be a SATA disk.

The install itself goes well and everything is fine until I need to reboot.
The GRUB comes up but no matter what I select (XP, Linux or recovery mode) nothing happens...... well if I'm trying to boot into Linux it tells me that there isn't anything to boot and it goes back to the GRUB selection image. When XP is selected it does something so fast I can't see it and goes back to the GRUB.

I understand that I should make the partition that has Linux on it bootable and I did that. On that SATA disk I had 2 other partitions, the SWAP partition and a FAT32 partition to be able to move things between the OS's.

Am I missing something obvious or is it just the SATA thingy not working?

Thanks!

---

### Post by amohanty on 2005-08-08
I have two SATA and the install works fine. A few questions:
Do you still have the IDE drive attached?
Is Hoary still installed on the IDE? 
In your CMOS setup whats the default boot device setup to be?
Something to note is that my BIOS, recongnizes the SATA's as removable drives, and also allows me to setup a removable device as the first boot device. However since I dont have any IDE devices other than my CDROM, I dont face the problem.

AM

---

### Post by Oxide on 2005-08-09
Yes, I still have the IDE disk in my computer as I don't want to delete my Windows setup.
I played with the boot order settings in the BIOS with no results.
I installed Hoary back onto the IDE drive in order to have my computer working.
After installing Hoary back onto the IDE drive everything works fine again.

I also read that the SATA's had problems if they were raided in the BIOS but that is not my case.

My BIOS doesn't have a default boot device, it has boot order. I can select 3 drives that I want the computer to try to boot, if the first one fails it goes to the second one and so on.

---

### Post by Oxide on 2005-08-09
Well, it seems that Ubuntu just CAN'T see my new SATA disk.
I installed Ubuntu back on the IDE drive and set my SATA disk to mount as /work

The folder /work is on the computer but shows me that it has 4.4GB free and not 190GB like it should.

Is there anything I can do to make the drive work propperly?

---

