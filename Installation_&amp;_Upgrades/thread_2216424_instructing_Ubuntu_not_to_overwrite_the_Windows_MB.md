---
title: "instructing Ubuntu not to overwrite the Windows MBR"
date: 2014-04-11
forum: Installation &amp; Upgrades
---

### Post by archp2009 on 2014-04-11
I have been the past few days recovering my multiboot Windows bootloader with the help of the EasyBCD support forum.  I was concerned about my former Grub (I have Mint and Ubuntu installed but presently inaccessible) overwriting the Windows MBR if I restore it with Supergrub.  The problems with the mutlboot menu began with Windows 8.1 apparently corrupting the multiboot menu.  I ending up choosing to reformat Windows XP knowing what the result would be but not being able to successfully recover the XP by any of the other options that I was familiar with.  One of the moderators on Neosmart Forum (EasyBCD) said this to me: "You can instruct the Linux install not to overwrite the MBR but to place grub in the Linux partition. That will protect the existing MS multiboot. You can then add a Linux  entry to the BCD and EasyBCD will automatically locate it and set up  everything necessary." I assume Neosmart (EasyBCD) are not expert in the Linux side of things.  Can you point me to a step by step guide for doing this from the Linux Ubuntu viewpoint.  I don't know if this can be done with a SuperGrub recovery disk or if I will need to reinstall Ubuntu.  Thanks in advance for any assistance.

---

### Post by oldfred on 2014-04-12
Grub does not recommend that it be installed to a partition's PBR or partition boot sector. It does not really fit. So it converts to blocklists or hard coded addresses which may change on grub update or even a fsck or anything that may move a file.

You get messages like this:
 grub-setup -v /dev/sda6
Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force 

Windows is not designed as a multiple boot system. It will boot multiple installs of Windows but most recent install takes over an moves all its boot files into the one primary NTFS partition with the boot flag. Then BCD or boot.ini is updated with additional Windows.
EasyBCD tries to modify BCD to chain boot to grub. It actually adds grub4dos and an entry in BCD or boot.ini to grub4dos to chain to the grub in the PBR. That actually was not so bad with grub legacy but not so good with grub2. Some in forum have post it does work. But be prepared to reinstall grub after major grub updates.

      
 [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Grub is designed a a multiple boot manager as well as a Linux system boot loader. So it just adds Windows to its menu and chain loads to the Window PBR, just like a Windows boot loader in the drive's MBR chain loads to the PBR.
      
 Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Do not install grub2 to any NTFS partition's PBR. That damages Windows.

---

### Post by archp2009 on 2014-04-14
Thanks for the prompt reply and the great links.  You didn't comment about using Supergrub.  Is there any hope of recovering my old Grub bootloader with Supergrub after reformatting my drive c?  One thing I did notice was that the drive letters Windows has assigned to my drives now is different than it was originally.  This is one good thing (I suppose it's good) that came out of the recovery process.  Windows XP is now C which is the way I expected it to be originally, but somehow during the process of installing the OS's the first time,  XP ended up being K instead of C.  I don't know if that contributed to the loader getting corrupted and I don't know if the fact that XP is C now but was K before is going to matter to Grub.  The OS's are actually installed to the same partitions as before.  Would it be safer reinstalling Ubuntu than trying to use Supergrub?

---

### Post by oldfred on 2014-04-14
Supergrub is a useful tool to have. It is for booting when grub is corrupted or you have other issues. But you should correctly install a boot loader once you boot with Supergrub.

Windows normally sees the c: drive as the version of Windows you boot into. If you have more than one Windows then that is d: or some other letter.

You should not need to reinstall Ubuntu, just repair grub. But I always suggest using grub2 in drive's MBR, not other boot loaders. But part of that is I know grub2, and do not know the others.

---

