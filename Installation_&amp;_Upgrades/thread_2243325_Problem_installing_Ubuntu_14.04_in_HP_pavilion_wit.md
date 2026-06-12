---
title: "Problem installing Ubuntu 14.04 in HP pavilion with win8."
date: 2014-09-08
forum: Installation &amp; Upgrades
---

### Post by prantik007 on 2014-09-08
So guys my laptop came with Windows 8 pre-installed. I want to dual boot it with Ubuntu 14.04. I have put in the live CD and tried to install 10 times!! and everytime the installer crashes in "install-grub2 failed,This is a fatal error". 
The partitions I made are 
ext2 boot/efi 500mb
ext4 / root 20gb
swap area 8gb
ext4 /home 20gb

here's my bug report: [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1366360](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1366360)

Here is what my laptop partition is by default. I just shrinked the local disk F to create free space.

[ATTACH=CONFIG]256246[/ATTACH]

Can anyone help me as why is this happening? Also I have tried boot-repair using the terminal commands. It fails too saying missing boot-repair file.
Will installing ubuntu like this mess my win 8 os?

---

### Post by prantik007 on 2014-09-08
131 views and no reply or help. People talk about Linux is the way. Now I see why it isn't.

---

### Post by coffeecat on 2014-09-08
Please be patient. The people who can help you may not have seen the thread yet. Only three forum members apart from yourself and myself have viewed the thread. The vast majority of the 131 views are from "guests" - people browsing the forum who are not logged in.

Your system is a UEFI one, so I shall not offer advice as my experience with uefi is minimal. However, a question: did you boot the live CD in UEFI mode? If you have not found it yet, you might find this community wiki page useful:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2014-09-08
An efi partition must be FAT32 for UEFI version of grub to install correctly.
An efi partition does have grub boot files, but is not the /boot folder or partition. And with most desktop installs you do not need /boot in a separate partition. Those with server type installs with RAID or LVM may need or want a /boot.

Do not create partitions with Windows, but use Windows to shrink the Windows NTFS partition. Your Windows screen shot does not show the Linux partitions.
If you have an efi partition for Windows grub will install into that same efi partition.

Be sure to fully backup Windows and create the recovery set of DVDs so you can reinstall Windows if desired.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by prantik007 on 2014-09-09
> **coffeecat said:**
> Please be patient. The people who can help you may not have seen the thread yet. Only three forum members apart from yourself and myself have viewed the thread. The vast majority of the 131 views are from "guests" - people browsing the forum who are not logged in.

Your system is a UEFI one, so I shall not offer advice as my experience with uefi is minimal. However, a question: did you boot the live CD in UEFI mode? If you have not found it yet, you might find this community wiki page useful:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

