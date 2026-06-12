---
title: "grub BORKED  by openbsd install"
date: 2013-11-02
forum: Installation &amp; Upgrades
---

### Post by omniaparatus on 2013-11-02
i recently installed ubuntu 13.10[cuz 12.04 wouldnt work] alongside windows 7 on two different hdd .
64 gb kingston for windows
first half of a 1.5 terabyte drive for ubuntu

it was mostly working fine for a week until youtube videos stopped playing all the time.

then for no connected reason i tried to install latest secure version of open bsd 5.4 on a removable usb drive
it was very different than installing any other os as most options were chosen in pre windows text [command prompt]whatever you call that.
anyways install seemed to be sucessful except when i went to reboot
all i would get is a frozen computer that couldnt make it past the bios screen

when i removed the usb drive and tried to boot windows or ubuntu all i got was a command prompt saying;
error; no such device; 730f34d4-e7bc-416e-bb74-ef8ad9c18905 
entering rescue mode
grub rescue>

then i reninstalled ubuntu 13.10 and erased all old ubuntu in process hoping it would reinstall and fix grub bootloader.

it didnt!

same exact thing on bootup

grub rescue>

so what do i do now?

---

### Post by omniaparatus on 2013-11-02
even tried unhooking previois two hdd and tried booting from just usb drive

bios is set to boot from usb hdd, no change

---

### Post by fantab on 2013-11-03
You must re-install Grub, which must have been damaged by failed BSD install.
You can re-install Grub with Ubuntu DVD/USB follow the instructions on how to from the link:
[https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal](https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal)

--OR--

You can use [BOOT-REPAIR]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu") utility from Ubuntu DVD/USB. In most cases 'Recommended Repair' should suffice. However, if you have installed Grub to any other location than default then use appropriate settings.

If you run into trouble with either method run the *BootInfo-Summary* that Boot-Repair generates and post the LINK here.

---

### Post by omniaparatus on 2013-11-05
ok i tried that boot repair disk twice, once recomended mode once advanced windows option i think .
both times it said it was successful but when i goto bootup windows 7 it says bootmgr is missing?

i should mention i no longer have the drive that ubuntu install was on connected at this time. i needed to isolate them to install ubuntu13.10 on that 1.5 tb drive. which was successful but now im still trying to recover my windows 7 partition which was on a different 64 ssd kingaston drive.

ive also tried windows reapir disk

---

### Post by fantab on 2013-11-05
To restore Windows Boot, if on a separate HDD:
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Your attached thumbnails says you have WUBI... How did you install your Ubuntu? WUBI or regular dual boot? If WUBI is on Windows HDD then follow this to uninstall: [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)
You should keep the Ubuntu HDD connected other wise Windows will not boot because all the boot files will be on ubunt Hdd.

---

### Post by omniaparatus on 2013-11-05
> **fantab said:**
> To restore Windows Boot, if on a separate HDD:
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Your attached thumbnails says you have WUBI... How did you install your Ubuntu? WUBI or regular dual boot? If WUBI is on Windows HDD then follow this to uninstall: [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)
You should keep the Ubuntu HDD connected other wise Windows will not boot because all the boot files will be on ubunt Hdd.

i originally had win 7 on the 64 gb drive cuz its 90% full and ubuntu 13.10 on 1/2  the 1.5 tb drive cuz it was almost empty.
then i tried putting openbsd on a flash drive 8 gb , thats when things went all wrong. nothing would boot , only freeze up with the flash inslalled, and no other drives would boot with it pulled out

so to remedy things i reinstalled ubuntu on the compltete 1.5 tb drive while the flash and 64 gb ssd were disconnected.

now im trying to recover my win 7 install on the ssd drive. i beleive i used wubi in windows to get the ubuntu originally installed

SO I ASSUME TO KEEP THE SSD WINDOWS AND UBUNTU SEPERATED I DO THE FIRST QUOTE AND GO TO THE SEVEN FORUM TUTORIAL TO RESTORE WINDOWS BOOT ON THE SEPERATE SSD DRIVE?

---

### Post by oldfred on 2013-11-05
Boot-Repair should fix your system. If you want and I suggest Windows boot loader on Windows drive and Ubuntu/grub2 boot loader on Ubuntu drive. But Boot-Repair's auto fix will just install grub to all drives. You can uncheck auto repair and then in the advanced select an operating system and a drive to install boot loader into. Run once for each system.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

Even if you have Windows on a SSD, it needs space to work well. Normally it works best at 30% free and at 10% free you may not have enough space to run a defrag.

---

### Post by omniaparatus on 2013-11-05
> **omniaparatus said:**
> ok i tried that boot repair disk twice, once recomended mode once advanced windows option i think .
both times it said it was successful but when i goto bootup windows 7 it says bootmgr is missing?

i should mention i no longer have the drive that ubuntu install was on connected at this time. i needed to isolate them to install ubuntu13.10 on that 1.5 tb drive. which was successful but now im still trying to recover my windows 7 partition which was on a different 64 ssd kingaston drive.

ive also tried windows reapir disk

hey OLDFRED did you happen to see this post?
i ask cuz i think i did boot repair with twice already with that ubuntu boot repair disk, or am i missing something?
or did i do it wrong?

---

