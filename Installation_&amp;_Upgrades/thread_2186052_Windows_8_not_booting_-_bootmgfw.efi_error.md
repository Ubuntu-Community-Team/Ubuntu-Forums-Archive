---
title: "Windows 8 not booting - bootmgfw.efi error"
date: 2013-11-05
forum: Installation &amp; Upgrades
---

### Post by irina_cat1 on 2013-11-05
Hello,

I can't boot into Windows 8, but I CAN boot into Ubuntu 13.10 (which I installed from a 13.04 live usb and then updated). I'll try to explain what I did as simply and understandably as I possibly can:

1. Had normal, working, preinstalled Windows 8.
2. Wanted to Install Puppy linux and used the windows installer. This didn't work and I tried multiple times, until at some point I manually cancelled (task manager I think) the process and ended un with a GRUB I could not remove.
3. Used Boot-Repair in an attempt to fix this.
4. I don't know why, but this made the laptop unable to boot into Win8: .the computer would go into recovery mode, but I think it couldn't access the partition, since not even refresh/clean reinstall work and I can't access it using Ubuntu now.
5. In an attempt to make it work again, I enabled/disbled UEFI and Secure Boot a few times and tried Boot-repair again. Nothing worked. I also tried Fedora and it wouldn't even get to desktop from the live USB. I also tried uEFInd, but this didn't work either. I also tried bootrec.exe/fixmbr, fixboot, scanos, rebuildbcd  and 'bootsect /nt60 c: /force /mbr' and 'bcdboot c: \windows /s c: . Also tried replacing c with d in the last 2. Didn't work.
6. Now Windows gives says it can't load the bootmgfw.efi image, but at least shows up in GRUB. A recent use of BootRepair made a lot of windows-related .efi entries appear in my GRUB menu. I think I tried to use them all and none worked, giving that same error.

Here are the links BootRepair produced along the way:

