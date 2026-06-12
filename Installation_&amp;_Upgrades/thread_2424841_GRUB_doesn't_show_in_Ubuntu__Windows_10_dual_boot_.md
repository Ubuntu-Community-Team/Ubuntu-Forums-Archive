---
title: "GRUB doesn't show in Ubuntu / Windows 10 dual boot (tried most solutions)"
date: 2019-08-15
forum: Installation &amp; Upgrades
---

### Post by Atulo on 2019-08-15
[LEFT][COLOR=#000000][FONT=Times New Roman][COLOR=#222222][FONT=Verdana]Hello,[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][COLOR=#222222][FONT=Verdana]Was just hoping to ask some advice, as am having trouble getting GRUB to load.  Have installed Ubuntu alongside Windows 10 on an HP Envy x360.  Many solutions are listed on the web, and have already tried many.  The laptop is very new.[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#000000][FONT=Times New Roman][COLOR=#222222][FONT=Verdana]Have tried the following solutions...[/FONT][/COLOR][/FONT][/COLOR][/LEFT]

[LIST=1]
[*=1][COLOR=#222222][FONT=Verdana] Have entered this command into DOS as an admin: [/FONT][/COLOR][COLOR=#ffffff][FONT=Verdana]bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi[/FONT][/COLOR]
[*=1][COLOR=#222222][FONT=Verdana]Tried disabling fast boot[/FONT][/COLOR]
[*=1][COLOR=#222222][FONT=Verdana] Tried disabling secure boot[/FONT][/COLOR]
[*=1][COLOR=#222222][FONT=Verdana]Tried booting in legacy mode[/FONT][/COLOR]
[*=1][COLOR=#222222][FONT=Verdana] Tried booting in Windows' advanced startup (Ubuntu doesn't show as an option)[/FONT][/COLOR]
[*=1][COLOR=#222222][FONT=Verdana] In the BIOS boot settings, neither Ubuntu or Windows appear as options[/FONT][/COLOR]
[*=1][COLOR=#222222][FONT=Verdana] Installed Ubuntu choosing the 'something else' option.  Created a swap partition.  Installed Ubuntu on the free space.  Chose the partition with Windows boot loader to install the boot loader.  On the Ubuntu installation, noticed that the EFI partition say that it has the Windows boot loader.  On the Windows disk management utility, it seems that the boot loader is on the C drive ([/FONT][/COLOR][COLOR=#222222][FONT=Verdana]/dev/nvme0n1p3).  Wasn't sure if should have installed the boot loader in the Ubuntu.  Will plan to attach photos.

[ATTACH=CONFIG]283812[/ATTACH][ATTACH=CONFIG]283814[/ATTACH][ATTACH=CONFIG]283813[/ATTACH]Was hoping to see if anyone might have any thoughts?
[/FONT][/COLOR]
[/LIST]

---

### Post by oldfred on 2019-08-15
If Windows is UEFI, do not turn on Legacy/BIOS/CSM mode. Only use UEFI.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off. 
    
Have you updated UEFI and SSD firmware. Many with various models of HP say UEFI update solves many issues.

Have you seen these?
       HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[Guide] Install Ubuntu 18.04 on HP Spectre x360 13" 
[https://ubuntuforums.org/showthread.php?t=2414086](https://ubuntuforums.org/showthread.php?t=2414086)
[https://ubuntuforums.org/showthread.php?t=2422113](https://ubuntuforums.org/showthread.php?t=2422113)

---

### Post by yancek on 2019-08-16
I would suggest you read the Ubuntu documentation on dual booting with windows 10 at the link below which should clarify some things for you.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

As pointed out above, you have an EFI system so do not use Legacy/CSM.
I'm not sure what windows advanced startup is or why that would allow access to boot Ubuntu?
On my HP notebook, I can access boot options by hitting the Esc key then F9 on boot, or BIOS setup by hitting Esc and F10 keys.  Do you have the same or similar options?  Are you saying that you do not see either Ubuntu or windows as an option here?  Does anything boot?

Installing the boot loader to the windows partition from Ubuntu was  mistakes as the boot files should go on the EFI partition and the Ubuntu partition.  There should be separate directories in the EFI partition for windows and Ubuntu boot files and there will also be boot files for each on their respective partitions.

Reviewing the link above should clarify some of the questions but if you continue to have questions/problems, post back.

---

### Post by Atulo on 2019-08-16
Hi Olfred,

Kind of you to pass along this advice.  Checked the HP support assistant and it says that everything is up to date.  Think this laptop was just purchased last week or so.  Have secure boot off and am booting in UEFI, but still no GRUB.

---

### Post by Atulo on 2019-08-16
Hello Olfred and Yancek,

Kind of you to pass along these answers.  Had installed the boot loader in the EFI parition.  As it turned out, was pressing F10 to enter BIOS, when needed to press F9 to enter the boot order.  Kind of you to pass along that suggestion Yancek.  After that, changed the default boot order to put Ubuntu's boot manager first, using efi boot manager ([https://www.lifewire.com/fix-uefi-bootloader-issues-when-dual-booting-2200655](https://www.lifewire.com/fix-uefi-bootloader-issues-when-dual-booting-2200655)).  So, now everthing is working fine.  

Was great to get this advice.  Am planning to mark this thread as solved.

WIshing you all the best.

---