### Post by archp2009 on 2014-04-14
Gparted Live Disk showed XP as /sda1 so I presume that's where the MBR is.  I installed Mint before Ubuntu so it would appear that sdc1 (13gb) is the Mint Partition sdc5 (4.8gb) is a swap partition, sdc6 ext3 (5.59gb) and sd8 ext4 (7.47gb) and  sd9 ext4 (7.26gb) must be all Ubuntu partitions (I don't remember why I partitioned it that way and/or which is home/root/etc.)  When I ran supergrub 2 and chose "locate grub even if mbr is overwritten" it gave me two options hd1 msdos8 or hd1 msdos1 for two grub config files.  Would I be correct in choosing the hd1 msdos1 file.  I have no idea what msdos1 means.  I understand that after I choose one of these two grubs it will ask me for the location of the Linux OS.  Do I choose /sdc1 (mint) or the first of the 3 ubuntu partitions sdc6?  I had my grub customized using grub customizer with a splash image.  I don't know how that will complicate the chances of recovery.  One of the problems I had with Grub2 in installing first Mint and then Ubunut is that it did not detect all the Windows OS's.  One of the options linked to the multiboot windows loader, so what I had going was a two menu system - one to choose between mint, ubuntu or windows, and if I chose windows I would get to choose one of the Windows OS's.  That worked and i got used to it, but I would have preferred having all OS's on the one menu. I don't know how hard that will be to do manually with Grub2.

---

### Post by oldfred on 2014-04-14
Best to see all the details.
 
Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)


MBR is the first sector of a hard drive and before any partitions. Windows also uses the PBR or the first sector of the NTFS partition for more boot code.

hd0 is first drive, hd1 second etc
msdos1 is first partition, msdos2 is second partition etc and that is with MBR or msdos partitioning not the new gpt partitioning.
It used to just be in grub as (hd0,1) but they added msdos or gpt to tell which partitioning the drive is.

If you have mulitple drives you can have different installs in each drive and different boot loaders in the MBR of each drive. Then in BIOS choose to boot another drive. 

You can have each Windows in grub if you have installed both Windows in primary partitions. Windows only boots from the drive in BIOS set as boot and on that drive the NTFS partition with the boot flag. All other installs put there boot files in that one partition, so grub can only find one install.  But if you move boot flag or change to other drive and do Windows repairs, The repair can add boot files to the second install. Then grub can find the second install.

---

### Post by archp2009 on 2014-04-14
Thanks for your continued guidance.  I burned a boot repair disk.  This is the url of the boot info:  [http://paste.ubuntu.com/7252717/](http://paste.ubuntu.com/7252717/)  The recommendation to set the bios to boot the 320gb disk is contradictory to the present location of the mbr.  Drive c is the first 137gb partition of the 1tb disk which has the XP on it.  The 320gb disk is the one with the Mint and Ubuntu and a partition of data (movies) but no Windows OS at the present time.  BTW, the drive management in XP gives false information about allocated and unallocated space and drive capacity for the 640gb drive.  Using third party utitlities such as Easeus Disk Manager gives the correct information for that drive.  One of my drives, the 1tb drive, has shown evidence in the past of failing using WD diagnostic software (lots of bad sectors) but no issues since I updated the mobo drivers, so I'm keeping my fingers crossed.  I went back and used the WD diagnostics again since and it showed passed and no errors at least in short test.

---

### Post by oldfred on 2014-04-14
Do not run Boot-Repairs auto fix. It is fine for those with one drive or only one system, but you want to keep the Windows boot loaders on both sda & sdb.

But you do want to install grub to sdc's MBR and change BIOS to boot sdc. Not sure which system you want in control. sdc1 Mint or sdc8 Ubuntu. With Boot-Repairs advanced choice you can choose system and choose drive to install to or sdc.

You also have mixed Windows boot files in sda1, sda2 & and no boot files for Windows 7 in sdb1. I might copy bootmgr & BCD from working system into sdb1. You may need to change BIOS to boot sdb temporarily and run Windows repairs to make it directly bootable.

       Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

You also have grub4dos's /grldr folders or files. That is for grub4dos to chainload to another boot loader and is usually installed by EasyBCD. With multiple hard drives and multiple MBRs you do not need EasyBCD.

      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by archp2009 on 2014-04-15
Thanks again,  All this is a bit overwhelming to me at this moment.  I will need some time to inwardly digest your comments.  Re-installing Ubuntu feels at least 10x easier to me. I guess I'm thinking only of the negative aspects and magnifying them in my mind.  All the Windows systems are working fine at this moment.  I may give it some time to consider.

---

### Post by archp2009 on 2014-04-19
> **oldfred said:**
> 
You also have mixed Windows boot files in sda1, sda2 & and no boot files for Windows 7 in sdb1. I might copy bootmgr & BCD from working system into sdb1. 

I have been hesitating this past few days for your comments to settle in my mind before deciding what I should try next. I'm surprised that if there are no boot files in the Win 7 partition that I can still successfully boot into Windows 7 from my present windows boot menu.  Does that not surprise you? Will you provide guidance on a reinstall of the Ubuntu 13.10 if I prefer that option?

---

### Post by oldfred on 2014-04-19
Windows is not a multiple boot system. It actually only boots from one drive as set in BIOS and from one partition as set with boot flag on that drive. All other installs move boot files into that one boot partition on the boot drive. Newest version seems to take control, or update BCD with all the installs. Mixed XP & later versions with BCD may have issues if XP is installed last.

This is Vista but applies to all BIOS type installs of Windows.
       Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)