[http://paste.ubuntu.com/6348764/](http://paste.ubuntu.com/6348764/)
[http://paste.ubuntu.com/6349407/](http://paste.ubuntu.com/6349407/)
[http://paste.ubuntu.com/6349519/](http://paste.ubuntu.com/6349519/)
[http://paste.ubuntu.com/6349626/](http://paste.ubuntu.com/6349626/)
[http://paste.ubuntu.com/6365737/](http://paste.ubuntu.com/6365737/)

I'm not very good with terminal commands and also not familiar with the inner workings of UEFI, Ubuntu and Windows 8 so I don't know what to try next or if there's any aditional information I should give. Ask and I'll try to give more detail if I can find it.

If anyone has any idea how to solve this, please help.

---

### Post by oldfred on 2013-11-05
It looks like you have an Ultrabook that has the small SSD using Intel SRT. The SRT uses RAID which then causes all sorts of issues as grub needs to be installed in the efi partition as a standard install not a RAID install. Standard desktop installer does not have RAID drivers but you do not want them anyway.

You also need to turn fast boot off as that is always on hibernation which causes major issues also. Is not Windows 8 great. :)

Not sure Puppy ever supported UEFI or even a BIOS/CSM boot from a gpt partitioned drive.

Boot-Repair does a file rename and undoing that may get your Windows working. You need that to get into Windows to turn off the fast boot or always on hibernation.

 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
If that does not work just manually copy your Windows efi file back into the efi partition.

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

You also show grub4dos which probably is from EasyBCD. You do not need that with UEFI, as you end up with too many boot managers, but some with limited UEFI find rEFInd still another boot manager useful.
UEFI is a boot manager where you can select system to boot from.
Grub2 is a boot manager where you can select system to boot from. 
EasyBCD is a boot manager where you can select system to boot from. 

But grub2 is also a boot loader and is required to boot Ubuntu.

See links in my signature. Review first two links on installing and the section on Ultrabooks.
What model Lenovo.

 Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)
Lenovo Ideapad Y500 LiveUSB Problem, also brightness
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500)
[http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

---

### Post by irina_cat1 on 2013-11-05
> **oldfred said:**
> It looks like you have an Ultrabook that has the small SSD using Intel SRT. The SRT uses RAID which then causes all sorts of issues as grub needs to be installed in the efi partition as a standard install not a RAID install. Standard desktop installer does not have RAID drivers but you do not want them anyway.

You also need to turn fast boot off as that is always on hibernation which causes major issues also. Is not Windows 8 great. :)

Not sure Puppy ever supported UEFI or even a BIOS/CSM boot from a gpt partitioned drive.

Boot-Repair does a file rename and undoing that may get your Windows working. You need that to get into Windows to turn off the fast boot or always on hibernation.

 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
If that does not work just manually copy your Windows efi file back into the efi partition.

 Windows UEFI install should  have backup of bootmgfw.efi here:
C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

You also show grub4dos which probably is from EasyBCD. You do not need that with UEFI, as you end up with too many boot managers, but some with limited UEFI find rEFInd still another boot manager useful.
UEFI is a boot manager where you can select system to boot from.
Grub2 is a boot manager where you can select system to boot from. 
EasyBCD is a boot manager where you can select system to boot from. 

But grub2 is also a boot loader and is required to boot Ubuntu.


Just wanted to reply quickly:

I have a Lenovo U310, which I think is not an Ultrabook. It does have a small SSD partition, though.

I didn't know anything had changed, so I didn't do my research before trying to nstall Puppy.

I'm not sure how to turn fast boot off since I can't boot into Windows. I think it is already though, since I can use F2 and F12. I also can't access the Windows 8 partition, so I don't know how to copy the EFI file from there. It seems that Ubuntu just doesn't detect it, even though I got the option of installing alongside Windows 8 and gparted detects it.

I don't know what a 'gpt partitioned drive' is and I hope to have time to look at the links tomorrow. Will also update this/reply with the results of Bootrepair after I try that, hopefully it will make WIndows 8 work.

Thanks for helping, I thought I'd provide some more info and/or clarification, even if just on the run.

ETA: Should I turn off Secure boot before using Bootrepair? Also, should I tick both 'restore EFI backups' and 'use the standard EFI file' or just the first? Anything else I should tick/untick in advanced options?

---

### Post by oldfred on 2013-11-05
I do not have UEFI so I am not sure what options you are seeing in Boot-Repair.
The restore standard EFI file sounds like something new. Yann does try to keep updating Boot-Repair to fix bugs or improve what it does. And UEFI is relatively new.

One other users had a U310
  lenovo u310  - install Ubuntu to part of SSD Post #19 
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

---

### Post by irina_cat1 on 2013-11-06
> **oldfred said:**
> I do not have UEFI so I am not sure what options you are seeing in Boot-Repair.
The restore standard EFI file sounds like something new. Yann does try to keep updating Boot-Repair to fix bugs or improve what it does. And UEFI is relatively new.

One other users had a U310
  lenovo u310  - install Ubuntu to part of SSD Post #19 
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

I have attached pictures of the Bootrepair options. In Grub location I also get the option 'Windows (via sb8 menu) ' instead of Ubuntu 13.10 and 'sdb3' instead of sdb2.

---

### Post by oldfred on 2013-11-06
Your screens are a lot different than my BIOS based screens. I think the use the standard efi file related to grub, but am not sure.
I know before the restore backups un-renamed the files and that should not have changed. So I would just run that. 
If not you can manually restore a copy of the orginal Windows efi file from Windows as explained in post #2.

---

### Post by irina_cat1 on 2013-11-06
> **oldfred said:**
> Your screens are a lot different than my BIOS based screens. I think the use the standard efi file related to grub, but am not sure.
I know before the restore backups un-renamed the files and that should not have changed. So I would just run that. 
If not you can manually restore a copy of the orginal Windows efi file from Windows as explained in post #2.

It asks me to disable secure boot. Do you think that's ok to do? I'm afraid not to damage Windows even further.

Also, I can't access the Windows partition, so I don't think I can restore that file manually. The only things that detect it so far are the Ubuntu installer, GRUB (though Windows doesn't boot, as I've said), gparted and bootrepair.

---

### Post by oldfred on 2013-11-06
Microsoft says you can disable secure boot. But a few systems will not boot Windows with it off, most still boot Windows ok.
       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

If you still have fast boot or the always on hibernation set then you cannot access the Windows as the Linux NTFS driver does not want to damage a system. Same with chkdsk which is required after any resize.

To install on Windows 8 you have to follow these instructions.

 Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

---

### Post by irina_cat1 on 2013-11-07
> **oldfred said:**
> Microsoft says you can disable secure boot. But a few systems will not boot Windows with it off, most still boot Windows ok.
       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

If you still have fast boot or the always on hibernation set then you cannot access the Windows as the Linux NTFS driver does not want to damage a system. Same with chkdsk which is required after any resize.

To install on Windows 8 you have to follow these instructions.

 Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

I got the prompt in the attached image. Yes or no?

ETA: I did disable SecureBoot.

---

### Post by oldfred on 2013-11-07
I think Boot-Repair overdoes the rename but the backup is important.

The rename is for those UEFI that have been modified to only boot the Windows efi file. So Boot-Repair renames grub2's shim file that has the Microsoft signing key to have the Windows name.

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

---

### Post by irina_cat1 on 2013-11-07
> **oldfred said:**
> I think Boot-Repair overdoes the rename but the backup is important.

The rename is for those UEFI that have been modified to only boot the Windows efi file. So Boot-Repair renames grub2's shim file that has the Microsoft signing key to have the Windows name.

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

So I click no? Because I've ticked "Restore EFI backups" and it seems odd to say yes to this.

---

### Post by oldfred on 2013-11-07
Did you do the backups before?

Boot-Repair does work well, but I am a belt & suspenders type when it comes to computers and would have full backups of Windows and the efi partition separately.

         The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

---

### Post by irina_cat1 on 2013-11-07
> **oldfred said:**
> Did you do the backups before?

Boot-Repair does work well, but I am a belt & suspenders type when it comes to computers and would have full backups of Windows and the efi partition separately.

         The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

I did have a full backup, but now Windows won't boot and I can't access the partition. It does boot in recovery mode, but none of the options have worked so far.

I'll just click yes for now and if it doesn't work go for no.

ETA: For yes: [http://paste.ubuntu.com/6377268/](http://paste.ubuntu.com/6377268/)

It also says: 'The boot files of [The OS now in use - Ubuntu 13.10] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))'. However, Ubuntu boots so I think I should ignore this. Any thoughts?

---

### Post by oldfred on 2013-11-07
Boot-Repair has that far from start warning, but I have not seen a UEFI system need any changes. It was some BIOS, grub and maybe only external drives or USB driver conflicts caused issues.

You now show two efi partitions. You can only have one. Use gparted and remove boot flag from sda5. Not sure if that is only error now or not.

You do have Intel SRT or related versions on your sda, the 24GB SSD.

---

### Post by irina_cat1 on 2013-11-07
> **oldfred said:**
> Boot-Repair has that far from start warning, but I have not seen a UEFI system need any changes. It was some BIOS, grub and maybe only external drives or USB driver conflicts caused issues.

You now show two efi partitions. You can only have one. Use gparted and remove boot flag from sda5. Not sure if that is only error now or not.

You do have Intel SRT or related versions on your sda, the 24GB SSD.

I should read up on SRT then.

If I click on no this is the report: [http://paste.ubuntu.com/6377575/](http://paste.ubuntu.com/6377575/) 

One of the GRUB options now boots into Onekey Recovery (which I had installed in Windows) but that either can't find my image (when I try to use the user backup option) or gives this error when I try to use the initial backup option: 'This program cannot find the system partition because its structure is incorrect. You may have to recreate the partition to continue.' Ideas?

ETA: BootRepair also said something about making my bios boot from sda2 (or sdb2 which makes more sense to me). I should have written that down.

ETA2: In Gparted, sda5 has label Windows8_OS. Should I still remove the flag?

ETA3: Also, there is an exclamation mark to next to sdb4. I will attach a picture. Also attached is an image with the /dev/sda Gparted screen.

---

### Post by oldfred on 2013-11-07
Gparted cannot see the RAID or Intel SRT or whatever version of Intel that is. Gparted does not work with RAID currently and may not ever work with the special RAID that Intel is using. So the errors on sda, your SSD are normal. If you turn off Intel in Windows or UEFI and remove meta-data then gparted will see it. 

Also the msftres partition is a required Windows partition that is unformatted space. It is where Windows will just hide DRM info or other Windows data like serial numbers. Since unformatted gparted cannot see it or complains it is unformatted. So that is normal.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

 Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

In BIOS systems you boot boot flag on the Windows partition with the boot files. And you can only have one boot flag per hard drive. With UEFI/gpt gparted used boot flag to show that the efi partition is the efi partition which is somewhat like the boot partition but in gpt is really different. But you can only have one efi partition per drive. So yes remove boot flag from Windows system partition, it should only be on the FAT32 real efi partition.
May also be why your one key has issues as two efi partitions will confuse it.

Boot-Repair says boot from efi partition, but in UEFI you normally see the efi partitions folder names or ubuntu or Windows.

  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

### Post by irina_cat1 on 2013-11-07
I'm writing this from Windows 8. Thanks a lot!

Ok, so here's what happened:

1. Removed flag in GParted.
2. Rebooted, went to OneKey, rebooted from there because I realized I should probably trythe normal boot first.
3. Selected Windows, left the room and found it in Ubuntu.
4. Restarted, chose Windows, and as far as I can remember it said preparing recovery too first, but I'm not sure, but then it booted into Windows and so far doesn't exhibit any symptoms of damage beyond repair.
5. Now Windows 8 seems to work, and I think Ubuntu does too, but I haven't exactly extensively checked either.
6. I'm now trying to make some backups, one of which will hopefully be on USB.

Yeah, so thanks again and I hope I won't run into any other problems.

I understand I should now mark this as solved. Is this right?

Also, any way I can shrink Ubuntu's partition now? I want to turn most of it into a backup partition, for obvious reasons. I suppose GParted is an obvious choice, I just don't know if that + format to NTFS or FAT32 is all right to then use it with Windows and not damage things.

---

### Post by oldfred on 2013-11-07
Generally use Windows tools for Windows and Linux tools for Linux.
If resizing the Windows system partition use Windows.
For new partitions use gparted as Windows may want to convert to dynamic which does not work with Linux.

If backing up just your files then you can use NTFS, but Linux has permissions and ownership, so any Linux system file or settings will lose those settings if backed up to NTFS.
I do suggest a shared NTFS data partition but fast boot hibernation may still create issues even with that. Not sure if in Windows you can unmount d: drive before shutdown or not. I stopped my XP install a couple of years ago.
Do not use FAT32 as it will not save a file over 4GB, or movies or backups that are one large file. And FAT32 does not have a journal so recovery or repair can be difficult or impossible. FAT32 is ok for smaller devices or partitions as then journal does not add much.

---

### Post by irina_cat1 on 2013-11-09
Managed to make the partition and the backup, hopefully all will be well with the laptop from now on. Thanks for helping.

---

