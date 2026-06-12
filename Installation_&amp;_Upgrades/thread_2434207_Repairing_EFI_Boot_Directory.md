---
title: "Repairing EFI Boot Directory"
date: 2020-01-01
forum: Installation &amp; Upgrades
---

### Post by Yogi2 on 2020-01-01
_MY CONFIGURATION_[INDENT]OS Name: Microsoft Windows 10 Pro        
 System Name: MSI    
 System Manufacturer: Micro-Star International Co., Ltd.    
 System Model    : GL72 7QF    
 System Type: x64-based PC    
 Processor: Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz, 2801 Mhz, 4 Core(s), 8 Logical Processor(s)    
 BIOS Version/Date: American Megatrends Inc. E1795IMS.311, 2/22/2018    
 SMBIOS Version: 3.0        
 BIOS Mode    UEFI    
 BaseBoard Manufacturer: Micro-Star International Co., Ltd.    
 BaseBoard Product: MS-1795    
 BaseBoard Version: REV:1.0    
 Secure Boot State: Off        
 Installed Physical Memory (RAM): 16.0 GB    
 Video Card: NVIDIA GM107M [GeForce GTX 960M] Optimus enabled
 Additional OS: Mageia7; Ubuntu 19.10
[/INDENT]
 

[HR][/HR]
 My laptop multi-boots into three OS's: **Windows 10, Mageia7, and Ubuntu 19.10**.  Recently I installed Linux Peppermint alongside the others, which turned out to be a huge mistake.  Peppermint identifies itself as Ubuntu in the EFI boot directory disregarding the fact that a true Ubuntu OS was already installed.  This conflict caused problems with the Windows Boot Device Manager so that it became necessary to uninstall Peppermint (deleted it's partition).   
 
 I used the **Boot Repair Disk** to restore Grub to a working state.  There were errors during the repair. The final report was very long and the following were the only entries that might relate to the current problem, but I can't be certain of that.  Given that secure boot is not enabled, these may be normal errors, or not.
```

 Adding custom /mnt/boot-sav/sda6/boot/efi/EFI/refind/drivers_x64/ext4_x64.efi
 Installing for x86_64-efi platform.
 grub-install: warning: Cannot set EFI variable Boot0001.
 grub-install: warning: vars_set_variable: write() failed: No space left on device.
 grub-install: warning: _efi_set_variable_mode: ops->set_variable() failed: No such file or directory.
 grub-install: error: failed to register the EFI boot entry: No such file or directory.
 grub-install --efi-directory=/boot/efi --target=x86_64-efi --no-uefi-secure-boot : exit code of grub-install :1
 
```
 *efibootmgr *reports the following boot order:
 ```
BootCurrent: 0004

 Timeout: 1 seconds

 BootOrder: 0000,0003,0002,0004

 Boot0000* Windows Boot Manager    HD(2,GPT,b524318a-9654-4983-9b59-d34dfbee61b0,0x40800,0x96000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...t................
 Boot0002* mageia7    HD(2,GPT,b524318a-9654-4983-9b59-d34dfbee61b0,0x40800,0x96000)/File(\EFI\MAGEIA\GRUBX64.EFI)
 Boot0003* rEFInd Boot Manager    HD(2,GPT,b524318a-9654-4983-9b59-d34dfbee61b0,0x40800,0x96000)/File(\EFI\REFIND\REFIND_X64.EFI)
 Boot0004* ubuntu    HD(2,GPT,b524318a-9654-4983-9b59-d34dfbee61b0,0x40800,0x96000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO

```
 The EFI boot directory is structured as such:
 ```
oot@GL72-7QF:/mnt/EFI# ls -l
 total 24
 drwxr-xr-x 4 root root 4096 Dec 31 17:09 Boot
 drwxr-xr-x 2 root root 4096 Nov 29 11:28 mageia
 drwxr-xr-x 4 root root 4096 Nov  1 10:58 Microsoft
 drwxr-xr-x 4 root root 4096 Nov  1 10:58 MSI
 drwxr-xr-x 4 root root 4096 Nov  1 10:58 refind
 drwxr-xr-x 3 root root 4096 Apr 16  2019 ubuntu
 
root@GL72-7QF:/mnt/EFI# ls -l ubuntu
 total 4264
 -rwxr-xr-x 1 root root     108 Dec 31 16:51 BOOTX64.CSV
 drwxr-xr-x 2 root root    4096 Apr 16  2019 fw
 -rwxr-xr-x 1 root root   75992 Apr 16  2019 fwupx64.efi
 -rwxr-xr-x 1 root root     126 Jan  1 10:47 grub.cfg
 -rwxr-xr-x 1 root root 1668984 Jan  1 10:47 grubx64.efi
 -rwxr-xr-x 1 root root 1269496 Dec 31 16:51 mmx64.efi
 -rwxr-xr-x 1 root root 1334816 Dec 31 16:51 shimx64.efi

```
 It appears that Ubuntu is booting from the **shimx64.efi (grub) binary** while Mageia is using it's grubx64.efi binary.  It was my understanding that the shimx64.efi file is used for secure boot only so that it does not make sense why Ubuntu isn't using it's own grubx64.efi binary.
 
 I can boot into Ubuntu via the Windows Boot Device Manager and most things are working well.  I tried to install a package from the repository called Grub Customizer and received the following error message:
