---
title: "GRUB won't boot Win2K"
date: 2004-10-12
forum: Installation &amp; Upgrades
---

### Post by RayG on 2004-10-12
I installed Ubuntu on a computer with an existing W2k install on hda1. Grub boots Ubuntu without problems. But when I try to boot Windows, I get an error that states that the file system is unrecognized. 

As root I ran   ## grub-install /dev/hda ##      to reinstalled GRUB. I get no error messages, but there was no change behavior. 

I reinstalled the windows boot loader using the W2k install disk repair console. I then used a linux install disk to boot into Ubuntu and then reinstalled GRUB again. No joy. I see no errors in the GRUB config file. 

Any ideas out there short of installing LILO?

Thanks,
RayG

---

### Post by emperor on 2004-10-13
Please post your grub menu.lst  so we can see the Win2000 boot entry.

---

### Post by theantix on 2004-10-14
RayG:

It sounds to me like you might be encountering a common problem --  is the Grub error message like this?

"Booting "Windows"
root (hd0,0)
Filesystem type unknown Partition type 0x7
Chainloader"

If so, to resolve this, in your BIOS set your hard drive setting to LBA instead of [auto] and reboot.  

If that isn't the problem, please post the exact text of  the error message you are getting.

Cheers,
-Ryan Thiessen-

---

### Post by arctic on 2004-10-14
also make sure that you didn't type wrong partition numbers in grub. lilos hda1 is hd0,0 in grub. ;)

---

### Post by drunken-wallaby on 2004-11-15
just played around today with replacing win2000 with win xp (had to!) and killed grub in a way. I can't get winxp which is installed in /dev/hda1 to boot with grub. I get the famous 0x7 error, double checked that I use LBA in the bios settings. the entry for windows in my menu.lst is: ```
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1
``` and the error is ```
"Booting "Windows NT/2000/XP"
root (hd0,0)
Filesystem type unknown Partition type 0x7
Chainloader"
```

anyone?

---

### Post by RayG on 2004-11-17
Thank you for all the replies. Due to life in general I had not checked back on this thread in a while. My Win2K partition is still dead. My grub entry for windows and the error message I get are exactly as Drunken-Wallaby shows. My hard drive setting in BIOS actually was "AUTO" and I changed it to LBA, but I still get the same error.  

I have attempted to reinstall windows on that partition. The windows installation routine goes through it motions of copying files to the partition, but when it reboots, up pops GRUB again. So, windows does not overwrite the MBR on installation? Booting from the windows system disk and going to the recovery console I can run fixboot and fixmbr to reinstall the windows boot files and mbr. Guess what GRUB doesn't mind that either! It's still there! 

This is all quite odd behavior. I have installed and removed a number of linux distributions and this is unprecedented strangeness. I really need to reinstall windows, as this is my son's computer and he needs MS Office for his homework. I am at the point of just wiping the whole drive and starting from scratch. 

I hesitate to go through the agony of reinstalling the entire win2k system and then risk it all again. I just loathe installing windows and then rebooting and then the motherboard chipset drivers and rebooting,  and then the video drivers ( pause to reboot),  and printer drivers, and MS Office, (don't forget to reboot) and a secure browser, (reboot as necessary) and the spyware removal software, (feel free to reboot), ..... infinitum...... And then come my son's games....don't get me started. :-)

Any wisdom is appreciated.  I sure would miss Gnome 2.8 if I can't safely reinstall Ubuntu. Thanks again for the help so far.

Best regards to you all,
RayG

---

### Post by KiwiNZ on 2004-11-19
Do you a Phoenix Bios?
 If you check your disk options you may have the following options
 CHS
 LBA
 LARGE
 AUTO
 
 If so try setting to LARGE , I have found this successful when setting to LBA has failed as in your case.
 
 Cheers

---

### Post by RayG on 2004-11-19
Success at last. It finally occurred to me last night, that when I last did a clean install of Win2k on this machine, I backed up the partition using Norton Ghost. I had put the backup on a FAT32 partition, which I use for data interchange between Windows and Linux. I had forgotten about it. After using Ghost to restore the partition, GRUB now boots windows. 

Thanks again for all of the help.
RayG

---