### Post by fantab on 2013-11-05
> **omniaparatus said:**
> i originally had win 7 on the 64 gb drive cuz its 90% full and ubuntu 13.10 on 1/2  the 1.5 tb drive cuz it was almost empty.
then i tried putting openbsd on a flash drive 8 gb , thats when things went all wrong. nothing would boot , only freeze up with the flash inslalled, and no other drives would boot with it pulled out

so to remedy things i reinstalled ubuntu on the compltete 1.5 tb drive while the flash and 64 gb ssd were disconnected.

now im trying to recover my win 7 install on the ssd drive. i beleive i used wubi in windows to get the ubuntu originally installed

SO I ASSUME TO KEEP THE SSD WINDOWS AND UBUNTU SEPERATED I DO THE FIRST QUOTE AND GO TO THE SEVEN FORUM TUTORIAL TO RESTORE WINDOWS BOOT ON THE SEPERATE SSD DRIVE?

YES. You should FIX the Windows MBR for Windows to boot on its own. Remember in BIOS/UEFI there will an option to set HDD boot priority, you should change that to boot your Ubuntu HDD first. 
After fixing Windows, I suggest, you keep all the HDD's connected then Reinstall Ubuntu. GRUB should be installed to HDD on which you have Ubuntu and in BIOS/UEFI this Ubuntu HDD must be set to boot first.

But before you do anything we'd like to see the **Bootinfo-Summary**, which Boot-Repair generates. It details your Boot process. So post the LINK to the BootInfo-summary, here.
Also do you have your System boot in UEfI or Legacy/BIOS boot? Perhaps I should have started by asking this!

NOTE: BACKUP ALL YOUR IMPORTANT DATA, preferably to external device.

---

### Post by omniaparatus on 2013-11-06
> **fantab said:**
> YES. You should FIX the Windows MBR for Windows to boot on its own. Remember in BIOS/UEFI there will an option to set HDD boot priority, you should change that to boot your Ubuntu HDD first. 
After fixing Windows, I suggest, you keep all the HDD's connected then Reinstall Ubuntu. GRUB should be installed to HDD on which you have Ubuntu and in BIOS/UEFI this Ubuntu HDD must be set to boot first.

But before you do anything we'd like to see the **Bootinfo-Summary**, which Boot-Repair generates. It details your Boot process. So post the LINK to the BootInfo-summary, here.
Also do you have your System boot in UEfI or Legacy/BIOS boot? Perhaps I should have started by asking this!

NOTE: BACKUP ALL YOUR IMPORTANT DATA, preferably to external device.


ok i am at a loss how to fix windows bootup at all. i downloaded windows 7 install disk and tried fixing mbr from command prompt and repair windows options,  with that disc but it didnt work. it says bootmgr missing when i try to boot that drive.

so i hooked up both drives and was able to still boot into ubuntu with bios set to that hdd and was able to access the windows data from ubuntu  heres that boot info summary [http://paste.ubuntu.com/](http://paste.ubuntu.com/)6371138/

then i ran bootrepair , reinstall grub version, rebooted , no windows boot option bis= 6371158

then i ran  bootrepair again, restore mbr option, still no windows boot option and wouldnt boot  computer at all if bios set to boot windows hdd bis=6371223

now what?

---

### Post by oldfred on 2013-11-06
Is this your last pastebin. easier if just clickable.
[http://paste.ubuntu.com/6371223/](http://paste.ubuntu.com/6371223/)

You show the standard 100MB (hidden in Windows) boot partition sda1, but boot script does not show boot files. You changed boot flag to main partition or sda2, but it also does not have boot files. Boot-Repair seemed to want to run ntfsfix on the NTFS partitions, but ntfsfix only does minor repairs and sets the chkdsk flag so next time Windows boots it will run chkdsk.
You probably cannot boot at all and need a Windows repairCD or flash drive. Move boot flag back to sda1 and run the Windows repairs and chkdsk on both sda1 & sda2. To run chkdsk on sda1, you may have to unhide it and assign it a drive letter as Windows normally does not let you see that 'drive' or partition.

If you have another Windows 7 system or access to one at school or work.
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

      
 Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 
Boot report did not show first two files. It could be because of partition needing chkdsk, so it could not mount it to see files or they are missing.
You can use gparted to move boot flag back to sda1 or use Windows tools to "set active" for whatever it sees as sda1.

      
 How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)
fix boot loader With screen shots from full Windows install media
[http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/](http://www.howtogeek.com/howto/32523/how-to-manually-repair-windows-7-boot-loader-problems/)

---

### Post by fantab on 2013-11-06
Your Bootinfo-Summary links are not working. EDIT: Just saw it, thanks to oldfred.

Usually when repairing Windows from install disk, it should be the same disc from which it was installed. If not then its 50-50. Is that downloaded Windows of same version and architecture?

If its getting too complicated for you, then consider REINSTALLING Windows 7 and if need be Ubuntu too. It would be much simpler, cleaner and time saving.

---

### Post by omniaparatus on 2013-11-06
thanks oldfred, hopefully something there will work.

[btw; you must be some kind of druid priest or linux guru to make sense of those bis things, lol]

if not at least i can back things up from ubuntu then reinstall windows and  maybe ubuntu too, to make a nice clean newly  installed system like fantab says.
im leaning towards the new clean install myself, just gotta go thru my storage c can to find my original install disk

---