> [B]Unable to install "Grub Customizer:
Error while installing package: Installed grub-efi-amd64-signed package post-installation returned error exit status 1[/B]
 This error seems to relate back to the error from the Boot Repair Disk operation.  I thought I had the boot problem resolved but apparently something is still amiss.  I am looking for advice on how to fix the efi booting so that I do not have errors when running Ubuntu 19.10.  Can anyone provide some guidance?

---

### Post by oldfred on 2020-01-01
While grub uses shimx64.efi for Secure Boot, it also seems to use it as default. Not sure now while there still is a grubx64.efi?

Windows, grub & rEFInd use /Boot/bootx64.efi as a hard drive or fallback boot entry and as copies of their .efi boot files.
So is rEFInd booting or is bootx64.efi reverted to one of the others. If you did a total reinstall of grub, it would have overwritten bootx64.efi with a new copy of shimx64.efi.

I have had that out of memory error. Not sure if UEFI or grub seeing space in efivars on hard drive.
I have multiple installs and had ESP on multiple drives with copies of /EFI/ubuntu. Some how my UEFI was finding all those copies and adding UEFI boot entries. Once I had to reinstall UEFI, houseclean all UEFI entries and unplug every drive. Only then rEFInd on a flash drive would boot & I then was able to get one drive to boot.

I do not use grub-customizer. It wants to write its own copies of most of grub. I prefer to manually edit settings or files in /etc/grub.d. And I do not normally edit any other file than 40_custom or /etc/default/grub.

Are all the files in /EFI/ubuntu from Ubuntu or are some from Peppermint?  Date may tell you otherwise only a full reinstall of grub will resolve that and that does not seem to be working.
Did you have any backups of /EFI/ubuntu. Most do not. I do, but that was where I got too many entries as my backups were copies in the ESP, and now just copy to a folder in /home so my regular backup includes those files.

---

