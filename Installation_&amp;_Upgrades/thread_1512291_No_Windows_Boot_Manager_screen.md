---
title: "No Windows Boot Manager screen"
date: 2010-06-17
forum: Installation &amp; Upgrades
---

### Post by LittleWolf on 2010-06-17
Hello!

I hope I am not posting on the wrong section; I tried to do multiple searches but could not find my specific problem. Your forums are quite intimidating for me, seeing as this is the first time I try Linux and I picked Ubuntu as my distribution. I have read many guides before I decided, everything has been cleared up, backed up, defragmented and set up. 

I got Wubi since I have no partitioning experience, following this guide by psychocats:

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

Everything went just like the guide said it would at first. My problem is, once I reboot, I don't get the Windows Boot Manager screen at all; more specifically this screen:

[IMG]http://www.psychocats.net/ubuntu/images/wubilucidthumb07.png[/IMG]

It just reboots as windows like nothing ever happened, and the other boot options are not related to either wubi or ubuntu at all. 

As the sticky indicated, I have tried uninstalling and reinstalling wubi several times with the same results. 

I am very sorry if this is a common problem posted before, but I have spent the better part of the day googling and searching the forums and I am hopelessly lost. :(

Technical information (more on request):

Windows XP Media Center Edition
HP Pavillon a1520n
AMD Athlon 64 X2 Dual-Core
Processor 3800+
NVIDIA GeForce 6150 LE
250 GB

[CENTER] [SIZE=4][COLOR=Red]**===================== SOLUTION =====================**[/COLOR][/SIZE][COLOR=Red]
[/COLOR] [/CENTER]
 
For this particular problem, it was resolved by changing my boot.ini file's timeout value with a lot of help, from this:

```
[boot loader]
**timeout=0**
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /TUTag=U8OPLA /Kernel=TUKernel.exe
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=U8OPLA-BAK
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
 
```To this: 

```
[boot loader]
**timeout=10**
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center  Edition" /noexecute=optin /fastdetect /TUTag=U8OPLA /Kernel=TUKernel.exe
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center  Edition (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=U8OPLA-BAK
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons
 
```

---

### Post by oldfred on 2010-06-17
I do not know nor have every used wubi. But it sounds like your install did not add the entry to boot.ini.

It should have added a line like this:


[boot loader]
timeout=15
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOW S
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
[COLOR=Red]c:\wubildr.mbr="Ubuntu-Linux"[/COLOR]

You also need to confirm that in your c: directory is wubildr.mbr.

Boot.ini may be a hidden file in windows that you will have to unhide to edit. Do not edit with gedit from Ubuntu's liveCD as that will not use correct windows style line endings. 

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by LittleWolf on 2010-06-18
Thanks for replying!

Sadly, I have no idea of where I should check to confirm whether that line was added or not. 

Could you perhaps enlighten me?

---

### Post by oldfred on 2010-06-18
I have not been in my XP for a while and forgot a lot of how to edit things there since I now use Ubuntu most of the time.

You need to use explorer and drill down to c: and turn on show hidden files. ( I used to do that as the first command when installing windows as I want to know the files, windows does not want users to know and possibly damage system.) I would make a backup of boot.ini and edit boot.ini to add the line.

More info:
[http://support.microsoft.com/kb/289022](http://support.microsoft.com/kb/289022)

---

### Post by LittleWolf on 2010-06-18
Well, I checked C: to see if I could find anything, and I found some wubi and ubuntu related files. I took some screenshots for your viewing pleasure. 

[IMG]http://img580.imageshack.us/img580/3908/001lnf.jpg[/IMG]


[IMG]http://img691.imageshack.us/img691/2152/002fsd.jpg[/IMG]

[IMG]http://img692.imageshack.us/img692/7648/003nur.jpg[/IMG]


The red rectangles follow my path, however I found no boot.ini on the other folders either.

---

### Post by LittleWolf on 2010-06-18
Oh crap! I did not see the link you included on your post. I thought it was part of your signature..

I'll read it and the thread again then get back to you. Thank you for your patience. >.<

---

### Post by oldfred on 2010-06-18
I forget if it is favorites or tools but there is on eentry that is a long list that you have to check one or two items to show hidden files.

---

### Post by LittleWolf on 2010-06-18
Here's a screenshot of what my boot contains:

[IMG]http://img39.imageshack.us/img39/2866/004yd.jpg[/IMG]

---

### Post by oldfred on 2010-06-18
When you boot windows it should then show the wubi as a choice to allow you to boot into Ubuntu.

---

### Post by oldfred on 2010-06-18
From the liveCD run this to see your entire boot configuration:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and click on # in edit panel(code tags) to make it easier to read when you post the results.txt.

---

### Post by LittleWolf on 2010-06-18
This is a little over my head, but if I am following this correctly:

1) Put a LiveCD on my optical drive, with the Ubuntu version I want to install. 
2) Go into "Try Ubuntu mode"
3) Download Boot Info Script to desktop to find it easily
4) Open a terminal (Applications>Accessories>Terminal in Gnome).
5) Type **sudo bash ~/Desktop/boot_info_script*.sh **
6) Obtain the file RESULTS.txt from the desktop.
7) Post the contents of RESULTS.txt on here.

Is that how I should proceed?

---

### Post by jessicasimpson on 2010-06-18
I forget if it is favorites or tools but there is on eentry that is a  long list that you have to check one or two items to show hidden files.


