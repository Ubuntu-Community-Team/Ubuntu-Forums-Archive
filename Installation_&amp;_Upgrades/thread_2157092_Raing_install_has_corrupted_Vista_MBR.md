---
title: "Raing install has corrupted Vista MBR"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by pekatete on 2013-06-24
Hi could someone help please.
I have installed the fairly new Ubuntu raring and have had my Vista MBR corrupted somehow. After reading some threads (here and everywhere) I managed to install and run boot-repair which gave the following result for the Vista partition:
> 
sda2: __________________________________________________________________________
      File system:       ntfs
     Boot sector type:  Grub2 (v1.99-2.00) 
    Boot sector info:  Grub2 (v1.99-2.00) is installed in the boot sector of                         sda2 and looks at sector 353995848 of the same hard                         drive for core.img, but core.img can not be found at                         this location. No errors found in the Boot Parameter                         Block.

Operating System:  Windows Vista
     Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe                         /ubuntu/winboot/wubildr /ubuntu/winboot/wubildr.mbr


1. I am sure there is something wrong with the boot files section ther-in but I am at a loss to resolve the same. Any help?
2. When I try to load cfdisk, it give the error "FATAL ERROR: Bad logical partition 6: enlarged logical partitions overlap"

Notwithstanding, I am able to boot into Ubuntu (both directly to the installed version AND onto the live system). Any pointer(s) on how to resolve this?
(PS. i have been, until yesterday, still running jaunty without issue but thought to upgrade to the latest and having been up till late last night trying to resolve this, the experience is really not nice!)

---

### Post by ajgreeny on 2013-06-24
Let's see the whole of the boot-info file please.

You can just give us the postbin link that you will have been given after running the script, and that may give us a lot more detail of what the situation really is.

---

### Post by Mark Phelps on 2013-06-24
From the wubildr entries, it looks like you tried to install Wubi -- which does not work anymore, as they have dropped it staring with Ubuntu 13.04.

---

### Post by oldfred on 2013-06-24
Like ajgreeny, it would be better to have the link to the full BootInfo report as there may be other issues.

But what you show has grub installed to the PBR of a NTFS partition boot sector. All NTFS partitions have to have NTFS in the PBR not anything else. But NTFS does keep a backup which if you only installed once can be used to restore the NTFS PBR.

Fix for most, a few have other issues, better than windows fix in many cases as it also fixes other parameters:
If win7 use small 'system reserved' NTFS partition instead of the partition where windows was installed for win7
This has instructions on using testdisk to repair the install of grub to the boot sector for windows from Ubuntu or Linux LiveCD.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)

OR:
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

---