oh sorry! and yes i booted ubuntu in uefi mode. i checked it using the echo||uefi command. my windows 8 is also uefi if that helps. I have tried installing 14.04 and 14.04 LTS. both gives same problem :(

---

### Post by prantik007 on 2014-09-09
> **oldfred said:**
> An efi partition must be FAT32 for UEFI version of grub to install correctly.
An efi partition does have grub boot files, but is not the /boot folder or partition. And with most desktop installs you do not need /boot in a separate partition. Those with server type installs with RAID or LVM may need or want a /boot.

Do not create partitions with Windows, but use Windows to shrink the Windows NTFS partition. Your Windows screen shot does not show the Linux partitions.
If you have an efi partition for Windows grub will install into that same efi partition.

Be sure to fully backup Windows and create the recovery set of DVDs so you can reinstall Windows if desired.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
 
yes i shrank the volume to about 50gb from windows as uallocated space. I let ubuntu do the partition. yet same error :/

---

### Post by prantik007 on 2014-09-09
[SIZE=5]**here is my partition after installing ubuntu(But grub2 install failed) so i dont have bootloader.**[/SIZE]

[IMG]http://i.imgur.com/mqUKEcr.png[/IMG]


[SIZE=6]**Here is the error which i get **[/SIZE]

[IMG]http://i.imgur.com/RrhXP9a.png[/IMG]

---

### Post by fantab on 2014-09-09
That erros hints that you may not have booted the Ubuntu media in UEFI mode... see [here]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode") to know the difference.
If the system has ESP/Efi partition FAT32 partition then grub should install to that partition and not the the 'MBR' as the error suggests.

---

### Post by prantik007 on 2014-09-09
> **fantab said:**
> That erros hints that you may not have booted the Ubuntu media in UEFI mode... see [here]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode") to know the difference.
If the system has ESP/Efi partition FAT32 partition then grub should install to that partition and not the the 'MBR' as the error suggests.

Thanks or your reply. But I do get the black screen when booting ubuntu from usb. so your link says I'm in efi only D:

---

### Post by fantab on 2014-09-09
"Try Ubuntu" from Ubuntu media, open Terminal [ctrl+alt+T], run the following command and post the output of:
```
sudo parted -l
sudo fdisk -l
```

Just copy-paste the output here.

---

### Post by prantik007 on 2014-09-09
> **fantab said:**
> "Try Ubuntu" from Ubuntu media, open Terminal [ctrl+alt+T], run the following command and post the output of:
```
sudo parted -l
sudo fdisk -l
```

Just copy-paste the output here.

okay done!! 
[ATTACH=CONFIG]256289[/ATTACH]


[ATTACH=CONFIG]256290[/ATTACH]

However that WARNING in sudo parted -l didnt come earlier when i tried installing it 6 times! its just new this time. maybe because i have ubuntu installed without bootloader and grub2?

---

### Post by oldfred on 2014-09-09
I have not seen issue recently but some had locked efi partitions so grub (or even Windows) could not edit efi partition to add folder & files.
Solution was to just fully backup efi partition, delete partition and recreate it as FAT32, with boot flag in gparted as same size and restore from backup. 

Also every HP so far will not boot Ubuntu from UEFI menu. It has modified UEFI to only boot a Windows entry. Most rename bootx64.efi in /efi/Boot and copy grub or shim into that folder and name it bootx64.efi. Then boot hard drive.

       It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)


 Some find chkdsk on efi partition helps, others backup, reformat and restore as current work arounds.
Another possible work around. HP Pavalion G7
[http://ubuntuforums.org/showthread.php?t=2112273](http://ubuntuforums.org/showthread.php?t=2112273)

---

### Post by JMB74 on 2014-09-09
> **oldfred said:**
> Also every HP so far will not boot Ubuntu from UEFI menu. It has modified UEFI to only boot a Windows entry. Most rename bootx64.efi in /efi/Boot and copy grub or shim into that folder and name it bootx64.efi. Then boot hard drive.

       It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it

Is that definitely the case?

Was looking at a HP pavilion 17 and it's [manual]("http://h20566.www2.hp.com/portal/site/hpsc/template.BINARYPORTLET/public/kb/docDisplay/resource.process/?spf_p.tpst=kbDocDisplay_ws_BI&spf_p.rid_kbDocDisplay=docDisplayResURL&javax.portlet.begCacheTok=com.vignette.cachetoken&spf_p.rst_kbDocDisplay=wsrp-resourceState%3DdocId%253Demr_na-c04402649-1%257CdocLocale%253Den_US&javax.portlet.endCacheTok=com.vignette.cachetoken") has ubuntu sections.

So perhaps newer HP's are not so restrictive?

---

### Post by prantik007 on 2014-09-09
> **oldfred said:**
> I have not seen issue recently but some had locked efi partitions so grub (or even Windows) could not edit efi partition to add folder & files.
Solution was to just fully backup efi partition, delete partition and recreate it as FAT32, with boot flag in gparted as same size and restore from backup. 

Also every HP so far will not boot Ubuntu from UEFI menu. It has modified UEFI to only boot a Windows entry. Most rename bootx64.efi in /efi/Boot and copy grub or shim into that folder and name it bootx64.efi. Then boot hard drive.

       It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)


 Some find chkdsk on efi partition helps, others backup, reformat and restore as current work arounds.
