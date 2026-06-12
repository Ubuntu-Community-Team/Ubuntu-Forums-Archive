---
title: "Samsung Ativ Book 9 Plus UEFI Install Troubles"
date: 2014-06-22
forum: Installation &amp; Upgrades
---

### Post by qepltab on 2014-06-22
Hi there,

I'm trying to install 14.04 on a new Samsung Ativ Book 9 Plus (NP940X3G-K06US, specifically), and I've run into some issues. First and foremost, secureboot and fastboot are turned off.

I can successfully install Ubuntu when the BIOS is in CSM, however UEFI isn't playing ball; no matter what I try it refuses to recognise the bootloader. I would be hapy with CSM, but there appear to be a few driver issues in it (the resolution does some odd stuff).

Here are my attempts so far. Start with an empty, unformatted drive. I've tried all combinations of the following.

**Making a new partition table and:**
 - Follow the [general wisdom]("http://ubuntuforums.org/showthread.php?t=2203824") and partition the drive as such:
    sda1: 100MB FAT32 EFI boot stuff
    sda2: 124GB ext4 mounted as /
    sda3: 4GB swap space
 - Partion without the EFI boot partition

**Then installing with the BIOS:**
 - Set to CSM and then switching to UEFI
 - Set to UEFI

**Running boot-repair (from the boot-repair image on a liveUSB), and:**
 - Doing a simple-repair
 - Doing an advanced repair and manually specifying the EFI boot partition.

And yet the damn bootloader still isn't being found. Does anyone have experience with this particular model of laptop, or any thoughts in general about how to get it recognised?

A few questions:
 - Does it matter what type the partition table is? (msdos or gpt)
 - Is it necessary to have a separate EFI boot partition?
 - Should I ditch grub altogether and use an alternative bootloader?

Cheers

---

### Post by grahammechanical on 2014-06-22
We do not need to turn off secure boot. Since the release of Ubuntu 12.10 we have been able to install Ubuntu with secure boot on. Have you seen this wiki page?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

It says this

