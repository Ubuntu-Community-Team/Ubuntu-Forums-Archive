---
title: "Dual boot hell"
date: 2015-10-30
forum: Installation &amp; Upgrades
---

### Post by pietrod21 on 2015-10-30
That's the 1000000th asking for help about dual boot do I win something? Maybe another hdd?


Ok that's the situation I hope in you.


 I install windows 7 on my just built pc, then I download a lot of thing on it, then I'm ready to install ubuntu, and I discover that the option "install alongside windows" doesn't show up.

I need a way to install it manually without losing the possibility to boot windows, that happen often as I read here.


Little information:

```

[LIST=1]
[*][COLOR=#000000]ubuntu@ubuntu:~$ sudo fdisk -l[/COLOR]
[*][COLOR=#000000]Disk /dev/sda: 1000.2 GB, 1000204886016 bytes[/COLOR]
[*][COLOR=#000000]255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors[/COLOR]
[*][COLOR=#000000]Units = sectors of 1 * 512 = 512 bytes[/COLOR]
[*][COLOR=#000000]Sector size (logical/physical): 512 bytes / 4096 bytes[/COLOR]
[*][COLOR=#000000]I/O size (minimum/optimal): 4096 bytes / 4096 bytes[/COLOR]
[*][COLOR=#000000]Disk identifier: 0x59379df7[/COLOR]
[*][COLOR=#000000]   Device Boot      Start         End      Blocks   Id  System[/COLOR]
[*][COLOR=#000000]/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT[/COLOR]
[*][COLOR=#000000]/dev/sda2          206848  1134321663   567057408    7  HPFS/NTFS/exFAT[/COLOR]
[*][COLOR=#000000]Disk /dev/sdb: 7920 MB, 7920943104 bytes[/COLOR]
[*][COLOR=#000000]255 heads, 60 sectors/track, 1011 cylinders, total 15470592 sectors[/COLOR]
[*][COLOR=#000000]Units = sectors of 1 * 512 = 512 bytes[/COLOR]
[*][COLOR=#000000]Sector size (logical/physical): 512 bytes / 512 bytes[/COLOR]
[*][COLOR=#000000]I/O size (minimum/optimal): 512 bytes / 512 bytes[/COLOR]
[*][COLOR=#000000]Disk identifier: 0xb124ca27[/COLOR]
[*][COLOR=#000000]   Device Boot      Start         End      Blocks   Id  System[/COLOR]
[*][COLOR=#000000]/dev/sdb1   *        2048    15470591     7734272    c  W95 FAT32 (LBA)





[/COLOR]
[*][COLOR=#000000]ubuntu@ubuntu:~$ sudo parted /dev/sda print[/COLOR]
[*][COLOR=#000000]Model: ATA ST1000DM003-1ER1 (scsi)[/COLOR]
[*][COLOR=#000000]Disk /dev/sda: 1000GB[/COLOR]
[*][COLOR=#000000]Sector size (logical/physical): 512B/4096B[/COLOR]
[*][COLOR=#000000]Partition Table: msdos[/COLOR]
[*][COLOR=#000000]Number  Start   End    Size   Type     File system  Flags[/COLOR]
[*][COLOR=#000000] 1      1049kB  106MB  105MB  primary  ntfs         boot[/COLOR]
[*][COLOR=#000000] 2      106MB   581GB  581GB  primary  ntfs[/COLOR]
[/LIST]

```

So it seems from second command output I use a MBR partition system if I get what I read here:

[http://ubuntuforums.org/showthread.php?t=1836878&p=11207113#post11207113](http://ubuntuforums.org/showthread.php?t=1836878&p=11207113#post11207113)

I create as you can see here:


[http://i.imgur.com/J1ptvjg.png](http://i.imgur.com/J1ptvjg.png) (attached)



the partition for ubuntu from windows, I read this get you a lower probability of doesn't find windows after installation of ubuntu here: 

[http://ubuntuforums.org/showthread.php?t=2206632&p=12934644#post12934644](http://ubuntuforums.org/showthread.php?t=2206632&p=12934644#post12934644)


Anyway after crawling a lot of posts I still doesn't get the definitive algorithm to get an apparently simple thing as installing ubuntu on the same drive of windows...

Is there somebody that can explain to me the details and give me a solution? 

PS Is there some actual movement/initiative to stop microsoft to try to get the world even dumber with this new genius uefi effort?

---

### Post by oldfred on 2015-10-30
Please post screen shots as attachments, not in line. Not all users have high speed Internet.
You can easily attach with Forum's advanced editor and the paper clip icon.

You do not have UEFI. Although if new hardware, the hardware is UEFI. 
You installed Windows in BIOS mode on MBR partitioned drive, and unless you want to totally reinstall in UEFI mode on a gpt partitioned drive, you should just install Ubuntu in BIOS boot mode.

Windows only boots from MBR in BIOS mode.
Windows only boots in UEFI mode from gpt partitioned drives.

If you resized Windows, did you use Windows own partitioning tools? Best to use Windows disk management and immediately reboot into Windows so it can run chkdsk. Chkdsk is always reaquired after any NTFS partition size change. And chkdsk can only be run from Windows. You can use your installer, or create a Windows repair CD or flash drive. Also make sure Windows is not hibernated.

If you want to install Windows 7 in UEFI mode you have to copy to a flash drive and move some files around so UEFI can see /EFI/Boot/bootx64.efi to boot in UEFI mode. The bootx64.efi is then just a copy of Windows UEFI boot loader.
 
You must boot Ubuntu in BIOS/CSM/Legacy boot mode. Your UEFI should offer two boot options for Ubuntu installer, one UEFI:flashdrive and the other just the flash drive for BIOS boot.
You want the purple accessibility screen not the UEFI boot which shows a grub menu.

       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu)

    
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)

---

### Post by pietrod21 on 2015-10-30
From your answer seems I can proceed, but I'm still not sure, yes I use the Windows disk management tool, that's the output of chkdsk:

```

Ongoing control of the file system on C: The file system is NTFS.
Warning! F parameter not specified CHKDSK runs in read-only mode.
Verifying files (stage 1 of 3) ...
186624 file records processed. File verification completed.
300 record large files processed.
0 record invalid files processed.
2 EA records processed.
74 records reparse processed.
Checking indexes (stage 2 of 3) ...
238118 index entries processed.
Check indices completed.
0 unindexed files scanned.
0 unindexed files recovered.
Checking security descriptors (stage 3 of 3) ...
186624 security descriptors / SID of files processed.
Cleaning of 245 unused index entries from index $ SII of file 0x9.
Cleaning of 245 unused index entries from index $ SDH of file 0x9.
Cleaning the 245 unused security descriptors.
Checking security descriptors completed. 25748 data files processed.
CHKDSK is verifying Usn Journal ... 33654016 USN bytes processed.
Check the USN Journal completed.
The file system check carried out.
No problems found.
567057407 KB total disk space.
139682816 141151 KB in file.
87788 KB in 25749 indices.
0 KB in bad sectors.
303819 KB in use by the system.
65536 KB occupied by the log file.
426982984 KB available on disk.
4096 bytes in each allocation unit.
141764351 total allocation units on disk.
106745746 allocation units available on disk.

   

```

I do not want the uefi mode but just the standard BIOS/CSM/Legacy boot mode, so can I proceed with manually creating swap partition and ubuntu partition on the unallocated disk space as specified here: 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

?

I change the image to attachment. I don't think about internet speed when I post it...

I'm not going to try with there resources, basically I don't get how can the ubuntu install preserve the windows 7's "boot.ini" without even detect it, can somebody explain this to me? 

And give me a way to previously save and eventually restore this "boot.ini" file? (I'm not even sure @oldfred give me the ok to proceed this way)

---

### Post by oldfred on 2015-10-31
With Windows 7 there is no boot.ini. Equivalent is BCD.
       Windows BIOS Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8/10 (After Vista the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

    
       Pictures here worth 1000+ words - shows Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

    
Grub chain loads to Windows PBR as discussed above. It does not use boot flag to find Windows like Windows does, but looks for boot files normally in the bootable partition.

Best to have full backups:
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

And have a current version repairCD or flash drive for every system you install. With Ubuntu the live installer works for that, but if you upgrade, you still should create a new live installer.
      
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)

---

### Post by pietrod21 on 2015-10-31
Now I will try to follow the normal manual installation and chose as I see here [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html) in Linux and Lilo/Grub chapter to install the grub (or lilo?) on the linux boot record, in this way the MBR have automatically to add it to the choices at the start and I do not risk to damage windows boot and can always try to add the linux option at the start in a second moment (also if I still doesn't understand how and if it's possible.)

Can you just tell me (I have windows 7 on mbr partition and want to add ubuntu to the new partition created from windows with windows tool, and checked after as you request) if you think I can go on, or if there is something missing and I have to lose 10x more time later try to fixing an error, because to me this system really seems some diabolic entity create this complexity just to steal my time, for this reason I really thanks you for the help.

I'm going to create a swap partition and a parititon where to install ubuntu on the unallocated space, and if it asks me this to install grub on the linux partition, is this right?

---

### Post by oldfred on 2015-10-31
DO NOT create partitions with Windows. Only use Windows disk management tools to shrink the NTFS partition and reboot to let it run chkdsk.

You cannot create Linux partitions with Windows and it may convert to dynamic disks which is Windows proprietary and does not work with Linux. It also does not work with standard Windows tools either.

Info on Linux in the old link is old. But the BIOS boot is still the same for all BIOS based installs.
But Ubuntu and most Linux now use grub2 which has the package name grub-pc for BIOS installs. Do not install grub as that is grub legacy and  is not supported much if at all anymore.

Yours is relatively simple. Wait till you get a new UEFI system. :)

---

### Post by pietrod21 on 2015-10-31
C'mon I say "with windows" for saying "windows disk management" I told you I use that.
I'd like an answer. Like, I will do so and so like explained above with the above modification, because I use the "windows disk management", so is it good to go on or maybe there is a problem with oud5 or maybe before I have to fix the idjwoi888 and poikpdw5 etc etc?

---

### Post by efflandt on 2015-10-31
Your original gparted output shows 2 partitions for Win7, which I assume are msdos partitions, and unallocated space that you could use from Linux to create Linux partition(s). Windows Disk Management should "only" be used to create or resize Windows partitions, NOT Linux partitions. And if you ever resize Windows partitions (preferably from Windows), reboot to Windows before doing anything else, so Windows can do its chkdsk and make sure that everything is OK.

You can either use gparted from live/install iso to create Linux partitions, or you can do that when you select Other (or whatever manual partitioning is called) during install. But in either case you would select Other or Manual partitioning during install to select and format the partition for / and whatever else. With an msdos partition table you can have up to 4 primary or extended partitions, so with 2 existing Windows partitions you would need at least 1 extended partition if you wanted more than 2 Linux partitions. And there is a drop down list at the bottom of the manual partitioning section of install about where to put grub2.

In my case Windows had 3 partitions (including Recovery partition that it boots from), but I have 8 GB RAM and do not hibernate, so I just made 1 primary partition for Linux (sda4) with no swap, and put grub on /dev/sda4 instead of /dev/sda (mbr). I do that because some Win7 programs stored data in what they "thought" were unused parts of the mbr (which messed up grub2). I normally boot grub2 on sdb mbr (SSD) from a backup system that is still Ubuntu 12.04. If Win7 needs to boot from its own mbr for a special update, I just need to switch BIOS to boot sda instead of sdb. If sdb failed for any reason and I wanted to boot Linux from sda, I would use gparted (or fdisk) to unmark sda2 as boot and mark sda4 as boot, and I could boot grub on sda4.```
efflandt@XPS-8100-1404:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2fb1db22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2   *      112455    24788294    12337920    7  HPFS/NTFS/exFAT (RECOVERY)
/dev/sda3        24788295  1072880064   524045885    7  HPFS/NTFS/exFAT (Win7)
/dev/sda4      1072880065  1953524596   440322266   83  Linux (64-bit 14.04 & grub2)

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
32 heads, 32 sectors/track, 152638 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006a571

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        1024   156301311    78150144   83  Linux (64-bit 12.04 w/grub2 in sdb mbr)
```

---

### Post by yancek on 2015-10-31
When you get to the Installation Type option with Ubuntu, select Something Else which is the manual method.  Using this method, you will have control and you should see the windows partitions and the unallocated space on your drive.  Click on the unallocated space and then click the + sign below and to the left of the window and your get an Edit partition window.  Repeat the process for the swap partititon.

I'm not sure if I am understanding correctly, but you seem to want to boot with windows.  You will need to manually edit the boot files on windows to do that as windows is not capable by default of booting or chainloading Linux.  The link below explains how to use bcdedit.

[http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html](http://www.sevenforums.com/tutorials/2676-bcdedit-how-use.html)

I don't know if you've read any tutorials on dual-booting but the link below has detailed instructions on installing, including dual-booting and a lot of other useful information which could save you a lot of time in the future.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by pietrod21 on 2015-10-31
[COLOR=#000000] With an msdos partition table you can have up to 4 primary or extended partitions, so with 2 existing Windows partitions you would need at least 1 extended partition if you wanted more than 2 Linux partitions. And there is a drop down list at the bottom of the manual partitioning section of install about where to put grub2.


[/COLOR]I don't know what a primary or extended partition are. Thanks for giving me more detailed infos. But listen, the only thing I really get is that this situation is really messy and that science and technology aren't still able to allow dual bot with a reasonable margin of logic - they allow it but with too many shortcoming, exceptions, fix and tricks, and I lost any trust in a logical resolution here.

I question in another way: in absence of a public and detailed algorithm to install ubuntu on the same hdd of windows after it, is there anybody that given the output of any given command he asks for can tell me how to install ubuntu on this forum? (Not give me a lot of notions about something I found obnoxious, incredibly messy, horrendous, without interest and really bad engineered)


PS I want a swap partition and a ubuntu partition as mentioned before, that's 2 primary (or extended, pretended or offended) partitions, I have other 2 of windows one mistery 100 mb and another of C:, so 2+2=4 seems ok if I can't go with more than 4 partition on msdos, so this is good no? Also I will put the grub on the linux partition if no problems.


I really hope there is some more intelligent resolution than save my data and try every possible combination until it works, because this will take a lot of time, and for sure in that time I - but also a monkey - can create a more linear and logical system of booting. :lolflag:

---

### Post by pietrod21 on 2015-11-01
Yuppiiiiiiiiiiiiii

I install before a primary partition ext4 with mount point / then a swap partition also primary and now it complitely ignore windows!! That's wonderful my friends, I got in the same situation that I try to avoid here + I lose the time to avoid it!

Next time I will do by myself, I'm starting to realize that others in general can only steal your time. If it has to be like so I prefer to lose my time by myself.

---

### Post by oldfred on 2015-11-01
Did you use an auto install option that said overwrite entire drive?
Or Something Else as recommended.

If you boot into Ubuntu and in terminal run this, does it show Windows?
sudo update-grub

If not boot Ubuntu or live installer and add Boot-Repair.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by pietrod21 on 2015-11-01
[COLOR=#000000][FONT=arial]
[/FONT][/COLOR][COLOR=#000000]seems you got the solution also if in the meanwhile I do other thing, here what:

ALREADY DONE
[/COLOR][COLOR=#000000][FONT=arial]installed with two primary partition first mounted on / ext4 where I[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]install ubuntu and the second of 9gb for swap, it starts only ubutnu,
[/FONT][/COLOR]UPDATE 
[COLOR=#000000][FONT=arial]I use boot repair and I got these grub options:[/FONT][/COLOR]

[COLOR=#000000][FONT=arial]ubuntu--->start ubuntu[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]advanced option for ubuntu--->let me chose some details[/FONT][/COLOR]
[COLOR=#000000][FONT=arial]system setup--->can't find command "fwsetup"[/FONT][/COLOR]
FIX THE PROBLEM
go into ubuntu and execute "[COLOR=#000000]sudo update-grub[/COLOR]"

I also get 2 option to start it seems (the one for sure is the magic 100 mb windows one), it does change something if I start with one ore another? I suppose no, and if the answer is no the problem seems solved! ([http://imgur.com/ZPFIKf1](http://imgur.com/ZPFIKf1))

THANNNNNNNNNKS and excuse my anger.

---

### Post by oldfred on 2015-11-01
Boot-Repair copies Windows boot files from the 100MB Windows Boot partition into main install. That is because so many users delete the 100MB partition not knowing it is essential. It is not normally mounted in Windows, so not seen.

But then grub2's os-prober finds both sets of boot files and adds both sda1 & sda2 as boot options.

---

### Post by pietrod21 on 2015-11-01
Anyway thanks now it works from every of 2 partition it seems, so thanks, if you will had a bitcoin address I for sure tip a bit! :D

---

### Post by pietrod21 on 2015-12-03
[B]Re-entering the hell? Yes, outside it's too cold!
[/B]

Is this true 

But, surprisingly enough, the Windows 10 upgrade process won&#8217;t overwrite the GRUB2 boot loader on your Linux PC. Everything will continue working normally, and you&#8217;ll see the usual Linux boot loader every time your reboot your PC. After you perform the upgrade process, selecting the &#8220;Windows&#8221; option in the bootloader will boot into Windows 10 instead of your old Windows system.

[http://www.howtogeek.com/226295/how-to-upgrade-a-linux-dual-boot-system-to-windows-10/](http://www.howtogeek.com/226295/how-to-upgrade-a-linux-dual-boot-system-to-windows-10/)

Or upgrading to windows 10 is risky? (Like seems here [http://ubuntuforums.org/showthread.php?t=2280643](http://ubuntuforums.org/showthread.php?t=2280643))

---