### Post by pekatete on 2013-06-25
Thank you all for the responses, and apologies for not responding earlier (I am new to this forum and had expected to receive an email when a response was made, but none appeared!)
I have been busy trying to rectify my predicament in the meantime, and I seem to have done more damage to my system than before, however, I will save you the details of that and just provide you with my LATEST link to the boot-repair (BootInfo?) log.
[http://paste.ubuntu.com/5799685/](http://paste.ubuntu.com/5799685/)

---

### Post by oldfred on 2013-06-25
There is a user setting somewhere that you can get emails on every new post. We upgraded Forum to vB4, so some of the details may be a bit different.
 Guide to Forum features:
[http://ubuntuforums.org/showthread.php?t=2054969](http://ubuntuforums.org/showthread.php?t=2054969)
[http://ubuntuforums.org/showthread.php?t=1006656](http://ubuntuforums.org/showthread.php?t=1006656)

You have several other issues, so good to see BootInfo report.
But you need to use testdisk as posted above to try to recover the PBR or partition boot sector of sda2. Generally you never install grub2's boot loader to a partition with BIOS/MBR configurations, just to a drive. Or you only install grub to sda, sdb etc, never sda1, sda2, sdb3 which are partitions. Only exception may be if you had another grub installed and then you still would never install to a NTFS partition's PBR.

You also have more than one boot flag on sda. Grub does not use Boot flag, but Windows has to have a boot flag on the NTFS partition you boot from, want to repair,  or install Windows into. One boot flag per hard drive and on sda you should only have boot flag on sda2. You can use gparted or Disk utility to remove flags. You can also use command line:

 set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda

You are missing two of the three boot files Windows needs.
      
 Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

I have seen users just copy /bootmgr and a BCD from a repairCD or other install and then manually edit the BCD to be correct for the install with bcdEdit.

 How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)

Or after fixing boot flags you should be able to run Windows repairs. But it may take three times with the auto repair and will then overwrite grub in the MBR. So you then can use Boot-Repair or manually reinstall grub2's boot loader to the MBR.

Not sure if anything else is an issue, but lets fix those first. I do not see an overlapping partition error?

Do you have a Vista repairCD or flash drive?
If you have another Vista machine.

 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by pekatete on 2013-06-25
oldfred, thanks for the response.
I have not had a chance to look at setting up the emails yet but will do later (more pressing issues while I have your attention!)
1. I have managed to remove the boot flags from all partitions bar sda2 as advised using fdisk.
2. I am missing the **Backup BS** option in testdisk as per intructions so I have chosen **Rebuild BS** - result is ***Extrapolated boot sector and current boot sector are identical***. I assume I need to reboot before I can re-run this, which I will do. 
3. In the meantime, I do NOT have a Vista recovery disk (infact my Vista recovery partition sda1 is no longer visible / bootable, which it was yesterday!)
I will update as soon as I finish rebooting and re-running testdisk.

---

### Post by pekatete on 2013-06-25
Just the update to testdisk - I re-run it after rebooting and I still do not have the Backup BS option, so I am on a dead-end on that for now.

---

### Post by oldfred on 2013-06-25
I think the Rebuild BS creates a valid NTFS partition boot sector but it is XP type. I once used a Windows 7 repair flash drive to run chkdsk on my XP install, it worked better than XP's chkdsk, but converted the PBR to Vista/7 type. With teskdisk you can compare PBR's and structure was different and in plain text the new PBR had bootmgr and the backup (XP one) had ntldr. So I restored backup and XP then worked better.

When grub is in PBR, Windows will not even run chkdsk on the NTFS partition. But once converted to XP NTFS then you can run Vista/7 chkdsk and it will fix it. But you still need the other boot files. And none can really be done from Linux. Or you need a Windows repair disk. Not sure what third party repair tools there are. 
 
May be able to run chkdsk from Hiren's boot CD. (mini xp.) But not sure if just XP?

---

### Post by pekatete on 2013-06-25
OK I think I just hit a brick-wall.
1. I have most definitely corrupted both my MFT and bootsector for sda2 (and possibly sda1 too) - I gleaned this from the testdisk manual (both MFTs are identical and so are the bootsectors, though I know now to be incorrect). Leaves me with the single option of running chkdisk from a Vista rescue disk, however, since I can no longer boot into sda1 either, I am at a loss, albeit the online rescue disk for $19 .... (but that would be a cost on Ubuntu)
2. I have an XP pro hardisk that I have attached via USB to my laptop (I was trying to boot into XP in the hope of running chkdisk from there), however, since it was not originally installed for this laptop, it bombs on every attempt to boot-up! The same disk has a recovery partition that I think would be a better try to boot up, but does not get installed by **sudo update-grub**, any ideas how to achieve that?
3. Could I get ANY Vista installation's boot sector to work on my harddrive? For example, if someone with Vista (or Win 7) did a **sudo dd if=/dev/sda2 of=vistambr.mbr bs=512 count=1** and sent me the resultant **vistambr.mbr** file, would that work on my install?
The last one seems a far fetched one, but gotta try something ......

---

### Post by oldfred on 2013-06-25
No as 512 includes the partition table. Your issue is not the MBR but the PBR. Linux can install a Windows type boot loader to the MBR.

 [http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair](http://www.cgsecurity.org/wiki/Advanced_NTFS_Boot_and_MFT_Repair)


Can you take a screenshot of testdisk. It should look like the link I posted above. I posted mine also.
You need to get something that is NTFS related not grub into the sda2 PBR. Rebuild BS should work if backup is not valid. It may say the grub version is valid but from testdisk view it may be, but only the backup was.

There are some other Windows repair tools not sure how much they do.
 Also has chkdsk and some other Windows repairs in free version:
[http://www.partitionwizard.com/features.html](http://www.partitionwizard.com/features.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

EasyBCD also does some repairs.
[https://neosmart.net/](https://neosmart.net/)

You really should have a repairCD for the same version of every operating system you have installed. And when making major changes have good backups.
      
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

My attachment is XP but one Bootsector is Windows 7 and the other is XP, so that is why they are different.

---

### Post by pekatete on 2013-06-25
Screenshot as requested, I will look at the links you've provided as well.
PS. Browsing through the Vista partition (using testdisk), there is a file in the root of the drive named BOOTSECT.BAK with a size of 8192. Could I dd this into MBR? (I know you mentioned PBR, just wondering)

[ATTACH=CONFIG]244173[/ATTACH]

---

### Post by pekatete on 2013-06-25
I think I may be making some progress.
1. I went ahead and re-populated /dev/sda2 mbr with using  
```
sudo dd if=vistambr.mbr of=/dev/sda2 bs=446 count=1
```
and this is the link to the latest BootInfo [http://paste.ubuntu.com/5800192/](http://paste.ubuntu.com/5800192/) (no reports of errors). I have backed up the old (corrupted) MBR just in case.
2. The worry I still have is that ```
sudo update-grub
``` still does not pick up the partition.
I am going to re-boot to see if re-running this after a reboot will make a difference.

PS. the vistambr.mbr is basically the BOOTSECT.BAK file that I found in the root of the partition.

---

### Post by pekatete on 2013-06-25
Just to reiterate I must have stumbled upon something here.
Having rebooted, I still can not get **sudo update-grub** to add the Vista partition, however, having copied part of the file **BOOTSECT.BAK** to the MBR, I can now even mount the partition inside ubuntu (which was not possible before)!
My next step will be to completely purge grub and then re-install it (rather than a plain update) and hopefully it will recognise the Vista partition and add it to the boot options. (At this point, I am pretty confident if I removed grub and rebooted, I'd boot into Vista straight .....! but a step at a time for now)

---

### Post by oldfred on 2013-06-25
Grub still will not find it until you have all 3 Windows boot files needed to boot Windows. I think grub just looks for the two you are missing, the one's in [COLOR=#ff0000]RED[/COLOR].

Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

The boot flag also has to be on sda2 for any Windows repairs or direct Windows booting. Grub does not use boot flag to boot anything and actually just jumps to the Windows PBR in the partition with the boot files (the one's in [COLOR=#ff0000]red[/COLOR]).

To better understand how Windows boots and actually all BIOS/MBR systems. It is just that grub does not use PBR like Windows. Other older Linux boot loaders like Lilo do use PBR.

       Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by pekatete on 2013-06-26
Thanks for clarifying that oldfred. I was missing the fact that they were two files.
1. Now where do I get those two files? I can not seem to see these anywhere on neither the Vista nor Ubuntu partitions.
2. If like you mentioned they are on the recovery CD, can these not be rebuilt from the Vista partition?

edit: I have now got hold of the winload.exe.file which resides on the Vista partion, now how do I recrete the first file aka [COLOR=#ff0000]/bootmgr /Boot/BCD [/COLOR]

---

### Post by pekatete on 2013-06-26
OK I found both files on the Vista partion
1. I copied** bootmgr** to the root of my Linux partition, i.e /bootmgr
2. I created a directory **Boot** in the root of the Linux partition and copied the file **BCD** to that directory.
3. i re-run **sudo update-grub** and also **sudo boot-repair** but grub did not pick up the Vista partition.
Here is my latest Bootinfo: [http://paste.ubuntu.com/5800896/](http://paste.ubuntu.com/5800896/)

PS. I noticed that boot-repair works on the boot rather than Boot directory (caps on). Do I need to copy the BCD file into the boot directory?
I also have the other matter of un-installing grub from the boot sector of sda6. I managed to remove grub from sda2 by over-writing the mbr, would this be same with sda6? Should I simply zero it out?

---

### Post by oldfred on 2013-06-26
Windows is not case sensitive so it can be any /boot. In fact some have installed grub to Windows and created /Boot and /boot which are different in Linux but then Windows sees duplicates & quits working.

BootInfo report still is not showing the bootmgr & BCD? Uusally it finds them but occassionly it does not. But then grub2's os-prober will not find them either. Is bootmgr at the root or top level of Windows? and /boot off that top level with the BCD? Not sure if Windows has other files? BootInfo only shows the files required for booting.

Do not worry about sda6's PBR. You would not normally use it and unless running the BootInfo report would not know if it was zeros or had some random data. In fact when users move partitions, the PBR often ends up with random data and BootINfo report shows it as unknown boot loader. There are ways with dd to zero it out, but than can be dangerous as any typo causes even more issues.

---

### Post by pekatete on 2013-06-26
oldfred, you have been such a godsend!
i am not over the hill yet, but here is where I stand as of now.
The two files you were reffering to I actually copied to the root folder of the linux partition! having copied them back to the windows folder, grub now recognises the windows partition and adds it to its menu. One small problem for now, grub thinks its a recovery and NOT an ntfs. i suppose that is because I got the BCD file from the **Windows/Boot/DVD/PCAT** folder. There is a **Windows/Boot/PCAT** folder, but it only contains the*** bootmgr*** and ***memtest.exe*** files plus locale folders (which only contain MUI files).

I am going to reboot to see whether booting into Vista will force some kind of sanity check (hopefully it does).

PS. And here is the latest BootInfo (with the two files showing!): [http://paste.ubuntu.com/5801964/](http://paste.ubuntu.com/5801964/)

---

### Post by pekatete on 2013-06-26
Just to update, the reboot failed to get me into Vista.
1. Are there any issues being caused by the error: **Warning: extended partition does not start at a cylinder boundary**. I believe this is caused by the linux partition /dev/sda6 starting at 278005760 whereas its parent extended partition /dev/sda3 starts at 278005758. Oddly though, the preceeding Vista partition /dev/sda2 ends at 278003764
2. Do we know where Vista stores its runtime **bootmgr** and **BCD** files?
3. I still can not get the recovery partition to show in grub, from the bootinfo, any ideas what i need to do. (For the record, I ran gparted and it never recognised the partition, not sure whether it is because it does not support vfat out of the box, or as it claims, the partition has errors!)

PS. the last bootinfo is as per my last post

---

### Post by oldfred on 2013-06-26
Any reference to cylinder boundary does not matter. Hard drives have not used cylinders since hard drive went over 8GB. Back then we had to manually set in BIOS CHS or cylinders, heads, sectors. They converted to LBA or large block allocation.
New 4K drives work much better if the boundary is on 8 sector setting which all new partitions tools do. But if you have Vista and older drives that does not matter either. 

If you do not have any other access to Windows repair disks, you could download the legal copy of Windows and install it. It gives you 30 days before you have to pay, but then you either pay or uninstall.

Did you try EasyBCD or any of the other Windows repair tools?

---

### Post by pekatete on 2013-06-26
OK, that was another false dawn. Looks like I am running out of options here.
1. Both the bootmgr and BCD files seem to relate to the recovery folder, as such, I always get an error whenever I try to boot into Vista.
2. I am still unable to gain any access to the recovery folder (/dev/sda1). On that front, I ran fdisk on each partition and on sda1, sda5 and sda6 fdisk indicated the same error (can not recall exactly what it said) and suggested writing the table to fix the error. After reboot, the error is gone on all partitions. In addition, cfdisk will not start with the error: **FATAL ERROR: bad logical partition 6: enlarged logical partitions overlap**. I think I'll have to open a new thread for this one, though I believe it has everything to do with my predicament.

Any more help out there?

---

### Post by oldfred on 2013-06-26
Did you do any changes to partitions. The BootInfo report you ran looked ok, plus it normally gives that error also.

Sometimes testdisk which actually still works with CHS rounds incorrectly and makes extended partition too large. But I thought we did not write a new partition table from testdisk but just a new PBR? 
But you can use fixparts to fix that error. If something else often required direct partition editing with sfdisk.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957](http://ubuntuforums.org/showthread.php?t=1667614&p=10367957#post10367957)
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)
First backup partition table, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt

    
You still need bootmgr & BCD for Windows to work. Did you find copies? IT may be hidden in some of the Windows repairCD?

---

### Post by pekatete on 2013-06-26
Thanks for the help. I'll look into that and update you. For now, I think I'll have some kip so that I am fresher tomorrow. 
Incidentally, just been reading this [http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598) aka overlapping issues!

---

### Post by oldfred on 2013-06-26
I link to that thread, by the creators of bootinfoscript which is now part of the BootInfo report you run. They really understand the inner workings of the system.

But fixparts was created later to repair many issues without having to directly edit the partition table.

---

### Post by pekatete on 2013-06-27
Another update AND a bit of a break-through!
1. I managed to restore access to the restore partition by running ntfsfix on /dev/sda1 - unfortunately, the same trick did not work for /dev/sda2 which is my main Vista partition.
2. The does not seem to be another BCD file on the restore partition, though it does contain a bootmgr file (at the moment, I assume it, like the last, will only boot to the restore).
3. My laptop is a Viao and the restore does not seem to give access to a Windows prompt for me to be able to run fdisk /mbr on /dev/sda2. Any idea, if at all, whether there is a way to circum-navigate around the lack of a boot prompt, or even a way to simply run fdisk or chkdisk in windows restore on a Viao recovery?
I'll keep plugging away and update as and when.

---

### Post by oldfred on 2013-06-27
If you can copy the bootmgr from sda1 to sda2 and then manually create a BCD or use Neosmart's EasyBCD to rebuild a BCD. I think the free version will do what you want. 

[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)
 
Some advanced BCD rebuild, Vista post #17 on:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD)

---

### Post by pekatete on 2013-07-01
Again, just an update .... this nightmare it seems has a way to go yet!
1. Copying the bootmgr from sda1 to sda2 did not do the trick.
2. EasyBCD runs under windows, and at the moment I do not have ANY  bootable windows environment, not even a bootable CD / DVD. I  incorrectly assumed that the Sony Viao recovery partition would give me  access to a command prompt, but there seems to be not option for this.
On the same topic, I notice that you can provide options to the recovery  boot process on a Viao recovery boot partion when you boot into it via  pressing F10. I am hoping that there is an option you can specify to  avail a command prompt, any ideas or hint what that option would be?

---

### Post by oldfred on 2013-07-01
If you have a one key recovery program, you can run that. But realize that most totally erase drive and restore it to "brand" new or as purchased. You have to back up all your data, restore that, run all the updates and reconfigure. That is why a full image backup of Windows is a good idea.

EasyBCD does have separate repairCD. They used to be free, but now they charge. I would look at the other Windows repair tools as they may have BCD recovery.

[http://www.inference.phy.cam.ac.uk/prlw1/computing/winpe.shtml](http://www.inference.phy.cam.ac.uk/prlw1/computing/winpe.shtml)
[http://www.microsoft.com/en-us/download/details.aspx?id=10333](http://www.microsoft.com/en-us/download/details.aspx?id=10333)

[http://social.technet.microsoft.com/Forums/windows/en-US/29a3ccc5-636e-421e-8b19-8253c4d79243/winloadexe-is-missing-or-corrupt-recover-cd-does-not-boot-problem-solved](http://social.technet.microsoft.com/Forums/windows/en-US/29a3ccc5-636e-421e-8b19-8253c4d79243/winloadexe-is-missing-or-corrupt-recover-cd-does-not-boot-problem-solved)

---