> [COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.[FONT=inherit][/FONT]
[*=left][FONT=inherit]if the other systems (Windows, GNU/Linux...) of your computer are installed in Legacy (not-EFI) mode, then you must install Ubuntu in Legacy mode too. Eg if your computer is old (<2010), is 32bits, or was sold with a pre-installed Windows XP.[FONT=inherit][/FONT][/FONT]

[*=left]if Ubuntu is the only operating system on your computer, then it does not matter, you can install Ubuntu in EFI mode or not.
[/LIST]


It seems to me that you are installing Ubuntu in CSM mode and then wanting to switch to UEFI mode and I do not think that is possible. Choose one or the other. Ubuntu will install on an MSDOS partition table and on a GPT partitioning scheme. 

> [COLOR=#333333][FONT=Ubuntu]To install Ubuntu in EFI mode:[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit]Use a 64bit disk of Ubuntu ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"))[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Use a supported version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI[SecureBoot]("https://help.ubuntu.com/community/SecureBoot") appeared in 12.10 and 12.04.2.[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "[Identifying if the computer boots the HDD in EFI mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")" paragraph below)[FONT=inherit][/FONT][/FONT]

[*=left]Then:[FONT=inherit][/FONT][FONT=inherit][/FONT]
[LIST]
[*=left]nothing special is required if you use the automatic installer of Ubuntu ("Install Ubuntu alongside others" or "Erase the disk and install Ubuntu"). Important: if you have a pre-installed Windows and you want to keep it, do not choose "Erase the disk and install Ubuntu".[FONT=inherit][/FONT][FONT=inherit][/FONT]
[*=left][FONT=inherit]if you use the manual partitioning ("Something else"), the difference is that you will have to set the /boot/efi mount point to the EFI partition. And if there was not any EFI partition on your HDD, you first will have to create it (see the "[Creating an EFI partition]("https://help.ubuntu.com/community/UEFI#Creating_an_EFI_partition")" paragraph below).[/FONT]
[/LIST]
[/LIST]


> [COLOR=#333333][FONT=Ubuntu]If you are manually partitioning your disk in the Ubuntu installer, you need to make sure you have an EFI partition set up.[FONT=inherit][/FONT][FONT=inherit][/FONT][/FONT][/COLOR]

[LIST]
[*=left]If your disk already contains an EFI partition (eg if your computer had Windows8 preinstalled), it can be used for Ubuntu too. Do not format it. It is strongly recommended to have only 1 EFI partition per disk.
[/LIST]


Regards.

---

### Post by oldfred on 2014-06-22
UEFI requires gpt partitioning. And then if installing in BIOS mode you need the 1 or 2MB unformatted bios_grub partition for grub to install correctly. And if converting now or sometime in the future you need the efi partition. UEFI spec says it should be first partition, although most installs do not seem to have it first, but it still is near beginning of the drive. It  must be FAT32 formatted with the boot flag. It can be 100 to 300MB. Basic UEFI boot does not need much but if adding features in the future you may want a bit more.

Some older Samsungs had major issues - bricked computer as UEFI would not clear memory and if UEFI NVRAM got too full it just crashed and could not be fixed. Originally blamed on Linux, but proven to also happen with Windows.

Some other Samsungs:
       Installing Ubuntu 13.10 on a Samsung ATIV Book 9 Plus
[http://ubuntuforums.org/showthread.php?t=2203824](http://ubuntuforums.org/showthread.php?t=2203824)
Update UEFI/BIOS helped see ports and other issues.
How to: Dual boot Windows 8 and Ubuntu 13.10 on Samsung 900X3E 
[http://ubuntuforums.org/showthread.php?t=2176559](http://ubuntuforums.org/showthread.php?t=2176559)
Samsung Ultrabook Windows 8 & Ubuntu & recovery boot Disk view of partitions post 7
[http://ubuntuforums.org/showthread.php?t=2097690](http://ubuntuforums.org/showthread.php?t=2097690)
Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)
 SAMSUNG Series 3 NP365E5C-XXXXX laptops 
[http://ubuntuforums.org/showthread.php?t=2120763](http://ubuntuforums.org/showthread.php?t=2120763)
Samsung series 5 UltraBook, erase Windows & install to SSD
[http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/](http://schoolsplay.wordpress.com/2012/11/22/install-ubuntu-linux-on-a-samsung-series-5-ultrabook-with-ssd/)

Some vendors modify UEFI to only boot Windows. So there are several work arounds on renaming files to make UEFI think it boots Windows when the file it boots is really grub or shim for secure boot. Not sure if Samsungs need that or not.

---

### Post by qepltab on 2014-06-23
Thanks for the replies,

*@grahammechanical*, I was trying to convert a CSM installation to a UEFI one because of how that 13.10 thread does it, despite it being a bit weird. I was also attempting to do a normal UEFI install. Good to hear we don't need secure boot, I've reinstalled with it turned on.

*@oldfred*, I've read about that brick issue but it looks like it only affects older models so hopefully I'm safe.

So I've now reinstalled with secure boot on, and choosing the "wipe everything and install Ubuntu" option from the installer. The drive looks like this:

 - sda1: 512MB FAT32 partition with the boot flag,
 - sda2: Main partition,
 - sda3: Swap space, 4GB.

And the bootloader still isn't being recognised. What are the other possible causes here? If UEFI has been modified, what's the procedure for tricking it into booting?

Also will boot-repair be of any use here? Or since it's already UEFI'd can I stop running it after every reinstall.

Cheers

---

### Post by Bucky Ball on 2014-06-23
Boot repair may be of use there, but follow oldfred's advice carefully before going there ...

---

### Post by Patricia_Konarski_ on 2014-06-23
Yes, boot repair is your friend in a time of need like this (and that is if you have maintained your boot repair--otherwise you will be out of look, so let's keep our fingers crossed).  All the best.

Patricia Konarski Tucson
--Freelance editor and owner of Patricia Konarski Literary Services of Tucson

---

### Post by oldfred on 2014-06-23
If you do not have the Windows boot files, the 'buggy' UEFI Windows file rename that Boot-Repair does will not work. But you can manually add the Windows folder and a copy of shim with the Windows file name.

Create a Windows folder in efi partition so your efi partition has these. Mount may be different depending on which system you mount it from.

 /EFI/Boot
/EFI/Microsoft
/EFI/ubuntu

Update: **Not recommended anymore**, better to use note below and see next post. Or use rEFInd.
Copy shimx64.efi into Microsoft folder in a /Boot folder and rename to 
efi\Microsoft\Boot\bootmgfw.efi 

Then see if you can boot the Windows entry in UEFI menu. You may have to reboot a couple of times for UEFI to add it to its menu as we have not run efibootmgr to register it in advance..

Other methods. Many like graphical boot that rEFInd uses. Some rename bootx64.efi in the /efi/Boot folder.
Also see D: below to rename in UEFI the shim to be Windows. Most vendors have modified UEFI to check only description in UEFI menu entry.

      
 **Systems that only boot Windows from UEFI. Work arounds -Often Sony & HP, maybe others**
Backup entire efi partition before making changes.
**A:** Manually rename files either  efi\Microsoft\Boot\bootmgfw.efi and/or /EFI/BOOT/BOOTX64.EFI to be grub or shim
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
some find renaming  /EFI/Boot/bootx64.efi  to be shimx64.efi or grubx64.efi 
Then booting device or hard drive works also.
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109)

   **B:**Boot_Repair renames Windows bootmgfw.efi. But cannot boot Windows from UEFI only from grub menu 
Always say no until proven that you only can boot Windows entry from UEFI menu.
buggy-kernel detected. Do you want to activate [Backup and rename Windows EFI files]? yes (if any choice fails, please retry with the other)
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

   Any rename either manually or with Boot-Repair will need to be redone after a Windows update as it will restore Windows files.

   **C: **Edit Windows BCD, one Alternative to Boot-Repairs rename to make shim have Windows name.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

   **D:** If Description has to be Windows then change UEFI description.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

   **E:** Some install rEFInd which seems to be another workaround and has nice boot icons.
[http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)

---

### Post by John_Novak on 2014-08-24
oldfred's post here was very useful! Registered to the forums just to respond to this... I just got a model similar to the parent (NP940X3G-K04US in my case); after many frustrating attempts, I finally got it to boot successfully with a clean Ubuntu-gnome 14.04 install by the following:

[list]
[*]After clean install from USB key, reboot into live session from key
[*]mount /dev/sda1, should see EFI directory
[*]create subdirectory EFI/BOOT
[*]from adjacent EFI/ubuntu directory, copy grubx64.efi to EFI/BOOT
[*]from adjacent EFI/ubuntu directory, copy shimx64.efi to EFI/BOOT/BOOTx64.efi
[*]power down, remove install USB key, reboot
[/list]

I should note that I had secure boot, fast boot, and boot password disabled in BIOS at this point, booting in UEFI mode; I have not yet verified whether this was necessary (docs suggest not required, other than having fast boot disabled while using USB key). Also, not positive that both items required in EFI/BOOT directory; did verify that shimx64.efi copied to BOOTx64.efi alone was not sufficient, however. (Went with both, because USB key has both and boots successfully.) I had tried many things before this point, including fiddling with efibootmgr to delete menu entries from previous attempts, so it's possible that affected things; however, based on the observed behavior, I think that unlikely.

Hope this is helpful to someone! And thanks again, oldfred, your post was the lifesaver after several days of attempts to get this working!

--John N.

---

### Post by Bucky Ball on 2014-08-25
John, thread is well old and pretty well in a coma, but thanks for sharing. ;)

---

### Post by rvu95 on 2014-11-23
I've tried to installed Tusty with Secure Boot ON, and the OS can't be loaded after then. :(

---

