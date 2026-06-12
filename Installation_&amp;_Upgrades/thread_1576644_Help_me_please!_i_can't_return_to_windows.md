---
title: "Help me please! i can't return to windows"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by dilloasimo on 2010-09-17
Hi, I'm a italian boy that have a problem with ubuntu.
I install ubuntu on my netbook with wubi but now I can't return on windows.
When I restar my pc i see

GNU GRUB version 1.98-1ubuntu6

I select the part for to go in XP

Windows NT/2000/XP (loader) (on/der/sda1)

but I see the black windows with the script

error: unknows command 'drivemap'

and than

Try (hd0,0): NTFS5:

And I return to black windows that allows me to choose the part Ubuntu.
I'm sorry form my English, I don't have a good english.
I hope that someone can help me.

Thanks

---

### Post by bobc4012 on 2010-09-20
Ciao. Did you install Ubuntu (Wubi install) by running Wubi in XP or did you use the install option from the CD? If you installed from the install option on the CD, then you probably messed up your Windows XP installation. If you ran the CD while in Windows and then did a Wubi install, it should not have messed up your Windows. But if it did happen, then take your Windows XP CD (assuming you have the CD) and run it in "R" (Repair) mode. When it finishes booting the CD and you get the prompt to select the "1. Window", select it and then on the windows command line enter "fixmbr" and then enter "fixboot" (without the quotes). Assuming you still have your XP system, these two commands should restore your "Master Boot Record" and the "Sector Boot Record" and you should be able to boot back into windows. 

When you do a "wubi install", it creates a directory - "ubuntu" (some older versions created a "wubi" directory). The Ubuntu code is installed into that directory, along with the virtual disks. Wubi also adds some files (menu.lst, wubildr and wubildr.mbr) an entry to the end of the "XP boot.ini file" on the "C: HDD". This entry (c:\wubildr.mbr="Ubuntu") boots into Ubuntu. When you turn on the PC, you should see the "list" to select booting into Windows (boot.ini has the entry -  multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP ....." /fastdetect /NoExecute=OptIn" - (the ..... may be Professional, Home Edition or whatever version of XP installed). Some older versions of Ubuntu may have "grldr" on the C: drive rather than the "wubildr and wubildr.mbr". 

If you cannot recover XP using this information, you might have to re-install Windows. If you have a USB flash drive (and a USB port), you may want to see if you can access your Windows files and copy them to the flash drive. If you cannot boot into Ubuntu to do this, you can try doing it by booting the Ubuntu CD and running from the CD. If you can boot into Ubuntu on the netbook, the opening the folder, "/host" in the Ubuntu file system should "open" up your Windows files (assuming they are accessible). If you have to use the Ubuntu CD to boot, then I think the "/media" directory will have a "disk" folder that will be the HDD of the netbook. 

BTW, I am basing this on Ubuntu 8.10. Grub was changed, I believe, in Ubuntu 9.10 (or 9.04). Since I have not upgraded my Wubi installs, I am not sure what changes may have been made to the process. Also, I don't believe Vista or Windows 7 uses "boot.ini". I believe the Windows boot process changed in those versions. However, you indicated you have Windows XP. 

Buona fortuna!

---

### Post by bobc4012 on 2010-09-20
I forgot to mention, if you run XP Repair mode to restore the boot records (and, possibly, the XP system), it may install a new "boot.ini" file and you will lose the entry to boot into Ubuntu. The Ubuntu directory should still be there (on the HDD - C: drive) and the files placed by Ubuntu on the C: drive (if not, then you can find them on the Ubuntu CD and copy them). You may have to edit the "boot.ini file" (MAKE A BACKUP FIRST) - you may need to change the "View" settings in the Windows "Folder Options" to display "hidden files". If you run Ubuntu from the CD (or can boot into it), you should back up the "boot.ini" file on the "C: drive" as it should have the Ubuntu boot entry following the XP boot entry.

---