### Post by Yogi2 on 2020-01-01
**oldfred **- Thank you for the reply.  That's quite a bit of information. 
[COLOR=#0000ff][I]
While grub uses shimx64.efi for Secure Boot, it also seems to use it as default. Not sure now while there still is a grubx64.efi?
[/I][/COLOR][INDENT]I've had various Linux installs on this system and each one had a single entry in it's EFI directory: **grubx64.efi**.   Ubuntu for some reason generates a few additional binaries.  
[/INDENT]
 

[COLOR=#0000ff][I]Windows, grub & rEFInd use /Boot/bootx64.efi as a hard drive or fallback boot entry and as copies of their .efi boot files.
So is rEFInd booting or is bootx64.efi reverted to one of the others. If you did a total reinstall of grub, it would have overwritten bootx64.efi with a new copy of shimx64.efi.[/I][/COLOR][INDENT]*rEFInd *is booting from **grubx64.efi** while the path shown in *efibootmrg *claims it's booting from **shimx64.efi**.  To be honest I don't know what the Windows Boot Device Manager is using.  I was expecting everybody to be on the same page, but it seems like they are not.
[/INDENT]
 
[COLOR=#0000ff][I]
I have had that out of memory error. Not sure if UEFI or grub seeing space in efivars on hard drive.[/I]
[/COLOR][INDENT]Is there a solution for this problem?[COLOR=#0000ff]
[/COLOR][/INDENT]
[COLOR=#0000ff] 

I have multiple installs and had ESP on multiple drives with copies of /EFI/ubuntu. Some how my UEFI was finding all those copies and adding UEFI boot entries. Once I had to reinstall UEFI, houseclean all UEFI entries and unplug every drive. Only then rEFInd on a flash drive would boot & I then was able to get one drive to boot.[/COLOR]
[I][COLOR=#0000ff]
I do not use grub-customizer. It wants to write its own copies of most of grub. I prefer to manually edit settings or files in /etc/grub.d. And I do not normally edit any other file than 40_custom or /etc/default/grub.[/COLOR][/I][INDENT]I get the same errors as are generated in the Boot Repair report when I try to install **gpart**.  It's not only a Grub Customizer issue.  My thinking here was that Grub Customizer might fix the problem.  I hesitate to edit config files because I don't know that much about what I'm doing at that level.  A package with a GUI is much preferred, but if I had the proper instructions I can copy and paste with no trouble. 
[/INDENT]
 
[COLOR=#0000ff][I]
Are all the files in /EFI/ubuntu from Ubuntu or are some from Peppermint?  Date may tell you otherwise only a full reinstall of grub will resolve that and that does not seem to be working.[/I][/COLOR][INDENT]I'm fairly confident that Boot Repair purged all traces of Peppermint and left me with what you see. What you see was installed by the Boot Repair disk and may not be Grub from Ubuntu or Peppermint.  The Grub boot options menu I now see has a lot more entries than what I've ever seen with Ubuntu's Grub.
[/INDENT]
 

[COLOR=#0000ff]*Did you have any backups of /EFI/ubuntu. Most do not. I do, but that was where I got too many entries as my backups were copies in the ESP, and now just copy to a folder in /home so my regular backup includes those files.*[/COLOR][INDENT]I have used *Hasleo's EasyUEFI* in my Windows environment.  It's pretty lame when it comes to handling anything Linux, but it does do ESP backups.  Unfortunately it never occurred to me to do a backup because I didn't expect Pepperment to search and destroy Ubuntu.  
[/INDENT]
 

Perhaps you can shed some light on my thinking.  I thought that I could simply rename the ubuntu directory to something else, e.g. **ubuntu-x**.  Then I would boot into ubuntu 19.10 and install Grub with the hope it would create a brand new EFI directory for itself - one that didn't have any errors.  My concern is what would happen down the line when Grub and/or Windows updated?  Would it revert back or crash or just go with what I modified?  Any thoughts on this approach would be appreciated.  And, if you think it's worth a try, can you also point me in the direction of some instructions for how to install Grub.  There are many articles out in the wild, but advice from an elder would be most valuable.

---

### Post by oldfred on 2020-01-01
I have regularly installed many versions of Ubuntu, but keep 18.04 as my main working install.
New UEFI installs always overwrote /EFI/ubuntu & added new UEFI boot entries, often duplicates. I learned I just had to edit /EFI/ubuntu/grub.cfg to have correct UUID for my 18.04 install.

I would not suggest renaming /EFI/ubuntu and keeping it inside the ESP. Back it up to another folder somewhere else. Its not large.
With /EFI/ubuntu folder missing it will not boot Ubuntu. You may be able to get rEFInd to boot as it bypasses the /EFI/ubuntu and goes to grub.cfg in your install. You can also use Supergrub on a flash drive to boot.

Is the UEFI the most current for your system?

Are the 6 folders and 4 UEFI boot entries all you have? When I had issues, I had many more.

My rEFInd does not have a grub.cfg nor use it. And it is only in /EFI/Boot (on my sdc drive).

```
fred@bionic-z97:/media/fred/ESP_C/EFI/BOOT$ ls -l
total 256
-rw-r--r-- 1 fred fred    134 Aug 30  2018 BOOT.CSV
-rw-r--r-- 1 fred fred 208776 Aug 30  2018 bootx64.efi
drwxr-xr-x 2 fred fred   4096 Aug 30  2018 drivers_x64
drwxr-xr-x 3 fred fred   8192 Aug 30  2018 icons
drwxr-xr-x 2 fred fred   4096 Aug 30  2018 keys
-rw-r--r-- 1 fred fred  31749 Sep 13  2018 refind.conf

```

---

### Post by Yogi2 on 2020-01-01
I liked the Ubuntu LTS version a lot but I wanted to see what the latest development path was like and abandoned it for 19.04 and then 19.10.  The thing I liked about the l9.x series is that it has a "safe video" install mode.  Sometimes my nVidia card gives Ubuntu a migraine.  

What I listed above is pretty much what is in the EFI/ubuntu directory.  However, while waiting for you to return I decided to re-install Ubuntu 19.10.  It refused to install Grub and the files that are in the current directory won't boot it either.  Now I can't boot into Ubuntu at all. 

I may take up drinking :confused:

---

### Post by oldfred on 2020-01-01
We have had a few cases where ESP gets corrupted. Then either chkdsk from Windows or fsck from Ubuntu may repair it. A few extreme cases required deletion & recreation of ESP. But then every UEFI entry has to be redone as they use GUID of ESP to know where to find boot files. Many or most UEFI find Windows but not other installs.

       [http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872](http://askubuntu.com/questions/862724/grub2-failed-to-install/865872#865872)
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted, change sda1 to your ESP.
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

I keep each LTS as main working install in a 25GB partition. And each new install in another 25GB / (root) partition but linked to same data partition. 
The newer versions now offer to install nVidia proprietary driver, so that does make it a bit easier.

---

