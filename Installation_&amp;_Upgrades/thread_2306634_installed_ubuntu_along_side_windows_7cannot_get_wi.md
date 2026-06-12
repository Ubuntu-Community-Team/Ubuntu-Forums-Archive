---
title: "installed ubuntu along side windows 7/cannot get windows 7 to boot"
date: 2015-12-17
forum: Installation &amp; Upgrades
---

### Post by cyryder7 on 2015-12-17
i installed ubuntu 7 alongside windows 7 but I cannot get windows 7 to boot normally. I realize this is probably an issue with the Grub2 bootloader and I followed the instructions in this post [https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

but that did not resolve the issue.

Here is what I did
1. I installed Ubuntu using the sliding partition GUI not the manual version (do I need to use the manual version to install Ubuntu alongside windows 7)
2) I typed sudo grub-install dev/sda in terminal but that did not resolve the issue
3) i typed sudo grub-install dev/sda1 (where windows 7 is located) but I get a warning about blocklists

Is there a way save my windows 7 partition? What is the recommended method of installing ubuntu alongside windows 7?

---

### Post by oldfred on 2015-12-17
You normally do not install grub to a partition.
And you never install grub to a Windows partition as the NTFS partition has essential boot code in the partition boot sector where you installed grub. But it does keep a backup, that you can usually restore it from with testdisk.
       PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see #12 for NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
Also check for /boot/grub in addition to /Boot 

That should fix Windows, but we need details on what issues are. 
      
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by cyryder7 on 2015-12-17
thank you for the reply, if i decided to do  complete reinstall of windows 7 and the ubuntu 14.04, how could i resolve the windows 7 not booting up issue?

---

### Post by oldfred on 2015-12-17
Without knowing what issue was, cannot tell.
If you run the report from Boot-Repair it may tell what issue was, otherwise just guessing.

---

### Post by cyryder7 on 2015-12-17
what is the normal typical process for installing ubuntu alongside windows7?

---