[cheap wholesale T-shirts](http://www.baiyokefactory.com)

---

### Post by oldfred on 2010-06-18
Yes, on download & run script. It also helps us if you post it in code tags as that preseves formating and puts it in a scrollable box. The easy was to add tags is use cursor to highlight pasted text and click on # in edit panel above.

---

### Post by LittleWolf on 2010-06-18
I can't boot from the LiveCD. My monitor goes to sleep and does not display anything. I'm afraid my video card gets disabled in the process.

---

### Post by oldfred on 2010-06-18
Mine goes to sleep too. Lucid is lazy.

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

### Post by LittleWolf on 2010-06-22
Here are my results (Sorry for taking so long!):

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => HP/Gateway is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  HP Recovery
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM /wubildr.mbr /wubildr

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   469,933,379   469,933,317   7 HPFS/NTFS
/dev/sda2         469,949,445   488,392,064    18,442,620   c W95 FAT32 (LBA)


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8017 MB, 8017936384 bytes
202 heads, 59 sectors/track, 1313 cylinders, total 15660032 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1               8,192    15,660,031    15,651,840   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        C690F98790F97E6D                       ntfs       HP_PAVILION                   
/dev/sda2        4B6E-6BC0                              vfat       HP_RECOVERY                   
/dev/sda: PTTYPE="dos" 
/dev/sdb1        FC30-3DA9                              vfat                                     
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/FC30-3DA9         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=0 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect /TUTag=U8OPLA /Kernel=TUKernel.exe 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Windows XP Media Center Edition (TuneUp Backup)" /noexecute=optin /fastdetect /TUTag=U8OPLA-BAK 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=0 
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda1/Wubi

00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 
```

---

### Post by oldfred on 2010-06-22
Unless there is something unique about your HP/Gateway boot in the MBR, I do not see anything wrong. You seem to also have parts of wubi installed in the HP recovery partition sda2. I do not know wubi well enought to know if any of the other files are correct or not.

---

### Post by bcbc on 2010-06-22
It looks like the timeout in boot.ini is set to zero. Try setting it to 10 and see if that brings up the menu.

edit: it's a read only file, so right click on it first, properties, check off read only. Open with notepad and resave, then mark it readonly again. Since you have not actually completed the install, you may need to uninstall and reinstall (you'll know soon enough). In which case, you should double check the boot.ini file after installing, and before restarting.

---

### Post by LittleWolf on 2010-06-22
Thank you for replying! It has been really helpful so far. 

Should I edit the boot.ini from Microsoft OS, or from the LiveCD?

Also, do you refer to this part? 

```
[boot loader] 
**timeout=0 **
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

```

---

### Post by wilee-nilee on 2010-06-22
> **LittleWolf said:**
> Thank you for replying! It has been really helpful so far. 

Should I edit the boot.ini from Microsoft OS, or from the LiveCD?

Also, do you refer to this part? 

```
[boot loader] 
**timeout=0 **
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

```

> 
edit: it's a read only file, so right click on it first, properties, check off read only. **Open with notepad** and resave, then mark it readonly again. Since you have not actually completed the install, you may need to uninstall and reinstall (you'll know soon enough). In which case, you should double check the boot.ini file after installing, and before restarting.

Notepad is MS I would wait for confirmation from bcbc but I think you would edit a windows program from windows.

---

### Post by bcbc on 2010-06-22
> **LittleWolf said:**
> Thank you for replying! It has been really helpful so far. 

Should I edit the boot.ini from Microsoft OS, or from the LiveCD?

Also, do you refer to this part? 

```
[boot loader] 
**timeout=0 **
default=C:\CMDCONS\BOOTSECT.DAT 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect 
C:\CMDCONS\BOOTSECT.DAT="Microsoft Windows Recovery Console" /cmdcons 
C:\wubildr.mbr = "Ubuntu" 

```

From Microsoft Windows. Yes that's the line. This is what mine looks like:
```

C:\>type boot.ini
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional"
/fastdetect
C:\wubildr.mbr = "Ubuntu"

C:\>
```

EDIT: PS the boot.ini in your last post is from your recovery partition. When you do it from windows you'll see the correct one

---

### Post by LittleWolf on 2010-06-23
It worked!! Thank you so much!! I put the solution as an edit on the first post in case anybody has this problem in the future.

I ran into another problem with wubi, tho. =/ 

As soon  as I start out the ubuntu selection, my monitor goes to sleep and does not respond with anything except a forced reboot. I read in other threads that this is due to the graphic's proprietary drivers being unable to work. 

I'm trying to run wubi with my alternate copy of text-only Ubuntu, but it tries to download the 64 bit version automatically and won't accept the appropriate copy I put on it's directory (I even tried renaming it like the file it was trying to download in hopes I could fool it).

I'd appreciate it greatly if I could continue receiving your assistance. =(

---

### Post by oldfred on 2010-06-23
It depends on what graphics card you have, but the nomodeset works for many.

I had to do this:
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf


if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by LittleWolf on 2010-06-23
I think it has been installed successfully!!! :eek:

I am not entirely sure of what I did, but I pressed ESC before Ubuntu loaded, then it took me to different booting modes, then I pressed the letter "e" and it gave me some text I could edit. From there, I found quiet and splash, deleted them, and typed nomodeset exactly where they were. 

After that, it installed, and rebooted the machine again. It gave me some booting options again, which made my monitor shut off. So I did the same as above, I found quiet and splash, and replaced them again with nomodeset.

I'm not really sure, nor am I sure of what to do now, but I guess I'll learn as I go. I take it the first thing I need is to download the appropriate drivers for my video card. 

Thank you so much bcbc, for helping me with the boot manager, and thank you so much Oldfred, you've been helping me out from the beginning, and I appreciate it. I hope I was not too frustrating and that'll you'll continue to help me in the future when I'll probably blow this goddamned machine up. 

Please let me know if I am missing anything crucial on a first install!

---

