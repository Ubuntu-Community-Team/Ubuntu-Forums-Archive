---
title: "Horror Run With Ubunutu Instilation Continues"
date: 2007-03-10
forum: Installation &amp; Upgrades
---

### Post by Rednut on 2007-03-10
Hey everyone,

I tried a couple of weeks ago to install Ubuntu on an old Pentium II, which summarily caught fire. So I purchased myself a new tower (Pentium IV, 2.66Ghz, 512MB RAM, 40GB Maxtor harddrive) and attempted to install Ubuntu 6.10. It took many,*many* failed attempts, but finally I got the installation process to go smoothly (I installed from an alternative disk because my mouse wasn't being recognised with the live CD). After the installation process had completed, I was given a  message "Your computer will now reboot into your new operating system", or something similar. I removed the instillation CD as suggested by the message, and pressed enter for it to reboot. It got to the black screen with white writing (BIOS?) and gave me the error:

Verifying DMI Pool Data .......
Boot from CD: 
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

This is despite the fact that I have set the hardrive to be the Primary Master, and the CD ROM to be Primary Slave. 

Does anyone know what exactly the problem is?

---

### Post by pradeepadapa on 2007-03-10
it seems that the grub didnt install properly on ur system, do go to recovery mode from the alternate cd of ubuntu  6.10

---

### Post by Rednut on 2007-03-10
Sorry to be slow, but how do I access recovery mode, and once there, what do I do?

---

### Post by Rednut on 2007-03-10
deleted

---

### Post by Stormx on 2007-03-10
Have you tried simply reinstalling grub, as instructed in the channel?

---

### Post by Rednut on 2007-03-10
Acting on the advice of xtknight I changed my boot order to primary:hd1, secondary hd0 which got rid of the 'DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER' error, but replaced it with: 
ISOLINUX 3.11 debian-2006-03-16 isolinux: image checksum error, sorry' 
Boot failed: press any key to retry...
So i changed boot order back to CDROM but now I can't boot the live CD either.

---

### Post by pradeepadapa on 2007-03-11
hello rednut,

if u r facing problems with ubuntu 6.10 then u try other linux distros like debian or mandriva or fedore 6, they r fine ,whatever distro u use but the main thing is that DONOT DEVIATE FROM LINUX.

---

### Post by pradeepadapa on 2007-03-11
hey since it gives u an checksum error, then i think ur cd has defect, just try to get an better cd nd check the md5 checksum of the image which u hav downloaded frm the ubuntu servers.............

---

