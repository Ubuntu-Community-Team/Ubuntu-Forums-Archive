---
title: "Messed up GRUB could not log to kubuntu, now is win boot is also messy"
date: 2019-04-20
forum: Installation &amp; Upgrades
---

### Post by leoszt on 2019-04-20
After installing kubuntu, I couldn't log into it, but windows kept working fine.

Then I managed to fix this by using boot repair disk's recommended method.

But I feel things are still kinda weird. Heres my paste.bin link:
[http://paste.ubuntu.com/p/VtjvSKdZRF/](http://paste.ubuntu.com/p/VtjvSKdZRF/)


Windows boot got a lot slower after fixing kubuntu, feels like grub redirects me back to mbr, and not directly to windows's bootloader. (I get lenovo's splash screen a second time, before getting to windows) (correct me if I'm wrong about this, please)

Is there a way to fix this? Going through the paste.bin data I saw that grub is present both in sda1 (which is mbr's partition right?) and on sda3, which's windows main partition (in addition to kubuntu's main partition, sda6). Is it the correct way things should be?

Sorry, for any dumb questions, I'm quite new to linux. Thank you for the answers!

---

### Post by yancek on 2019-04-20
You neglected to indicate which version of windows you are using.  The boot repair output shows that you have windows code for windows 7 in the MBR of that disk.  sda1 is an EFI partition which has the correct files for both windows and Ubuntu.  sda4 and sda5 show as windows 8 so which is it?  Also, on sda3, boot repair shows Grub files.  This is an ntfs (windows) filesystem partition and Grub should never be installed there.

The drive is GPT so you need UEFI for windows to work on it.  Go into the BIOS and make sure Legacy/CSM is disabled.  This might help but may not be the problem.  Were you able to make the change suggested at the end of boot repair?

> please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!

> I saw that grub is present both in sda1 (which is mbr's partition right?) and on sda3, which's windows main partition (in addition to kubuntu's main partition, sda6).

sda1 os not the MBR partition, nothing like that exists.  It is the EFI partition and Grub files should be there as well as on the Kubuntu partition (sda6) but never on a windows partition.

---

### Post by leoszt on 2019-04-20
> **yancek said:**
> You neglected to indicate which version of windows you are using.   

Ops sorry, it's windows 10.

Partition is like this:

sda1 - UEFI
sda2 - Windows reserved
sda3 - 100gb for windows 10
sda4 - 25gb of lenovo recovery stuff (didnt take it out due to warranty)
sda5 - 1gb winre
sda6 - 40gb kubuntu's root
sda7 - ~800gb /home

> **yancek said:**
>  The drive is GPT so you need UEFI for windows to work on it.  Go into the BIOS and make sure Legacy/CSM is disabled.  

I enabled legacy boot for it was easier to boot in USB drive this way, but boot repair advised me to disable it before  running the fix, and so I did. 
So legacy boot is already disabled

> **yancek said:**
>  Also, on sda3, boot repair shows Grub files.  This is an ntfs (windows) filesystem partition and Grub should never be installed there. 

So how do I take GRUB away from windows partition?

> **yancek said:**
>  Were you able to make the change suggested at the end of boot repair? 

Will have to check on how to get this done. will this disable grub in sda3?


> **yancek said:**
>  sda1 os not the MBR partition, nothing like that exists. It is the EFI partition and Grub files should be there as well as on the Kubuntu partition (sda6) but never on a windows partition.

Thanks for the info ;)

---

### Post by yancek on 2019-04-20
> So how do I take GRUB away from windows partition?

I'm not sure but you could simply try deleting the grub files there.  Problems with this is your standard windows boot files don't show on the windows system partition so I'm not sure if they are still there and not seen or if they have been overwritten.  You might wait until someone with specific knowledge/experience with this situation posts.

>  			 				please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file! 			 		

You would have to access your BIOS and look for boot priority settings which vary with manufacturer

---

### Post by leoszt on 2019-04-20
Sorry if I'm mistaken, but isn't UEFI a substitute for the BIOS?

By BIOS you mean the screen that fires up after smashing F2 or F12, Fsomething, during startup?

---

### Post by leoszt on 2019-04-20
[[img]http://i.imgur.com/oaRowBGl.jpg[/img]](https://imgur.com/oaRowBG)

here's my bios boot sequence, looks like it's right, right?

---

### Post by oldfred on 2019-04-21
I am surprised Windows boots at all. You cannot have grub in the partition boot sector (PBR or BS) of a NTFS partition.

       You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyze] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
Also check for /boot/grub in addition to /Boot 
Since ntfs partitions are case insensitive this leads to confusions between "/boot" and the already existing folder "/Boot" 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by yancek on 2019-04-21
> Sorry if I'm mistaken, but isn't UEFI a substitute for the BIOS?

No.  Look at the image you posted which contains EFI settings but many more settings unrelated to EFI.  Different systems use different keys but F2 is a common key to access BIOS Setup.

I'm not sure why/how windows boots given your situations.  Does the problem with windows occur when booting from the Lubuntu Grub?  What happens when you select the windows EFI entry show in your last post in the BIOS?

---

### Post by leoszt on 2019-04-23
> **yancek said:**
>  Does the problem with windows occur when booting from the Lubuntu Grub?  

You mean GRUB in sda1? that's where I've been booting from all this time. It's slow

> **yancek said:**
>  What happens when you select the windows EFI entry show in your last post in the BIOS?   

If I put Windows first in this list, it will boot to Windows exacyly the same way as if I do it from GRUB, slower than usual. Weird uh?

---

### Post by leoszt on 2019-04-23
> **oldfred said:**
> I am surprised Windows boots at all. You cannot have grub in the partition boot sector (PBR or BS) of a NTFS partition.

       You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyze] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
Also check for /boot/grub in addition to /Boot 
Since ntfs partitions are case insensitive this leads to confusions between "/boot" and the already existing folder "/Boot" 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

allright, goin to check on this tomorrow.
The source forge link is broken, tough.

---

### Post by leoszt on 2019-04-23
[[img]http://i.imgur.com/Frk8J0kl.jpg[/img]](https://imgur.com/Frk8J0k)

this is my grub list FYI

It boots windows using it's bootmanager right?

Care to say what are those other options? are they needed?

---

### Post by yancek on 2019-04-23
My earlier question about what happens when you select windows was in reference to selecting it in the BIOS and NOT from the Grub menu.  You clearly show this option is available in post 6 above.
I would test this to see if it changes anything with the boot.  I'm not sure why you have all those options in your EFI boot menu.  You should need only the first one but I would keep at least the first 2 options retaining the ability to directly boot Kubuntu and windows from the BIOS and keeping Setup is probably useful.

Your problems are a combination of having a mix of Legacy/UEFI installs with windows code in the MBR of the drive which is GPT and requires UEFI plus the Grub files on the windows OS partition which may be the reason for the slow boot, I don't know but those files definitely should not be there.  Disable Legacy in the BIOS

---

### Post by oldfred on 2019-04-23
Did you run Boot-Repair?
It sees  extra .efi boot files in ESP and adds boot entries to 25_custom.
You can edit or turn off execute bit on 25_custom to eliminate them.
The other entries are grub standard and you may at some point want them.

       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also. also can turn off execute on 25_custom  (the -x)if none wanted
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

---

### Post by leoszt on 2019-04-23
> **oldfred said:**
> 
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyze] and select [BackupBS]
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)

TestDisk returns a healthy boot sector for sda3, windows main partition.

---

### Post by leoszt on 2019-04-23
> **yancek said:**
> My earlier question about what happens when you select windows was in reference to selecting it in the BIOS and NOT from the Grub menu.  You clearly show this option is available in post 6 above.
Yup, that's what I meant. It boots exactly as if I chose it in GRUB menu.

> **yancek said:**
> I would test this to see if it changes anything with the boot.  I'm not sure why you have all those options in your EFI boot menu.  You should need only the first one but I would keep at least the first 2 options retaining the ability to directly boot Kubuntu and windows from the BIOS and keeping Setup is probably useful. 
Do you mean the options in my GRUB menu? (EFI boot has only 3 options which seem pretty standard to me)

> **yancek said:**
> Your problems are a combination of having a mix of Legacy/UEFI installs with windows code in the MBR of the drive which is GPT and requires UEFI plus the Grub files on the windows OS partition which may be the reason for the slow boot, I don't know but those files definitely should not be there.  Disable Legacy in the BIOS

Legacy is disabled, as in my post 6. Boot mode [UEFI] (I disabled fast boot just so I can make an easier access to BIOS )

---

### Post by oldfred on 2019-04-23
Please attach screen shots, not post in line.
Easy to attach with Forum's advanced editor and paperclip icon.

Grub in a PBR can be considered healthy if it correctly installed, its just that it can never be correct to be in a NTFS partition.
You need to restore from the backup.

Did you already run a fix or install grub twice, so sectors are identical? As it says you must have a valid NTFS boot sector, which has Windows boot info (if bootable), partition size and some other info.

---

### Post by leoszt on 2019-04-23
> **oldfred said:**
> Did you run Boot-Repair?
It sees  extra .efi boot files in ESP and adds boot entries to 25_custom.
You can edit or turn off execute bit on 25_custom to eliminate them.
The other entries are grub standard and you may at some point want them.

       # Edit 25_custom entries created by Boot-Repair:
sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
# turn off execute bit or it will run backup also. also can turn off execute on 25_custom  (the -x)if none wanted
sudo chmod a-x /etc/grub.d/bkp25_custom
sudo nano /etc/grub.d/25_custom
# Then do:
sudo update-grub

there's no such file:

```
$ sudo cp -a /etc/grub.d/25_custom /etc/grub.d/bkp25_custom
cp: cannot stat '/etc/grub.d/25_custom': No such file or directory
```

here's a ls of grub.d:

```
$ ls /etc/grub.d
00_header        30_os-prober_proxy  33_linux_xen        36_custom_proxy   41_custom  proxifiedScripts
05_debian_theme  31_linux_proxy      34_custom_proxy     37_uefi-firmware  backup     README
10_linux_proxy   32_custom_proxy     35_os-prober_proxy  40_custom         bin
```

---

### Post by leoszt on 2019-04-23
> **oldfred said:**
> Please attach screen shots, not post in line.
Easy to attach with Forum's advanced editor and paperclip icon. 
Sorry, some of them I uploaded directly from my celphone

> **oldfred said:**
> Grub in a PBR can be considered healthy if it correctly installed, its just that it can never be correct to be in a NTFS partition.
You need to restore from the backup. 

I've run TestDisk directly from kubuntu, does it make any difference? should I do it from live USB?

> **oldfred said:**
> Did you already run a fix or install grub twice, so sectors are identical? As it says you must have a valid NTFS boot sector, which has Windows boot info (if bootable), partition size and some other info.
Sorry, I dont get what you mean.

---

### Post by oldfred on 2019-04-24
You posted the testdisk screen that said BS and backup BS are identical. Post #14
It is that they cannot be grub.
This can never be correct.
```

       
 File system:       ntfs
Boot sector type:  Grub2 (v1.99-2.00)
Boot sector info:  Grub2 (v2.00) is installed in the boot sector of sda3  
     and looks at sector 209223912 of the same hard drive 
   for core.img. core.img is at this location and looks 
   for (,gpt6)/boot/grub. It also embeds following  
                        components: 

```
And if you have installed grub twice, it is more convoluted to fix as Windows will not repair it, you have to use testdisk to write a NTFS type BS, but newer Windows does not like it, and you have to run chkdsk from a Windows repair disk to repair it.

Because you ran grub_customizer, it replaced all you5 grub files with proxy files or its own versions. So 25_custom may be backed up, but is not now used. Not sure if Boot-Repair would recreate it, if it sees the customizer version of the files.

---

### Post by leoszt on 2019-04-24
So you're saying that the pastebin generated by boot-repair must be wrong? I've been wondering this also, since testdisk returns identical values for both the BS and BS backup.

still, windows booting is very slow. 

I've came across a method of formating EFI partition and reinstalling windows bootloader with command 'bcdboot' as in FIX #1 in this page:
[https://www.partitionwizard.com/clone-disk/bootrec-fixboot-access-is-denied.html](https://www.partitionwizard.com/clone-disk/bootrec-fixboot-access-is-denied.html)

It has further instructions (FIX #3) that mention using 'chkdsk' as you mentioned. 

Then I would just have to reinstall grub to EFI partition.

Since sda3 seems to be ok (BS and BS backup are identical) I figure the issue is a messed up EFI partition. 
(If you check my GRUB screen, windows boot option points to /dev/sda1)

what do you think?

---

### Post by oldfred on 2019-04-24
Do not know if Windows will fix the issue, but some third party tools do the same thing as testdisk.
That they are identical is not always correct. If you installed grub twice then both are corrupted and you need to go to next screen in testdisk and create new BS.
Do that first as I do not think ESP - efi system partition (your sda1) has issues.

---

### Post by leoszt on 2019-04-25
> **oldfred said:**
> you need to go to next screen in testdisk and create new BS. 

do you mean the "rebuild BS" option?

---

### Post by oldfred on 2019-04-25
Yes. But I think it still makes a XP type that will say ntldr and you have to run chkdsk from Windows to convert to Windows 7, 8 , or 10 type that will say bootldr.

You also can see the internal details and compare the BS with the backup BS. 
Use dump command.
If it says .NTFS at beginning it is then a NTFS type boot sector, but if mention of grub it is not.

---

### Post by leoszt on 2019-05-01
I'm in a hurry with some projects and have not been using windows for now.
Will try this ASAP and report back. 

thank you a lot for all the effort.

---

### Post by leoszt on 2019-05-24
> **oldfred said:**
> Yes. But I think it still makes a XP type that will say ntldr and you have to run chkdsk from Windows to convert to Windows 7, 8 , or 10 type that will say bootldr.

You also can see the internal details and compare the BS with the backup BS. 
Use dump command.
If it says .NTFS at beginning it is then a NTFS type boot sector, but if mention of grub it is not.

Hey, it's been a while, don't know if you remember my case.

Rebuild BS did not change anything, it just returns this:

```
filesystem size           195311616
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.

```


the dump of the boot sector and the boot sector backup are exactly the same, and both of  them weirdly shows signs of both NTFS boot loader and grub simultaneously:

```

=================== hexdump -n512 -C /dev/sda3
00000000  eb 63 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.c.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 08 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 37 a4 0b 00 00 00 00  |.........7......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  4e 06 24 20 06 24 20 c0  |........N.$ .$ .|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 80 e8 80 78 0c  |.....3........x.|
00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  f6 07 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |...t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..|f..f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f...D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d 5a 84 d2 0f  |...p.v....s.Z...|
000000f0  83 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  72 65 73 73 65 64 00 0d  |...<.u..ressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|
00000200

```

---

### Post by oldfred on 2019-05-24
It is the grub that is the issue. And that backup & primary are the same is also an issue.
Windows usually does not see a NTFS partition with grub installed to boot sector, so it will not repair it.
But if you use the testdisk command to create a new boot sector, then you can use Windows tools & chkdsk & fixBOOT commands to finally repair it. Not sure which order you need to run them.

Where it says grub, it needs to be ntldr for XP and all new NTFS, it should show bootmgr.

The part that now says grub may be the part that is not uses in the XP version. Not sure if that it says .NTFS at beginning should be enough then for Windows chkdsk to see it.

---

### Post by leoszt on 2019-05-26
Which testdisk command do you mean? I've tried 'Rebuild BS' and it gave this message:

```
filesystem size           195311616
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               2
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.
```

chkdsk was also tried, it took a while but did not fix the boot sector

---

### Post by oldfred on 2019-05-26
Did chkdks run?
If so then the RebuildBS must have worked as chkdsk will not run on a partition not seen as NTFS.
I might try chkdsk again and then fixBoot command from Windows. Some have to run chkdsk multiple times as it does not fix all errors on one pass.

BootRec.exe /FixBoot  #updates PBR partition boot sector or see bootsect.exe commands

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors - Use diskpart, then list volumes to see which drive to use 
bootsect.exe /nt52 c:  *compatible* with operating systems older (XP) than Windows Vista.
bootsect.exe /nt60 c:  *compatible* with Windows Vista, Windows Server 2008 or later

---

### Post by leoszt on 2019-05-27
well, we finally did it, grub was removed from sda3's BS:

[http://paste.ubuntu.com/p/rpwnDJk6Hh/](http://paste.ubuntu.com/p/rpwnDJk6Hh/)

```

=================== hexdump -n512 -C /dev/sda3
00000000  eb 63 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.c.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 a8 08 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  ff 37 a4 0b 00 00 00 00  |.........7......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  4e 06 24 20 06 24 20 c0  |........N.$ .$ .|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 cd 13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f cd 13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb cd 1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu$....r..|
000000f0  68 07 bb 16 68 52 11 16  68 09 00 66 53 66 53 66  |h...hR..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 cd 1a 33 c0 bf  |U...h..fa....3..|
00000110  0a 13 b9 f6 0c fc f3 aa  e9 fe 01 90 90 66 60 1e  |.............f`.|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 cd 13 66  59 5b 5a 66 59 66 59 1f  |.......fY[ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a1 f6 01 e8 09 00  |...u...fa.......|
00000170  a1 fa 01 e8 03 00 f4 eb  fd 8b f0 ac 3c 00 74 09  |............<.t.|
00000180  b4 0e bb 07 00 cd 10 eb  f2 c3 0d 0a 41 20 64 69  |............A di|
00000190  73 6b 20 72 65 61 64 20  65 72 72 6f 72 20 6f 63  |sk read error oc|
000001a0  63 75 72 72 65 64 00 0d  0a 42 4f 4f 54 4d 47 52  |curred...BOOTMGR|
000001b0  20 69 73 20 63 6f 6d 70  72 65 73 73 65 64 00 0d  | is compressed..|
000001c0  0a 50 72 65 73 73 20 43  74 72 6c 2b 41 6c 74 2b  |.Press Ctrl+Alt+|
000001d0  44 65 6c 20 74 6f 20 72  65 73 74 61 72 74 0d 0a  |Del to restart..|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 8a 01  a7 01 bf 01 00 00 55 aa  |..............U.|

```

bootin to windows didnt get any faster tough.
Maybe I will have to just stick to it, thank you a lot!

---

### Post by oldfred on 2019-05-28
Yes, it now shows bootmgr not grub in partition boot sector.

My XP used to boot in 5 minutes, but after a chkdsk it booted in only 3 minutes.

An SSD is the single biggest improvement you can do to a system. And SSD have dropped a lot in price.

---

### Post by leoszt on 2019-05-28
Yes, it now shows bootmgr not grub in partition boot sector.

> **oldfred said:**
> My XP used to boot in 5 minutes, but after a chkdsk it booted in only 3 minutes.
Well, maybe I'm a bit spoiled, I used to boot to windows 10 in like 15 our less (with a clear install), after dual booting it started to took like 40 ~50 seconds. but it's probably normal in dual booting systens.


> **oldfred said:**
> An SSD is the single biggest improvement you can do to a system. And SSD have dropped a lot in price.
boy, i know. I have a macbook with ssd it's fast as hell.

---