### Post by oldfred on 2015-12-17
First we need to know if UEFI or BIOS. Most Windows 7 systems are BIOS, but a few are UEFI.
Windows 7 systems usually use all 4 primary partitions. So you have to houseclean or backup one partition, so you can create an extended partition for logical partitions for Linux.
With Windows best to use Windows to shrink it own NTFS partition.
Fully backup Windows and all data.
Install Ubuntu into unallocated space. Default install is / & swap. Some also suggest separate partiitons for /home, data or shared NTFS data. But extra partitions require use of Something Else install option where you manually create your own partitions.

       [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

 [https://sites.google.com/site/easylinuxtipsproject/first](https://sites.google.com/site/easylinuxtipsproject/first)
Install with screen shots, auto install option
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
Windows 8 & Ubuntu
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

      
 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)

---

### Post by cyryder7 on 2015-12-19
thank you for your assistance. Here is a link to my boot info [http://paste.ubuntu.com/13108242/](http://paste.ubuntu.com/13108242/)

Here is what I did so far

1) Used the TeskDisk tool  [https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
2) Ran the boot repair live cd and did recommended repair

Neither approach resolved my Windows 7 boot issue. Would you be able to look at the boot info url and tell me what might be the recommended solutions?

after running boot repair, I now have two windows 7 loaders (sda1 and sda2) and I am using BIOS not UEFI

---

### Post by yancek on 2015-12-19
I'm not sure how you did this, but you have overwritten your windows 7 install.  Looking at the very top of the boot info summary you can see Ubuntu installed on sda1 and Debian on sda3.  There are no windows partitions shown and no entries for any windows in the grub.cfg file.  I'm not sure how you could be seeing two entries for windows as neither the grub.cfg on Ubuntu or Debian shows any?  Did you try to recover data with testdisk?

---

### Post by cyryder7 on 2015-12-19
in "TestDisk", i ran "Rebuild BS" not "Backup BS"

what would you recommend at this point?

---

### Post by yancek on 2015-12-19
You could try following the Step By Step instructions to drive to get data off the drive although I wouldn't have much hope.  Link below.  Otherwise, reinstall windows 7.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by oldfred on 2015-12-21
One of your Linux installs totally overwrote your Windows. There will be no way to restore a working Windows as if any file is overwritten it will not work.
But if you had data that do did not backup, then you may be able to recover some with Testdisk or Photorec. But you must immediately stop using system as every write by Ubuntu is over writing more of your data.

---

### Post by cyryder7 on 2015-12-21
thank you for the reply, how can i install windows 7 and then ubuntu 14.4 properly in order to avoid this issue? Would resizing the partition in Windows 7 when installing windows 7 resolve this issue? I believe I am using BIOS not UEFI

---

### Post by mrroberthadley on 2015-12-21
I will assume Ubuntu was installed on the same HDD but different partition? If this is the case then you should be able to recover.
Can you see the windows files while you are in the Ubuntu OS? If not then it is very likely you overwrote the windows partition.
If you can see the windows files then you can either repair the boot sector or just do what is called a "repair install" on the windows partition.
If you don't care about any of the data then start over and create new partitions. Install Ubuntu first and then Windows has been the easiest way I have found.

Let us know how it goes...

---

### Post by cyryder7 on 2015-12-21
yes same hdd but different partition, i can still see and access the windows files. 
i ran both test disk and and a boot-repair cd and neither solution worked  (i used the recommended repair option)
when you say "repair install" on the windows partition, do you mean with the windows 7 cd? how do you suggest I repair the boot sector?
> **mrroberthadley said:**
> I will assume Ubuntu was installed on the same HDD but different partition? If this is the case then you should be able to recover.
Can you see the windows files while you are in the Ubuntu OS? If not then it is very likely you overwrote the windows partition.
If you can see the windows files then you can either repair the boot sector or just do what is called a "repair install" on the windows partition.
If you don't care about any of the data then start over and create new partitions. Install Ubuntu first and then Windows has been the easiest way I have found.

Let us know how it goes...

---

### Post by mrroberthadley on 2015-12-21
Try this....
[http://www.howtogeek.com/howto/33433/restore-the-windows-boot-loader-after-an-ubuntu-update/](http://www.howtogeek.com/howto/33433/restore-the-windows-boot-loader-after-an-ubuntu-update/)

---

### Post by cyryder7 on 2015-12-21
thanks, would installing via wubi resolve the boot issues?

---

### Post by mrroberthadley on 2015-12-21
There is a way to get GRUB to work for both OS's. I have done it before but cant remember exactly how. I am not sure if Wubi would change your current scenario.
Have you tried what I linked you to? Did it work?

---

### Post by oldfred on 2015-12-21
Wubi is not supported anymore. 
       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

    
You totally overwrote Windows so tying to repair Windows or anything related will not work. You will need to reinstall. Windows in BIOS mode only boots from, installs to, or repairs a primary NTFS formatted partition with the boot flag.
The default install of Windows 7 or later uses two partitions, one a hidden 100MB boot and the main install. But you can install to one NTFS primary partition as an option if partitions are created in advance.

---

### Post by cyryder7 on 2015-12-24
So reinstall Windows 7, create two partitions while installing windows and then reinstall ubuntu?

> **oldfred said:**
> Wubi is not supported anymore. 
       Forums Staff recommendations on WUBI
[http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

    
You totally overwrote Windows so tying to repair Windows or anything related will not work. You will need to reinstall. Windows in BIOS mode only boots from, installs to, or repairs a primary NTFS formatted partition with the boot flag.
The default install of Windows 7 or later uses two partitions, one a hidden 100MB boot and the main install. But you can install to one NTFS primary partition as an option if partitions are created in advance.

---

### Post by Vladlenin5000 on 2015-12-24
> **cyryder7 said:**
> So reinstall Windows 7, create two partitions while installing windows and then reinstall ubuntu?

No, you're overcomplicating.
Just install Windows leaving unallocated space. The Ubuntu installer then will use that unallocated space and automatically create all the necessary partitions in there.
You can't create partitions for Linux from Windows anyway.

---

### Post by cyryder7 on 2015-12-26
thank you for the reply. when installing windows 7, i allotted some free space.

when installing from the ubuntu live cd, i have two options "Install ubuntu alongside Windows 7" and "Something else"

I chose "Something else" and I tried to install ubuntu to the unallocated space but I get an error message "No root file system is defined"

What do you recommend?

> **Vladlenin5000 said:**
> No, you're overcomplicating.
Just install Windows leaving unallocated space. The Ubuntu installer then will use that unallocated space and automatically create all the necessary partitions in there.
You can't create partitions for Linux from Windows anyway.

---

### Post by Vladlenin5000 on 2015-12-26
If you already have unallocated space then "install alongside..." is a safe option. The installer will use it to create the required partitions without user input. Without the unallocated space the installer would have to shrink one or more (Windows) partitions to make room and that may have consequences like Windows not booting afterwards. It usually works fine though as long as the Windows system partition is in an healthy state to start with (no logical errors, defragmented, etc.).

Choosing "something else" requires the user to manually create partitions for Ubuntu (in the unallocated space). Two are necessary: "/" (the root file system) and swap. Some suggest a separated "/home". It's up to you.

In your case it's safe to just let the installer do it for you.

---

### Post by cyryder7 on 2015-12-26
that's exactly what I did but i still cannot boot windows 7. 

I get the boot screen that lets you choose between windows 7 and ubuntu. loading ubuntu works fine but choosing windows 7 just gives me a purple screen.

just ran boot repair paste.ubuntu.com/14226454

To recap here is what I have done so far

1) installed windows 7
2) created unallocated space for ubuntu while installing windows 7
3) installed ubuntu via the live cd option (not wubi) and chose "Install ubuntu alongside windows 7"
4) ran boot repair

