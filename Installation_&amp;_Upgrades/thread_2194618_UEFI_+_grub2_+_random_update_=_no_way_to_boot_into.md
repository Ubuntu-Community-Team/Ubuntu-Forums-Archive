---
title: "UEFI + grub2 + random update = no way to boot into windows anymore."
date: 2013-12-19
forum: Installation &amp; Upgrades
---

### Post by Mandibela on 2013-12-19
What should I do to get my setup working? 

[http://paste.ubuntu.com/6601113/](http://paste.ubuntu.com/6601113/) [http://paste.ubuntu.com/6601478](http://paste.ubuntu.com/6601478)

I have rEFIend installed, but atm it can only choose the same boot options as grub that ubuntu made. I think because it just copied the settings from ubuntu.

The problem that I have is that (every) ubuntu update messes the grub cfg. Dual-boot used to work fine. "Windows Boot Manager" is another grub. I have a windows install disk, but it cannot seem to 'comprehend' where it is, if I try to boot from the cd, it gives the 0xc0000185 error ( [http://www-947.ibm.com/support/entry/portal/docdisplay?lndocid=MIGR-5084140](http://www-947.ibm.com/support/entry/portal/docdisplay?lndocid=MIGR-5084140) ) and cannot proceed. I can use bios to boot different disks, but none of the options gets me to windows anymore after the latest ubuntu update.

---

### Post by QIII on 2013-12-19
Moved to its own thread.

---

### Post by Mandibela on 2013-12-19
What should I do to get my setup working? 

[http://paste.ubuntu.com/6601113/](http://paste.ubuntu.com/6601113/) [http://paste.ubuntu.com/6601478](http://paste.ubuntu.com/6601478)

The problem that I have is that (almost every) ubuntu update messes the grub somehow. Dual-boot used to work fine, I could select from boot with UEFI the windows disk, and boot to it. Now, if I let the machine boot, it goes to ubuntu. 

"Windows Boot Manager" is another grub menu now. I have a windows install disk, but it cannot seem to 'comprehend' where it is, if I try to boot from the cd, it gives the 0xc0000185 error ( [http://www-947.ibm.com/support/entry...d=MIGR-5084140](http://www-947.ibm.com/support/entry...d=MIGR-5084140) ) and cannot proceed. I can use bios to boot different disks, but none of the options gets me to windows anymore after the latest ubuntu update.

I have rEFIend installed, but atm it can only choose the same boot options as grub that ubuntu made. I think because it just copied the settings from ubuntu.

I'd like to boot to windows as well.

---

### Post by Mandibela on 2013-12-19
Oh yeah. I've got an USB3 external disk. The Ubuntu is installed on the 60GB SSD, part of which is used by the windows as swap location. Other disks have windows-related stuff, OS on C and programs on D when looking from windows.

---

### Post by Mandibela on 2013-12-19
I made a new thread, sorry didn't realise [SOLVED] is not a good place to continue. Delete this thread plz =D

---

### Post by oldfred on 2013-12-19
It looks like you have mixed BIOS installs and UEFI installs. And you have a gpt drive with hybrid MBR/gpt - sdd.
 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)
Cannot help on sdd as that is a violation of your terms of use and forum policy.

 [http://www.ubuntu.com/about/about-ubuntu/conduct](http://www.ubuntu.com/about/about-ubuntu/conduct)
[http://ubuntuforums.org/misc.php?do=showrules](http://ubuntuforums.org/misc.php?do=showrules)

You cannot dual boot BIOS and UEFI installs except from UEFI/BIOS menu. Once you start booting in one mode only installs in the same mode can be booted.

Do not run any auto fixes from Boot-Repair as it will try to install one boot loader to every drive. You want different ones in every drive.

---

### Post by oldfred on 2013-12-19
Merged threads.

---

### Post by Mandibela on 2013-12-19
Fixed. I removed all but the windows 500GB disks, used the windows CD to boot to repair command prompt, did:
```
c:\>bootrec /fixmbr

c:\>bootrec /fixboot

c:\>bootrec /rebuildbcd

bcdboot c:\windows
```
and restarted.

Ubuntu starts normally, by the order specified in UEFI. If I want win, I interrupt the boot and choose it via UEFI myself.

Only problem is that when another grub update comes, update-grub will put grub on every HDD containing an OS. Can I block that?

---

### Post by oldfred on 2013-12-19
Update grub's memory on where to reinstall.

 #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