Another possible work around. HP Pavalion G7
[http://ubuntuforums.org/showthread.php?t=2112273](http://ubuntuforums.org/showthread.php?t=2112273)

So i was looking at the last comment on [http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154) . That is exactly my case but I'm not sure how exactly he fixed it. Did he just boot-repair it with the terminal commands? If so then i tried some boot-repair commands too but it says some files couldn't be downloaded. Are there new commands for 14.04?

Also should I be worried about the warning shown here?
[ATTACH=CONFIG]256303[/ATTACH]

---

### Post by oldfred on 2014-09-09
@jmb74
That would be great if HP allowed dual booting. But many users have posted issues with hard coded UEFI that resets to make Windows first. Windows 8 used to only reset itself to first in boot order on maintenance, but now 8.1 seems to do it on every boot.

But some of the vendors do have Ubuntu only versions and then must have a different UEFI?

 Vendors violated UEFI specs - [http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf](http://hwe.ubuntu.com/docs/ubuntu-bios-uefi-requirements.pdf)
> Firmware should not enforce any boot policy other than the mechanism specified in Section 3 of the
UEFI 2.3.1 specification [UEFI 2.3.1]. Specifically, firmware should not modify boot behaviour de-
pending on the Description field of the EFI_LOAD_OPTION descriptor.

 @prantik007
If you have Windows in UEFI mode you must have gpt partitioning, not MBR(msdos). But gpt partitioned drives have a protective MBR with one partition entry showing gpt for entire drive, so old tools like fdisk will not think drive is unpartitioned and just let you repartition it incorrectly.

I might run gdisk or fixparts. Just loading and rewriting gpt partition table from either may fix MBR partition table also. But check that partitions are shown correctly before writing.


 [http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

OR:
      
 Use gdisk and verify partitions are correct with p, and use w to write the partition table. The v command can give more details on issues if necessary.  If not correct just use q to quit. The w -write should update primary, backup & protective MBR.

   sudo apt-get install gdisk
sudo gdisk /dev/sda
Command (? for help): 

    

 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by JMB74 on 2014-09-09
> **oldfred said:**
> @jmb74
That would be great if HP allowed dual booting. But many users have posted issues with hard coded UEFI that resets to make Windows first. 

Yes, I've seen those problems, but it's only those latest HP17/15 laptops that seem to reference ubuntu UEFI setups in their maintneance manuals, so perhaps they have seen the light after I imagine many complaints. Can't see how they could ref it in the manuals if they were still hard coded for Windows boot only.

Interestingly those laptops have been on sale since May and I can't find anyone reporting those old problems with those models, but a negaitive does not prove a positive, or I may have missed it, or not enough people have tried ubuntu on them yet.

Anyway.... don't want to high-jack this thread any more. So I'll leave that there.

Thanks :)

---

### Post by prantik007 on 2014-09-09
Hey. I just tried a boot repair with the 500mb boot repair live cd. It did its thing and uploaded a error log here [http://paste.ubuntu.com/8301529/](http://paste.ubuntu.com/8301529/) although grub menu isn't showing up yet


Also is there any other Linux distro which doesn't have this grub thing and boots well with Windows 8??I'm desperate for a linux :O

---

### Post by oldfred on 2014-09-09
You have to make sure fast boot is off so the always on hibernation is not on.

 The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

This says it cannot write into the FAT32 efi partition.

Reinstall the grub-efi linux of sda8
Installing for x86_64-efi platform.
grub-install: error: cannot open `/boot/efi/EFI/ubuntu/grubx64.efi': No such file or directory.

Can you create a /boot/efi/EFI/ubuntu folder manually from live installer, just to see if it is writeable?
From Live installer in may not mount as /boot/efi/EFI.
If not, then you need to do the backup (which you should do anyway) and erase & restore.

---

### Post by prantik007 on 2014-09-10
I guess I'll just give up. I fear I may mess up my Windows in doing so. :/ any other linux distro I could try without this bug/problem?

---

### Post by JMB74 on 2014-09-10
Do you need Windows?

- Hard drives are cheap, so on previous laptop I just swapped in a new hard drive and installed ubuntu on to the clean drive. No problem. If ever needed I have the old drive to pop back in.

- External drives are not expensive - Install and boot from one of those?

Neither may work for you, but thought I would suggest.

---

### Post by prantik007 on 2014-09-10
> **JMB74 said:**
> Do you need Windows?

- Hard drives are cheap, so on previous laptop I just swapped in a new hard drive and installed ubuntu on to the clean drive. No problem. If ever needed I have the old drive to pop back in.

- External drives are not expensive - Install and boot from one of those?

Neither may work for you, but thought I would suggest.

How about I delete Windows 8 with all the recovery,EFI partitions and install a Linux+Windows 7? Wil HP's firmware restrict that too? Btw I have a Windows 8 recovery disks so i can re-install it anytime.

---

### Post by oldfred on 2014-09-10
Even with the recovery disks it oftern is better to have a full backup of Windows and the efi partition. Then you do not have to reconfigure Windows.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

You can install Windows 7 if you have purchased a new Windows 7 license. Your Windows 8 license is embedded in the UEFI and only valid for your vendor version of Windows 8. Windows 7 will install in UEFI or BIOS mode but will not have the secure boot option. Many find the default install from a DVD only installs in BIOS mode and creates issues as it does not correctly convert from gpt partitioning to MBR. You then have to run fixparts to remove the rest of the gpt backup partition info. You can copy DVD installer to flash and update so Windows 7 will install in UEFI mode.

Many with HP just use the rename of bootx64.efi or use the one time boot key and have both Windows 8 and Ubuntu in UEFI mode. One or two with just Ubuntu had to recreate a /efi/Microsoft/Boot folder and copy grub efi files into that folder and rename it to bootmfgw.efi so system thinks it is booting Windows but really booting grub.

---

### Post by prantik007 on 2014-09-10
> **oldfred said:**
> Even with the recovery disks it oftern is better to have a full backup of Windows and the efi partition. Then you do not have to reconfigure Windows.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

You can install Windows 7 if you have purchased a new Windows 7 license. Your Windows 8 license is embedded in the UEFI and only valid for your vendor version of Windows 8. Windows 7 will install in UEFI or BIOS mode but will not have the secure boot option. Many find the default install from a DVD only installs in BIOS mode and creates issues as it does not correctly convert from gpt partitioning to MBR. You then have to run fixparts to remove the rest of the gpt backup partition info. You can copy DVD installer to flash and update so Windows 7 will install in UEFI mode.

Many with HP just use the rename of bootx64.efi or use the one time boot key and have both Windows 8 and Ubuntu in UEFI mode. One or two with just Ubuntu had to recreate a /efi/Microsoft/Boot folder and copy grub efi files into that folder and rename it to bootmfgw.efi so system thinks it is booting Windows but really booting grub.

Yes I installed windows 7 now. Disabled Secure boot and Enabled Legacy/BIOS boot. however while installing i found out that windows 7 doesn't install in gpt partition so while in windows 7 setup i pressed shift+f10 for command prompt. then deleted all my volumes in disk and then typed "convert mbr". then i installed windows 7 already :). now installing ubuntu should be seamless?

---

### Post by oldfred on 2014-09-10
The Windows 7 convert to MBR does not do it correctly. gpt partitioning has a backup gpt table at end of drive and Windows does not delete that. Then Linux tools see both MBR and backup gpt and get confused on which you really want and most assume you want to start over or erase entire drive. You need to remove backup gpt table.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Use Windows own disk tools to shrink the Windows NTFS partition to make space for Ubuntu. But do not create any partitions with Windows as it may try to convert to dynamic from basic partitions. That does not work with Linux.
Reboot immediately so it can run chkdsk and make repairs to its size change.

Then you should be able to install as long as you have available a free primary partition to use as the extended partition.

---