5) i get options to boot windows 7 but I just get a purple screen

> **Vladlenin5000 said:**
> If you already have unallocated space then "install alongside..." is a safe option. The installer will use it to create the required partitions without user input. Without the unallocated space the installer would have to shrink one or more (Windows) partitions to make room and that may have consequences like Windows not booting afterwards. It usually works fine though as long as the Windows system partition is in an healthy state to start with (no logical errors, defragmented, etc.).

Choosing "something else" requires the user to manually create partitions for Ubuntu (in the unallocated space). Two are necessary: "/" (the root file system) and swap. Some suggest a separated "/home". It's up to you.

In your case it's safe to just let the installer do it for you.

---

### Post by oldfred on 2015-12-26
Did Windows boot ok, before installing Ubuntu?
Does it need chkdsk or is it hibernated.

You may need to use Windows repairCD or flash or installer in repair mode and see if reinstalling Windows boot loader lets you boot/repair Windows. Then use Boot-Repair to reinstall grub to MBR and see if then you can boot Windows from grub. Grub really only boots working Windows.

---

### Post by cyryder7 on 2015-12-26
thank you for your help on this forum. windows 7 booted fine before installing Ubuntu, i could try running chkdsk though.

Did you see anything here that would indicate an issue? [http://paste.ubuntu.com/14226454/](http://paste.ubuntu.com/14226454/)

this is what I will try next. 
1) install windows 7, create unallocated space for Ubuntu
2)install ubuntu in the unallocated space via the live cd "Install alongside Windows 7 option" not manual partition
3) repair the windows 7 using the windows cd
4) run boot repair

what is the typical process for installing ubuntu alongside Windows 7? I am following this documentation to the letter [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

would Gparted or EasyBCD help resolve this issue? [https://help.ubuntu.com/community/GParted](https://help.ubuntu.com/community/GParted)
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)
> **oldfred said:**
> Did Windows boot ok, before installing Ubuntu?
Does it need chkdsk or is it hibernated.

You may need to use Windows repairCD or flash or installer in repair mode and see if reinstalling Windows boot loader lets you boot/repair Windows. Then use Boot-Repair to reinstall grub to MBR and see if then you can boot Windows from grub. Grub really only boots working Windows.

---

### Post by oldfred on 2015-12-27
You should not need to reinstall.
You may need to run Windows repairs from Windows repairCD or flash drive or if installer has the repair console.
Or install a Windows type boot loader with Boot-Repair and see if Windows boots or f8 gets you into Windows own repair console.
Then use Boot-Repair to restore grub2's boot loader.

       f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)