BIOS/Grub/Ubuntu  boot process
[http://www.thegeekstuff.com/2011/02/linux-boot-process/](http://www.thegeekstuff.com/2011/02/linux-boot-process/)

You should not have to reinstall Ubuntu, just grub if desired. Or you may want 14.04 since that just came out.

---

### Post by archp2009 on 2014-04-23
Sorry, my reply of a couple of days ago did not show up here.  Basically, I was requesting whether you'd be kind enough to walk me through this process assuming I want the upgrade.  If would probably be simpler for me if you just gave me the first step or two from where I am now.  Then I can get back to you and confirm that I have completed to that point.  Thanks again.

---

### Post by oldfred on 2014-04-23
Have you fixed the Windows boot file issues?

Are you reinstalling 13.10 or 14.04. Have you downloaded ISO, created flash drive and booted in live mode to check how well it works?
       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)

I always create partitions in advance or reuse a partition that I had before. I then have to use Something Else, and choose change to change the existing old partition to be the new install. And then choose with combo box at bottom of screen on which drive to install grub boot loader into.

some screen shots from my install.

---

### Post by archp2009 on 2014-04-23
Thanks again for the prompt reply. I need to take this one step at a time.  When you said last week, "You also have mixed Windows boot files in sda1, sda2 & and no boot files for Windows 7 in sdb1. I might copy bootmgr & BCD from working system into sdb1. You may need to change BIOS to boot sdb temporarily and run Windows repairs to make it directly bootable," this sounds to me like a number of items to be fixed.  Could you elaborate on the first one and how to go about fixing that one first.  I think the first problem you mentioned were that there were mixed Windows boot files in sda1.   That sounds like the XP partition.  What files do I need to delete and/or add to this partition?  BTW, the system currently boots only from one of the three drives currently listed in the BIOS. The others fail to find an OS.

---

### Post by oldfred on 2014-04-23
Windows only boots from the drive set as bootable in BIOS and the partition with the boot flag (with BIOS/MBR).
Each added install adds its boot files to that one partition on the BIOS boot drive. But you can add boot files to every install and then grub can directly boot each Windows.

       Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

So make sure your XP install has the boot.ini and other XP files.
And make sure every Windows 7 install has bootmgr & BCD files or folders. Just copying files & folders to installs missing those files may work, or it may need Windows repairs.

If you do run Windows repairs, Change BIOS to boot that drive and change to add boot flag on that install of Windows. Only one partition can have boot flag per hard drive. Auto repair requires 3 passes to complete everything.

      
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

To understand how Windows boots. Shows Vista, but all BIOS based Windows work like this:
      
 Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by archp2009 on 2014-04-24
I used a search utitlity called Everything to search for the boot files/folders you listed.  Here are my results:

boot.ini found on XP and Vista x86
ntldr found on XP and Vista x86 and Movies2 \NST
NTDETECT.COM found in XP in root and in 2 folders,  found in Win7 in EasyBCD profile, found in Win8 in EasyBCD profile, found in Vista x64 in EasyBCD profile, found in Vista x64 in root and in EasyBCD profile
bootmgr found in root of Win8.1, Win XP, Movies2, Win8, Vista x86
Boot folders found in all Windows partitions
BCD found in boot folder in Vista x86, XP, Win7, 

What do I need to do from this?

---

### Post by oldfred on 2014-04-24
I do not know Windows search, but it is having boot files in every Windows install. Look at your bootinfo report.
All the /grldr as grub4dos usually from EasyBCD.

