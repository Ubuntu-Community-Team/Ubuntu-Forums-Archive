---
title: "Help with frustrating install on netbook"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by JeffDG on 2010-01-31
Hello everyone,

   Im attempting to install Ubuntu on a Samsung N130 1.6ghz 160gb netbook with 1gb RAM. It originally came installed with Windows 7 starter. I downloaded Unetbootin, downloaded 9.10 Netbook remix ISO, and installed to a PNY 4gb flash drive. 

 I was able to boot from the flash drive and use the live version, but upon installing I had an error with my HD and was forced to cancel. Upon rebooting i received the "No OS Found" error. To be safe i downloaded parted magic onto the flash and wiped the HD clean.

Afterwards UNR will not finish boot sequence, giving me various errors. I assumed the ISO was corrupted, formatted the drive and installed the desktop edition ISO. Still have problems with initial boot sequence. 

   I have installed Ubuntu on desktops in the past via CD with no problem however this is my first flash drive install. I was up til 3:30 in the morning trying to figure this out, and am stuck.

                                                               Thank you, Jeff

---

### Post by JeffDG on 2010-01-31
Well... Im embarrassed to say the least. After going back through and careful reading everything i must have skimmed over last night I found the following,

"
(optional) If you need to activate the original Ubuntu livecd boot menu, for example if you want to disable the framebuffer or read the Ubuntu livecd HELP screens and cheatcodes, please make these changes to your USB drive after your UNetbootin installation is completed: 
1) Delete the SYSLINUX.CFG file or rename it to be SYSLINUX.OLD 
2) Enter the ISOLINUX folder and rename the ISOLINUX.CFG file to be SYSLINUX.CFG. You may or may not need to rename ISOLINUX.BIN to SYSLINUX.BIN, but it won't hurt. 
3) Move up to the top level and rename the ISOLINUX folder to be SYSLINUX"

Did this, and am currently completing installation.

---

### Post by oupamster on 2010-01-31
congradulations, it's very important to read carefully.

---

### Post by JeffDG on 2010-01-31
unfortunately at about 75% the install halted with [errno 5] Input/Output.

Check the disk upon reboot and was told 5 files were damaged. If i cant get this to work I will try another flash drive.

---

### Post by oupamster on 2010-01-31
you might also md5 the downloaded iso else you could try reinstalling the iso to the same flash. otherwise you can try another flash.

---

### Post by JeffDG on 2010-01-31
Iso md5 comes back good. Just purchased the flash drive for this yesterday, is it possible that is the problem? Worst case scenairo, what are my options? Blank HDD with just bios and no cd drive.

---

### Post by oupamster on 2010-01-31
> **JeffDG said:**
> Iso md5 comes back good. Just purchased the flash drive for this yesterday, is it possible that is the problem? Worst case scenairo, what are my options? Blank HDD with just bios and no cd drive.

Can you reformat the stick to fat32, and recreate the iso on to the flash drive? otherwise you might try with a different flash drive. 

Earlier you mentioned you had an error "75% the install halted with [errno 5] Input/Output" and that might be from the stick/flash drive read/write.

---