---

### Post by oldfred on 2015-12-27
User already has his own thread. And has done several total reinstalls.
Not quite sure why Windows does not boot from grub as installs do look normal.

[http://ubuntuforums.org/showthread.php?t=2306634](http://ubuntuforums.org/showthread.php?t=2306634)

---

### Post by cyryder7 on 2015-12-27
i already tried running Windows repairs from the Windows repair cd. that did not work.

I also tried running boot repair as well [http://paste.ubuntu.com/14226454/](http://paste.ubuntu.com/14226454/)

---

### Post by oldfred on 2015-12-27
Your installs look normal. And with dual booting they are separate and should boot independently. Only settings in BIOS or booting/boot loader may cause some issues.

If you either use Boot-Repair's advanced mode to temporarily install a Windows boot loader, or use Windows repairs to run fixMBR to install Windows boot loader, does Windows then boot? That is then back to Windows without any Ubuntu. If it works or needs repairs fix those.
Then use Boot-Repair to restore grub to MBR.

What brand/model system?

---

### Post by cyryder7 on 2015-12-27
progress! Here is what I did

1) installed windows 7 and allocated space for ubuntu
2) installed ubuntu using "Install alongside Windows 7" not manual partition
at this point, Ubuntu boots fine but windows 7 would only give a purple screen so 
3) I ran the Windows repair cd and went to command prompt (I did not use the automatic repair option at the top)
4) i typed bootrec /fixMBR, bootrec /fixBoot, bootrec rebuildBCD

Now Windows 7 will boot normally but I have lost access to GRUB/Ubuntu