Your sda1 shows this which has both XP & the boot files for Vista/7/8 and grub4dos:
           Boot files:        /boot.ini /grldr /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

sda2  had both XP & Vista/7 boot files and grub4dos:
Boot files:        /boot.ini /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /ntldr 
                       /NTDETECT.COM

sda3: has not bootmgr nor BCD
Boot files:        /Windows/System32/winload.exe

sdb1 has not bootmgr nor BCD
Boot files:        /Windows/System32/winload.exe

sdb2 has not BCD:
Boot files:        /grldr /bootmgr /Windows/System32/winload.exe /grldr

Your installs in sdb5 & sdb6 are not directly bootable as Windows can only boot from primary partition, so to boot a install in a logical partition you need to boot thru a primary partition.

With all these versions of Windows & different boot file I am also confused. This is a very complex multi install system of Windows. Please go back and review the multibooters site in post #2.

---

### Post by archp2009 on 2014-04-24
[COLOR=#0000ff]Thanks again.[/COLOR]


> **oldfred said:**
> I do not know Windows search, but it is having boot files in every Windows install. Look at your bootinfo report.
All the /grldr as grub4dos usually from EasyBCD.

Your sda1 shows this which has both XP & the boot files for Vista/7/8 and grub4dos:
           Boot files:        /boot.ini /grldr /bootmgr /Boot/BCD /grldr /ntldr 


                       /NTDETECT.COM

[COLOR=#0000ff]Would you please tell me again which files are Vista/7/8 only and can be safely deleted from this Vista partition.[/COLOR]


sda2  had both XP & Vista/7 boot files and grub4dos:
Boot files:        /boot.ini /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /ntldr 
                       /NTDETECT.COM

[COLOR=#0000ff]Would you please tell me again which files are not needed for Vista and can be safely deleted from this Vista partition.[/COLOR]

sda3: has not bootmgr nor BCD
Boot files:        /Windows/System32/winload.exe

[COLOR=#0000ff]Would you please tell me again which files are not needed for Vista and can be safely deleted from this Vista partition. Also which files Vista should have and could be copied from another working Vista system.[/COLOR]


sdb1 has not bootmgr nor BCD
Boot files:        /Windows/System32/winload.exe

[COLOR=#0000ff]Would you please tell me again which files are not needed for Win7 and can be safely deleted from this XP partition.[/COLOR] [COLOR=#0000ff]Also which files Win7 should have and could be copied from another working Win7 (x64) system.[/COLOR]


sdb2 has not BCD:
Boot files:        /grldr /bootmgr /Windows/System32/winload.exe /grldr

[COLOR=#0000ff]Would you please tell me again which files are not needed for Win8/8.1 and can be safely deleted from this XP partition.[/COLOR] [COLOR=#0000ff]Also which files Win8 should have and could be copied from another working Win8/8.1 (x64) system.[/COLOR]


Your installs in sdb5 & sdb6 are not directly bootable as Windows can only boot from primary partition, so to boot a install in a logical partition you need to boot thru a primary partition.
[COLOR=#0000ff]
The whole 640 gb drive sdb shows up as unallocated space when I use gparted live cd today.  That did not happen before but there does seem to be something wrong with that disk.  In Easeus I can see the same drive OK. It has 5 partitions the 4th is Win8.1 and the last (5th) is data only[/COLOR].

With all these versions of Windows & different boot file I am also confused. This is a very complex multi install system of Windows. Please go back and review the multibooters site in post #2.
[COLOR=#0000ff]
What do you think the odds are that, if I install the new version of Ubuntu, I will be unable to access Windows at all.  The last 3 or 4 installs I did, one of the options took me into the windows boot menu.  I was able to remove the other Windows entries and leave the one that booted into the Windows multiboot menu.  I then had one menu booting into another which was good enough for me.[/COLOR] [COLOR=#0000ff]The only problem I am having with the Windows at the moment is restore points in Win8 and 8.1 being deleted on rebooting.

[/COLOR]

---

### Post by oldfred on 2014-04-24
Post #8 shows which are XP and Which are Vista/7/8 boot files.

I would backup any files you delete as you may only have one Windows BCD that has your correct configuration. And I do not know which one.

You need all three XP files in the XP partition to directly boot XP.
You need all three Vista files in the Vista partition to directly boot Vista.
With Windows 7, you may or may not have the separate Boot partition which would have bootmgr & BCD. But if no boot partition then you need all three files in the Windows 7 partition. 
If an install is in a logical partition, no need to copy boot files into it except perhaps as a backup. Windows cannot directly boot from a logical partition.

Linux may not see Windows 8 if you leave it hibernated and it always is hibernated. This also can be an issue in your case with just Windows.
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

I would suggest choosing one hard drive as your Ubuntu drive that has no Windows installs you want to keep and make it Ubuntu only. Many suggest then disconnecting all Windows drives to prevent issues. But you can use Something Else or manual install, but have to create partitions for /, /home swap or others and assign those partition to those mounts.

I show my install to an existing partition that had an old test install. Combo box at bottom still shows grub boot loader still being installed to sda. Normally you would want to change that to the same drive as Ubuntu install with mulitple drives.

---

### Post by archp2009 on 2014-04-24
The only thing I don't understand about the boot process is the idea of the active partition.  I thought every partition becomes active after an OS is installed on it.

---

### Post by archp2009 on 2014-04-24
I notice in Easeus Partition Manager that the option is there to right click and go "convert to primary" for the Win8.1 partition which is now logical.  Do you recomend that?

---

### Post by oldfred on 2014-04-24
Windows calls it active partition. In Linux we see a boot flag.
Windows boots from MBR. But MBR is tiny so the Windows boot loader in MBR looks for the active partition which has boot flag and more Windows boot code in the PBR or partition boot sector to continue to boot. Generally the PBR just calls out ntldr for XP or bootmgr for Vista/7/8 to continue booting. 
Only the active partition with Windows is bootable, but you can have one per hard drive, so BIOS then controls which drive is bootable.

If you convert Windows 8.1 to primary does that wipe out your other partitions on that drive? And do you care? It looks like swap & an ext3 partition are before the Windows 8, so they will probably be deleted. Not sure exactly how Easeus does it.

---

### Post by archp2009 on 2014-04-24
The conversion to pirmary for the Win 8.1 completed successfully - took less than a minute - only effect was loss of restore points - but that has been happening a lot for Win8 and 8.1 anyway, so could be another cause.

---

### Post by oldfred on 2014-04-24
What version of Windows do you primarily use. And then why all the other installs?
May be best to houseclean down to one primary and one secondary. XP is now obsolete.

The can you devote one drive to Ubuntu?

---

### Post by archp2009 on 2014-04-25
It's difficult to say which one that I primarily use.  Although its's finally no longer supported I have definitely spent most of the last 15 years using XP.  The last time I had my system crash I had resolved to use only XP but in less than 2 weeks I realized I needed a 64-bit OS for certain software and that's when I found myself adding the various OS's again. I enjoy the learning experiences.  The truth is that it has become an addiction.  Unfortunately, I panic when things up wrong and end up depending on people like yourself who become like online friends to me. I have no every day friends in real life.  I apologize for that.

---

### Post by oldfred on 2014-04-25
I started with DOS and used XP both at home and work. While I installed Ubuntu in 2006 and promised myself I would shutdown XP, it took years as I had one app that I had upgraded from DOS days. Ubuntu equivalent was not as good. After several years the hassles of booting, maintaining, updating XP exceeded that advantage and I decided the Linux application was good enough. It had improved over the years but still not as good a the Windows version.

---

### Post by archp2009 on 2014-04-29
I had a crash yesterday and three of my six windows volumes did not boot.  I got them back with system restore and manual BCD rebuild command.  As I may have mentioned before, I think my 1tb drive is failing.  I have manually created a bcd on the Win7 volme.  I have since downloaded Ubuntu 14.03 which is supposed to be supported for 5 years.  The dvd boots fine.  I have been having problems with restore points being deleted by XP, Vista and Win7, so I have used regedit to set vulnerable volumes offline.  That didn't work in Vista so I used disk drive disable in device manager in both the Vista volumes to protect the 640gb drive which has the two Win8 volumes.  Should I make all drives online and enabled before installing Ubuntu?

---

### Post by oldfred on 2014-04-29
If drives are connected the os-prober will find them.
If they are not connected and you later connect them, you can run this to add Windows to grub boot menu.
sudo update-grub

But Windows normally installs all its boot loaders into the one drive set as boot by BIOS and the partition set as boot with the boot flag or active setting in Windows.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

---

### Post by archp2009 on 2014-04-30
Thanks for the reply.  I assume by connected you mean connected to the motherboard, do you?  I assume it makes no difference that they are disabled in device manager or set offline via the windows registry offline by the key /dosdevices/d: off in a particular Windows OS, does it?

---

### Post by oldfred on 2014-04-30
Any Windows settings should not matter.
But if you can in BIOS disable them, then they should not be seen.

---

### Post by archp2009 on 2014-04-30
Of course, when I install the Ubuntu 14.03, I want all the drives to be seen.  I have already deleted the Ubuntu partitions and now have 20gb of unallocated space.  There is already one 4gb swap partition set when I installed Mint (not included in this 20gb) so I assume, being that I never user hibernation, that I can get by without any more swap space.   What type and size of partitions would you use under the "something else" option in the Ubuntu partitioning section?  I assume it will ask if I want to write Grub to the MBR on sda1.  If so I will answer yes, will I?   Should I also click back and choose to write Grub to a boot partition on the Ubuntu drive as well?

---

### Post by oldfred on 2014-04-30
If you only have 20GB, just install / to that partition.

You always install grub to the MBR or sda, never to any NTFS partition as that damages Windows. Only if using another grub2 as your primary boot might you install grub to the same partition more so it is not used to boot.

---

### Post by archp2009 on 2014-04-30
Installed successfully.  Only thing the Mint won't load.  I get the Mint logo and a line of text across the top of the screen reading Keys: Continue to wait Press S to skip Mounting, or M for mnaual recovery.  I tried M and it said home directory does not appear to exit.   Suggestions?

---

### Post by oldfred on 2014-04-30
Did Mint have another partition for /home? And is that still there?
If just corrupted you can run fsck to fix it.

May be best to see details.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by archp2009 on 2014-05-01
I'm thinking the obvious answer is that I inadvertently deleted the home partition for Mint when I was preparing to install Ubuntu.  I'll have to try that boot disk again to see what it says now.

---

### Post by archp2009 on 2014-05-01
The new boot info report is at [http://paste.ubuntu.com/7372158/](http://paste.ubuntu.com/7372158/)
Can you tell anything from that?  Should I delete the Mint partition/s and reinstall it as well?

---

### Post by oldfred on 2014-05-01
This looks like Ubuntu now:
 # /home was on /dev/sdc7 during installation
UUID=b1fe2cc7-32e3-4866-ac8b-5d96b411db9c /home           ext3    defaults        0       2

I would install grub2 to the MBR of sdc and put Windows boot loaders in sda, and keep Windows boot loader in sdb. And set BIOS to boot sdc.

You also need to make sure grub reinstalls to correct drive on major updates.
      
 
#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by archp2009 on 2014-05-01
[COLOR=#0000ff]Thanks for the reply.  I have typed between the lines in blue.[/COLOR]

> **oldfred said:**
> This looks like Ubuntu now:
 # /home was on /dev/sdc7 during installation
UUID=b1fe2cc7-32e3-4866-ac8b-5d96b411db9c /home           ext3    defaults        0       2

[COLOR=#0000ff]Can you tell whether or not I deleted it for Ubuntu?[/COLOR]

I would install grub2 to the MBR of sdc and put Windows boot loaders in sda, and keep Windows boot loader in sdb. And set BIOS to boot sdc.

[COLOR=#0000ff]Do you mean during reinstallation of Mint?  I did not get a question regarding where Grub was going to be installed when I installed Ubuntu.  It just reported what is was doing during installation.  In my BIOS I get names for my 3 drives that do not tell me which is which.  How do I ascertain which is which by looking at the names in BIOS?[/COLOR]

You also need to make sure grub reinstalls to correct drive on major updates.
      
 
#To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

[COLOR=#0000ff]These lines are in the info report, are they?[/COLOR]

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

---

### Post by archp2009 on 2014-05-01
Mint is reinstalled an all is well.   Thanks so much for your kind suppot over the past couple of weeks.

---

### Post by archp2009 on 2014-05-01
Is Ubuntu Gnome 3http://ubuntugnome.org/download/  installed on top of Ubuntu 14.03 or is it an alternative version of Ubuntu?  Do you rcommend it.  I'm not a big fan of the icons down the left sde of the screen.

---

### Post by oldfred on 2014-05-01
I prefer fallback which has worked well with 12.04. It is the old gui look like Ubuntu was with gnome2.
 [http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)
Kansasnoob on flashback/fallback in Saucy, Quantal and Raring
[http://ubuntuforums.org/showthread.php?t=1966370&p=12857225#post12857225](http://ubuntuforums.org/showthread.php?t=1966370&p=12857225#post12857225)
Sixth, if you begin with an installation of Ubuntu GNOME, you'll find a  login option for GNOME Classic but it should NOT be confused with the  older classic/fallback/flashback sessions! The new GNOME Classic session  truly is GNOME Shell with some cherry-picked extensions added to  provide a "classic" look but it is NOT configurable in the same way as  "Flashback"!

[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)
[https://wiki.gnome.org/GnomeFlashback](https://wiki.gnome.org/GnomeFlashback)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12859103#post12859103](http://ubuntuforums.org/showthread.php?t=2090021&p=12859103#post12859103)
[https://mail.gnome.org/archives/gnome-announce-list/2013-September/msg00093.html](https://mail.gnome.org/archives/gnome-announce-list/2013-September/msg00093.html)
[http://packages.ubuntu.com/saucy/gnome-session-flashback](http://packages.ubuntu.com/saucy/gnome-session-flashback)

But I have not installed flashback (fallback) in 14.04 or with gnome. 

 seems like more issues with 14.04 depending on what details you like or might want to change.
Flashback/fallback in 14.04 Kansasnoob
Installing the package 'gnome-session-flashback' does exactly the same thing as installing the package 'gnome-panel'.
[http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477](http://ubuntuforums.org/showthread.php?t=2090021&p=12994477#post12994477)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002](http://ubuntuforums.org/showthread.php?t=2184682&p=12986002#post12986002)
[http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487](http://ubuntuforums.org/showthread.php?t=2184682&p=12971487#post12971487)

---

### Post by archp2009 on 2014-05-01
Thanks for this.  I will try to install the package 'gnome-session-flashback'  Actually, I burned a disk for the Ubuntu Gnome 14.03 and was trying to install it on a new partition.  Easeus shows only one primary and 4 logical partitions on that disk.  Easeus does not show (as Gparted does) that the 4 logical partitions are all on the one extended partition.  Is this a problem?  When I tried to install Gnome I could not get the button to "install" or "continue" after attempting to add another logical partition. I was also surprised that "primary" partition was not available.   I tried a second time and this time I was asked up front if I wanted to dismount other unspecified volumes on the disk.  Is doing this a problem?

---

### Post by archp2009 on 2014-05-01
Disk Management in Windows Vista shows 4 primary partitions and one logical. Perhaps I could change the new partition back to logical.  The Ubuntu partitioner did not show it as primary.

---

### Post by oldfred on 2014-05-01
Do not change partitions with Windows or add partitions.
Windows does not correctly see Linux partitions and just forgets to write them if it does a rewrite to the partition table. Usually a big hassle but can be recovered with testdisk. And I am sure it is a bug that Windows will not fix. 
Also if you create partitions with Windows it may convert to dynamic partitions which do not work with Linux at all.
Use Windows partition tools to shrink NTFS partitions.

I understood some of the new versions of the Windows third party partition tools will create Linux partitions, but not ext4 which is now preferred.

But use gparted for all other Linux partition activities.

All logical partitions must be inside one extended partition. Some tools may not show extended but write it when updating partition table.

---

### Post by archp2009 on 2014-05-02
Thanks for this.  I can see now that you can't depend on anything not Linux when you are using linux.  I successfully added one more OS last night - Ubuntu Studio which seems to be working well.  I need to restudy Daniel Richter's Grub Customizer as it doesn't always work for simple things like font changes. Ubuntu Gnome seems to have a buggy installer - the fonts don't allow viwing of the progress windows on the bottom of teh screen.  Another one - Ubuntu Chrisitian Studio failed to write Grub but tnankfully did not corrupt the exisitng Grub.  Kindest regards.

---