Should I use Boot Repair (if so which settings, "Recommended Repair") or the Ubuntu Live CD to reinstall GRUB? this link suggests using the Live CD and typing grub-install [https://askubuntu.com/questions/229827/windows-7-and-ubuntu-boot-issue?rq=1](https://askubuntu.com/questions/229827/windows-7-and-ubuntu-boot-issue?rq=1)

---

### Post by oldfred on 2015-12-27
Make sure you have not left Windows hibernated.

Any of the choices should work.
I think all you should need is the default reinstall of grub to MBR.
If issues booting Ubuntu then you may need the advanced option of uninstall/reinstall of grub2.

---

### Post by cyryder7 on 2015-12-27
I have given up on the dual boot. I don't understand why the Boot Repair CD cannot resolve the issue. [http://paste.ubuntu.com/14238633/](http://paste.ubuntu.com/14238633/)

This is what I did
1. Ran boot repair cd w/ "Recommended repair". Afterwards, I can boot into Ubuntu but windows 7 no longer boots
2. Used the windows CD to repair via cmd prompt. Afterwards, I can boot into windows 7 but GRUB2 is gone

3. Ran the boot repair cd and used the Advanced options- "Purge Grub2". This took me through a lengthy sequence of terminal commands and I was able to reinstall the Grub2 bootloader.
4. Now I can boot into Ubuntu normally but booting into Windows 7 via GRUB2 still does not work. I get a purple screen. I can hear the windows login sound

I am using a custom built pc with BIOS. It is an older model and I do not think it even supports UEFI. I am using Windows 7 professional 
> **oldfred said:**
> Make sure you have not left Windows hibernated.

Any of the choices should work.
I think all you should need is the default reinstall of grub to MBR.
If issues booting Ubuntu then you may need the advanced option of uninstall/reinstall of grub2.

---

### Post by oldfred on 2015-12-27
Grub only boots working Windows, so something is not set correctly with Windows.
Is BIOS set for AHCI, not IDE?
Normally is it hibernation or chkdsk needed on the NTFS partition that causes issues.
Windows will boot with either of those, but grub cannot boot Windows with those issues. 
Boot-Repair does not fix most Windows issues, for that you have to use a Windows repair console.

I do not recommend as it requires you to install grub to a partition. That requires grub to use blocklists which grub does not recommend and make grub fragile. Or you may need Boot-Repair to fix grub more often.
       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
dual boot Windows 7 & Ubuntu 12.04 with EasyBCD
[http://ubuntuforums.org/showthread.php?t=2038652](http://ubuntuforums.org/showthread.php?t=2038652)

---

### Post by cyryder7 on 2015-12-27
My BIOS does not have an option for setting either AHCI or IDE. Where would I find that?

I ran chkdsk in Windows 7 and it showed no errors.

What is this hibernation issue that you are referring to? Anytime I run the windows repair cd or the boot repair cd, I turn off the computer and boot from the cd. In BIOS, my boot order is CD, hard disk, floppy drive.

> **oldfred said:**
> Grub only boots working Windows, so something is not set correctly with Windows.
Is BIOS set for AHCI, not IDE?
Normally is it hibernation or chkdsk needed on the NTFS partition that causes issues.
Windows will boot with either of those, but grub cannot boot Windows with those issues. 
Boot-Repair does not fix most Windows issues, for that you have to use a Windows repair console.

I do not recommend as it requires you to install grub to a partition. That requires grub to use blocklists which grub does not recommend and make grub fragile. Or you may need Boot-Repair to fix grub more often.
       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
dual boot Windows 7 & Ubuntu 12.04 with EasyBCD
[http://ubuntuforums.org/showthread.php?t=2038652](http://ubuntuforums.org/showthread.php?t=2038652)

---

### Post by oldfred on 2015-12-28
Windows 8 or later has always on hibernation which they call fast start up.
Windows 7 just has hibernation.

       More explanation of NTFS driver & Windows hibernation
[http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](http://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

 WARNING for Windows 8 Dual-Booters 
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast startup
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by cyryder7 on 2015-12-28
thank you for the reply and all your support in this process. I changed the hibernation settings and that did not work.  

However, I think may have come across some potential solutions. Based on the posts below, I think it is a video card driver error. I think resetting the resolution or changing it to a non-graphical boot may resolve the issue.  [URL="https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen"]

https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen[/URL]
 [http://ubuntuforums.org/showthread.php?t=2207319](http://ubuntuforums.org/showthread.php?t=2207319)  [URL="http://zaidmunir.blogspot.com/2014/04/purple-screen-on-windows-start-when.html"]
http://zaidmunir.blogspot.com/2014/04/purple-screen-on-windows-start-when.html[/URL] [URL="https://askubuntu.com/questions/120096/ubuntu-hangs-at-purple-screen#120168"]
https://askubuntu.com/questions/120096/ubuntu-hangs-at-purple-screen#120168[/URL]
 [https://askubuntu.com/questions/433388/windows-7-hangs-at-grubs-purple-screen-when-dual-booting](https://askubuntu.com/questions/433388/windows-7-hangs-at-grubs-purple-screen-when-dual-booting) 
 [https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2#Configuring_GRUB_2) 
 [https://wiki.ubuntu.com/X/NonGraphicalBoot](https://wiki.ubuntu.com/X/NonGraphicalBoot) [http://ubuntuforums.org/showthread.php?t=1296225](http://ubuntuforums.org/showthread.php?t=1296225) [URL="http://ubuntuforums.org/showthread.php?t=2117287"]
http://ubuntuforums.org/showthread.php?t=2117287[/URL]
 [http://ubuntuforums.org/showthread.php?t=2117287](http://ubuntuforums.org/showthread.php?t=2117287)

---

### Post by oldfred on 2015-12-28
I would not normally think a video driver issue would prevent booting Windows.
It often is an issue with Linux as vendors do not fully support video drivers for Linux and it takes a while before programmers can catch up to new designs. Proprietary drivers usually required for nVidia & AMD.

---

### Post by cyryder7 on 2015-12-28
finally, resolved the issue. I am using EasyBCD instead of Grub2. Would it be possible to add the EasyBCD tutorial to the official Windows/Ubuntu documentation? It may help save people a lot of time.

thank you for all the replies and help. please list this thread as solved

[URL="https://neosmart.net/wiki/easybcd/dual-boot/linux/ubuntu/"]https://neosmart.net/wiki/easybcd/dual-boot/linux/ubuntu/


[/URL]

---

