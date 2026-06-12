---
title: "Dual Boot Ubuntu + Windows 8"
date: 2013-01-23
forum: Installation &amp; Upgrades
---

### Post by tk2013 on 2013-01-23
I have been having problems installing ubuntu 12.04.1 lts on a new UEFI enabled laptop.  I had problems at first trying to get a live CD working but I was able to get it to load.  

The issue is whenever I try to install ubuntu either from the live cd or grub menu, I am not given an option to install alongside windows.  I keep getting an error telling me that there is no installed OS.  I have windows 8 build 9200 working perfectly but it is not recognized by ubuntu.  
I have tried some fixes but without success. 

Fixes include: removing dmraid; using boot-repair; and doing a clean install of windows 8.  Any help would be appreciated.

---

### Post by arpanaut on 2013-01-23
This may help you out.  I think you would have better luck with 12.10
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2013-01-23
Is this an Ultra-Boot? That adds a level of complication. What system is it?

Also be sure to turn off fast boot in UEFI and secure boot to install.

The Intel SRT uses RAID somehow and that is why Ubuntu's desktop installer usually does not see the Windows install.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)

---

### Post by tk2013 on 2013-01-23
> **arpanaut said:**
> This may help you out.  I think you would have better luck with 12.10
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I have already tried to use that document before posting and i prefer 12.04.1 due to the stability.  I'm currently using a Toshiba Satellite S855-S5378 system.  I have both secure boot + fast boot in the BIOS and set them to disabled/normal boot respectively. Even after enabling them and disabling them there is no change.  

Although, I found out that the windows partition was unable to be accessed through the ubuntu live cd until i turned off the fast boot in windows 8 OS. Still no success.

Before seeking advice on the forum I tried to manually install ubuntu using the "something else" option.  I created a ext4 partition for ubuntu and the grub boot files in the UEFI partition already created by windows 8.  The install was successful but after restarting the windows loader kicks in.  I ran the live cd once more to run boot-repair and it fixed the grub bootloader.  On the screen I had 7 choices, 2 for ubuntu(os+recovery) memory test x2, and 3 windows loaders, each named differently.  I was never able to load windows from any of the loaders, even after a windows boot repair attempt.

I would still prefer to have the option to install ubuntu alongside windows 8, but if someone could help use the "something else" option that would be great too!

---

### Post by oldfred on 2013-01-23
In a couple of weeks there will be another point release of 12.04. That will include the grub2 2.00 that is in 12.10 and works with secure boot.

If secure boot is off, grub2 1.99 from 12.04 should work as its efi has worked with Windows 7 in UEFI mode.
You need fast boot off and secure boot off but UEFI on. 
Some confuse that with UEFI on meaning secure boot off or several toggle switches that prevent once setting or another depending. 
But you do not want Ubuntu in BIOS/legacy mode as then it cannot chain load into Windows. 

Some UEFI implementations only boot Windows. Boot-Repair will optionally rename the secure boot shim file from 12.10 to Windows efi file and then create a chain load to the backup of the Windows efi file. Boot repair then may not be able to auto rename with 12.04.

       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot
signed GRUB file shimx64.efi.

    
       To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC and please tell us what you observe.

    
Not your system but may give some clues.
       sony vaio laptop error: symbol not found: `grub_efi_secure_boot'.
[http://ubuntuforums.org/showthread.php?t=2102083](http://ubuntuforums.org/showthread.php?t=2102083)
So this time I installed 12.10, then I booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)

---

### Post by tk2013 on 2013-01-23
Thanks again oldFred for your replies.  I will try out your solution tomorrow, with the backing up and renaming of the EFI boot file.  

I will also include the generated boot-repair url with the results.  I will do a fresh install of ubuntu 12.04.1 (after installing win8 of course) and probably have to do the something else option.
Correct me if im wrong, but I do believe that I should choose the boot dir in the same partition as the window UEFI according to this documentation : [https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")

---

### Post by oldfred on 2013-01-24
Yes, but do not confuse the efi partition which is like the old MBR in BIOS but allows multiple boot loader in that partition with a separate /boot partition that has kernels and grub folder. 
With most desktops, a separate /boot partition is not required.

---

### Post by c.pfarher on 2013-02-01
Hello, I have the same laptop, but I will install ubuntu 12.10, and I have some questions...

My lapotp comes with windows 8 and UEFI pre-installed. First, I disabled secure boot, and put in normal the speed of boot following the instructions of [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

First of all I have an usb with ubuntu 12.10 for install.

My problem is in the section of guide:
Identifying if the computer boots the HDD in EFI mode: I know that the computer boot the usb in EFI mode, but i don´t know if the hdd run in EFI mode.  
1- Can I proceed with the instalation even if I don´t sure if my hdd run in efi or not?
2- I think that I don´t need to change de boot mode to legacy such as my windows8 was installed in UEFI  mode. That is correct?
3- About de process of instalation, I understand that I can use the same EFI boot partition of windows for linux? That´s correct?
I think is /dev/sda2 in the image attached: [http://ubuntuforums.org/attachment.php?attachmentid=230914&stc=1&d=1359757237](http://ubuntuforums.org/attachment.php?attachmentid=230914&stc=1&d=1359757237)

What represent the other partitions??(Are come with manufactured installation)

4- The last questions is about the instalation process: always when I install ubuntu, I select ¨something else¨ in partition process and I defined the / paritition, /home parition and swap partition. That is the same now? I am very confused because I read that I need to define a /boot partition or something?? 

Thank you for your help...

---

### Post by oldfred on 2013-02-01
You normally do not need a /boot. 

Your efi is the FAT32 with the boot flag which in gparted or parted is shown with boot flag, but actually it means something totally different in gpt partitions than in MBR(msdos) partitions.

You need to use Windows Disk Mangement to shrink Windows and reboot a couple of times to get it to run chkdsk and make other repairs do to the resize.

Make backups of efi partition and main Windows partition.
       The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

    
       Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

    
All the existing partitions are required by Windows, Windows repair and Vendor recovery. You will use the same efi partition for both Windows & grub/Ubuntu.

You still manually partition if you want to create a separate /home. I do suggest especially with Windows 8 that you also create a shared NTFS data partition for any data you may want in both systems and set Windows as ReadOnly.

You will need Boot-Repair to fix the grub issue on chain loading. You should install in UEFI mode, but Boot-Repair will convert a BIOS install to UEFI by unintalling grub-pc and installing grub-efi.

---

### Post by c.pfarher on 2013-02-07
First at all, thank you oldfred for the reply! 

I created the recovery disk with Toshiba Recovery Tool... I think this is the backup of the recovery partition (the last in the image). Am I right?

Also, I created with Macrium reflect a backup of the boot and msftres partition of the image that I uploaded in my last post..

Can I delete de recovery partition in the disk (label: Recovery) without affecting Windows OS and the boot of the machine? And then, shrink windows partition?

What represent the partition with flag msftres and the first partition with Label system in the image of my last post?.... :confused:

After all this steps, I proceed to install Linux Ubuntu 12.10 with the ¨Something else option¨ creating the / and /home partitions. Here I would like to know if I need to check the box for install grub or not?? 
And as a final step I will execute Boot-Repair with a live CD as you say in your last post....

ps. sorry for my english... 
Thank you...

---

### Post by oldfred on 2013-02-07
When you say you backed up boot, was that the efi partition?

The msr partition may not have anything in it. It is unformatted space where Windows virus checkers or DRM software may write serial numbers. Still probably a good idea to backup. 

I would not delete any partitions. Some systems need them and you currently do not need the extra space.

If installing in UEFI mode grub should auto install to the efi partition. I think it still shows choices. But if in BIOS mode you still install to sda.

---

### Post by c.pfarher on 2013-02-08
- yes... backed up boot is /sda2 in the attachment image of my post (fat32) and is the efi partition ...
- Now, I trying to do the backup with clonezilla, because I use Macrium reflect but that software has a 30 trial period......
- Then I will do the installation of ubuntu...!
Thank you...

---

### Post by c.pfarher on 2013-02-08
Oldfred you said me: ¨You will need Boot-Repair to fix the grub issue on chain loading. You should install in UEFI mode, but Boot-Repair will convert a BIOS install to UEFI by unintalling grub-pc and installing grub-efi.¨ ... 

What option in boot repair I need to execute for fix it?
Thank you

---

### Post by oldfred on 2013-02-08
I believe it is in advanced options, but it may depend on how you booted live installer to run it.

       How Boot-Repair works with UEFI systems - post 687 Dec 15, 2012
[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)
How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)

    
       grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

    
If you do not want the incorrect entries until grub fixes os-prober, you can just turn it off.
       Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by c.pfarher on 2013-02-17
Oldfred one more question.... I downloaded ubuntu secure remix 12.10 64 bits, because ubuntu doesn´t recognize my ethernet and wireless cards, and then I don´t have internet if I need to use boot-repair
When I boot an try to install, in type of instalation, ubuntu don´t detect an operating system (although it was installed windows8), this is normal?,,, I don´t know if I proceed with the instalation or not? I have 4 options:
1- Erase disk an install ubuntu
2- Encrypt the new Ubuntu installation for security
3- Use LVM with the new Ubuntu Installation
4- Something else 

I think I need to select the 4 and create / and /home .. but I think it is properly to confir that is a normal situation that it doesn´t detect windows 8...
Thank You

---

### Post by oldfred on 2013-02-17
Ubuntu almost always works with Ethernet. But often not with wireless as there are so many drivers they all are not on installer. You then should be able to download. 
I so not know details, but there are one or two Ethernet chips that have to have downloads to work. 
What Ethernet chip/card do you have?

Is this system an Intel SRT with small SSD? That uses RAID  that is not on desktop install. Other issues can be that Windows needs chkdsk, it still hibernated (Which Windows 8 does by default for fast boot) or you created partitions with Windows and converted to dynamic partitions.

---

### Post by c.pfarher on 2013-02-17
It is a Toshiba S855-S5378 (It hasn´t SRT system).

This are the hardware: 
* Ethernet Controller: Atheros AR8161 Gigabit ethernet (rev10), and * Realtek Semiconductor co. Ltd. Device 8723 (wireless). 
 opened a thread last weak: [http://ubuntuforums.org/showthread.php?t=2115725](http://ubuntuforums.org/showthread.php?t=2115725)

I follow this step after boot with ubuntu live cd:
1- I configured windows 8 for normal boot (as same in the bios),  and I desactivated Secure Boot.
2- I used windows for shrink the System drive in order to do space for Ubuntu.
3- In the Bios I have an option to change UEFI boot to Legacy mode, but I understand that UEFI is the correct in my case. Then, I don´t change to Legacy. Right?

---

### Post by oldfred on 2013-02-17
You want to install in UEFI if at all possible but some systems will not let you. Also some Toshibas have issues.

       Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)

           Some Toshiba's will not boot.
 they managed to leave the signing key out of the database that's used to validate binaries

But some are able to install in Toshiba
       [SOLVED] Can't install Windows 8 & Ubuntu in Toshiba Portege Z930 with explanation how by OP feb 2013
[http://ubuntuforums.org/showthread.php?t=2114290](http://ubuntuforums.org/showthread.php?t=2114290)

---

### Post by c.pfarher on 2013-02-17
I don´t have problem to boot the live cd in uefi mode with live cd of ubuntu remix 12.10 or ubuntu 12.10... But It isn´t detect windows... I don´t know If is safe to following with the installation ;|

Are there a way to put the ethernet card to work in live cd?? or maybe a Ubuntu CD with backports drivers?

Thank You.

---

### Post by oldfred on 2013-02-17
I think you need to resolve Ethernet issue as you need that to install easily and especially with UEFI to make fixes and updates.

Either search forum based on your chip or start a thread on that issue posting what chip you have. 

       Using Google is often better than the forums search function.
Just append site:ubuntuforums.org to your search term
[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

    
Someone posted this:
lspci > ~/abs-network.txt
lsusb >> ~/abs-network.txt
ifconfig >> ~/abs-network.txt
iwconfig >> ~/abs-network.txt
Now post this in a new thread,  and attach (via the paperclip) the abs-network.txt file which will be in your home folder.

But all my Ethernet has just worked so I have not followed the specific issues.

---

### Post by c.pfarher on 2013-02-17
Thank you, I post in [http://ubuntuforums.org/showpost.php?p=12515769&postcount=4](http://ubuntuforums.org/showpost.php?p=12515769&postcount=4) the output of that Commands...

---

### Post by oldfred on 2013-02-17
First search result:
[http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)

Also some suggestions:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/927782](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/927782)

---

### Post by c.pfarher on 2013-02-18
Yeah, I read it, but the problem is that I can´t install it in LIVE CD, That steps works when you install it in your hard drive... :(

---

### Post by oldfred on 2013-02-18
I have seen some do it with BIOS installs, but it really is a Catch-22.

It may then be best to just do an install without Internet and see if your system will boot. Many UEFI systems still seem to need fixes, but you can manually do them. with some effort. A few have just worked.
 Boot-Repair will do some of the fixes, but some do require downloading packages. You again can down load package manually and copy into Ubuntu to then install package.

You can still run BootInfo report but it will complain that you cannot upload to pastebin. But it has copy on system that you can attach to a post. I can be large, so probably best just to attach with paperclip icon in edit panel above new message.

---

### Post by c.pfarher on 2013-02-18
> **tk2013 said:**
> Thanks again oldFred for your replies.  I will try out your solution tomorrow, with the backing up and renaming of the EFI boot file.  

I will also include the generated boot-repair url with the results.  I will do a fresh install of ubuntu 12.04.1 (after installing win8 of course) and probably have to do the something else option.
Correct me if im wrong, but I do believe that I should choose the boot dir in the same partition as the window UEFI according to this documentation : [https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")

Do you have success in the instalation? I have the same laptop and I will go to install ubuntu 12.10... Can you boot ubuntu?
Thank You.

---

### Post by c.pfarher on 2013-02-20
Oldfred, what about install linux without dual boot (delete windows 8 system)? Can I set in the bios for boot in legacy mode, an the install it in the common way. I am right? I that case can I delete the Efi partition?
Thank You

---

### Post by oldfred on 2013-02-21
If you have UEFI in legacy/CSM mode you should be able to erase drive and install in BIOS mode. 

I hesitate to suggest that as some systems have to have Windows as UEFI and Windows seem to be integrated.

I did see one user who did what you want. For him it worked. 
Another user always buys a lwer cost laptop that offers a faster SSD option. Then he just removes hard drive an d puts it on shelf,  and puts his own SSD in with Ubuntu. If he eve wants to sell system or send in for repair he just puts Windows back in. A way to have a full backup.

I use Ubuntu with BIOS and gpt partitions, so you do not have to change from gpt to MBR partitioning. In BIOS mode with gpt partitioning you need a tiny bios_grub partition of 1MBR that has no format.

       However, in the GPT setup, there is no space following the 512-byte MBR for embedding the "second stage" core.img.
    
       In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.

   You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02.

---

### Post by c.pfarher on 2013-02-27
Finally I installed ubuntu 12.10 remix...but I have some problems:
1-  When I reboot, it doesn´t show grub and the system boot directly to ubuntu.... although i don´t delete the windows partition... (ubuntu boots ok and show me de desktop correctly)

2- As you know, I ubuntu live don´t recognize the ethernet or wireless card, then I use a script for download de .deb files in other computer and then installed for recognized the ethernet card with success... for this, I install linux-backports-modules-cw-.. When the instalation finished I reboot the pc and now I have internet, but ubuntu boots in console mode (no graphics mode ;( )... 
I execute startx command, but It show me an error. (I attached here de Xorg log)
Thank You!

---

### Post by oldfred on 2013-02-27
I guess this is the problem.

> display NO RECLAMADO
             descripción: VGA compatible controller
             producto: 3rd Gen Core processor Graphics Controller
             fabricante: Intel Corporation
    

But i thought Intel just worked. There is only one driver and it is the open source one included.

But some have posted these work arounds, but I only have nVidia.

       Some other settings, test with e on grub menu in place of splash quiet:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)


[LIST]
[*]Older Intel video card: i915.modeset=1 or i915.modeset=0
[*]newer:  [COLOR=Red]i915.i915_enable_rc6=1[/COLOR]
[*]nVidia: nomodeset
[*]Generic: xforcevesa or nouveau.modeset=0
[*]Radeon: radeon.modeset=0
[/LIST]
     
       Limited resolutions with Intel Sandybridge graphics
[http://ubuntuforums.org/showthread.php?t=2057807](http://ubuntuforums.org/showthread.php?t=2057807)

    
Some have said this works, but you have to use you monitor's size.
       Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

    
And some have posted this:
       For Intel graphics running slow:
sudo apt-get install mesa-utils
glxinfo | grep OpenGL | head -n3

---

### Post by c.pfarher on 2013-02-28
Thank you oldfred, It´s really wierd,,, I attached here the lshw and Xorg log when I boot with the live cd and graphic mode was be ok.... Is there any manner to apply this configuration to the installed system?

I note that in my system when I write sudo halt for shutdown,, the system don´t shut down, it stop in 
* Will now halt
 [488.821849] System halted. 

For finally shut down the system, I need to do it manually with keep press the power button of the notebook

---

### Post by oldfred on 2013-02-28
It seems to have a lot of trouble finding your video. 24 to 879 seems like a very long time for EDID to be found. But I do not really know video issues.

> [    24.580] (II) XKB: generating xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[   879.395] (II) intel(0): EDID vendor "AUO", prod id 8428
[   879.395] (II) intel(0): Printing DDC gathered Modelines:
[   879.395] (II) intel(0): Modeline "1366x768"x0.0   76.50  1366 1382 1398 1580  768 771 785 806 -hsync -vsync (48.4 kHz eP)

You should try to never use the power switch to shut down. Always remember the elephants.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by c.pfarher on 2013-02-28
is there any solution for my case? thank you....

---

### Post by oldfred on 2013-02-28
I do not know video issues. You might want to start a new thread with your video issue in the title and post what you know as above.

---

### Post by siepo on 2013-03-01
As to shutdown: on my HP ProBook, pressing the power switch initiates a normal shutdown instead of a power off. At least, if I am at a text console.

Again on a text console, 'sudo halt' does everything except power off, and sudo shutdown -h now' does everything including power off.

Oldfred, what is so bad about power off if all filesystems are already unmounted?

---

### Post by oldfred on 2013-03-01
If file systems are all unmounted you should be ok. 

Best to remember the elephants.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[URL="http://kember.net/articles/reisub-the-gentle-linux-restart/"]http://kember.net/articles/reisub-the-gentle-linux-restart/

[/URL] R gives back control of the keyboard, S issues a sync, E sends all processes but init the term signal, I sends all processes but init the kill signal, U mounts all filesystem ro to prevent a fsck at reboot, B reboots the system

[URL="http://kember.net/articles/reisub-the-gentle-linux-restart/"]
[/URL]

---

### Post by windows8news1 on 2013-03-05
[IMG]http://www.windows8post.com/[/IMG]windos8 is the latest version of Microsoft. It is latest computer o parting system. I give thanks to poster this post and I strongly believe that you can get more and more exciting and important information from the bellow website. I believe you will be surprise after see the bellow website.
www.windows8post.com

---

### Post by c.pfarher on 2013-03-07
After some upgrades and execute X -configure and copy the xorg file generated to /etc/X11/xorg.conf, now the graphic mode It´s working! :)
Now, I have only one problem, when computer start, it doesn´t show me the grub, it boots directly to ubuntu. As you know in the previous posts I commented that I don´t delete windows partitions....I would like to have the grub with the options to boot to win or ubuntu....
I executed boot-repair, and it showed me a info windows said: Efi detected. After that, I have the advance or recommended options .... I don´t know what option I need to select... there are a lot of checkboxes ...
Here is the info recollected with boot repair: [http://paste.ubuntu.com/5594548/](http://paste.ubuntu.com/5594548/)
Thank You!

---

### Post by oldfred on 2013-03-07
Boot-Repair has not yet added the Windows boot files to 25_custom. I would first run the recommended repair and see it that adds correct Windows entries. Otherwise you can manually add entries as posted as workarounds in this bug report.

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by ubfan1 on 2013-04-11
I have some limited experience with the Toshiba Satellite S855-5378,  using it for secure booting Windows and Ubuntu.  First thing is to  ensure you have the latested firmware for your machine (6.60) to fix the  key/database issue to allow Ubuntu to secure boot.  I too could not get  both Windows and Ubuntu booting off the same EFI files, but putting a  second EFI partition on a USB to boot Ubuntu (running off the hard  disk), and keeping the original EFI files on the hard disk for Windows  worked for me.  I did not have any video issues.  
  Your present  situation looks like your are booting Ubuntu, but not "securely", so  just copying the present files to a GPT partitioned USB with a 250M EFI  bootable partition will not work when secure boot is enabled.   Maybe  boot-repair would set things up correctly, but it's not hard to do  manually, just confusing since the signed and unsigned .efi files all  have the same names when in the EFI directories.  On the Ubuntu  filessystem, you should have the signed versions of the following:  /usr/lib/shm/shim.efi.signed,  /usr/lic/grub/x86_64-efi-signed/grubx64.efi.signed, and
  /usr/lib/grub/x86_64-efi-signed/gcdx64.efi.signed.  Copy them all onto  the USB stick .../EFI/ubuntu directory without the ".signed" extension.   Then copy and rename the shim.efi to the USB .../EFI/Boot/bootx64.efi.  Also copy the grubx64.efi to the EFI/Boot/grubx64.efi.  There should be  the working grub.cfg in the USB .../EFI/ubuntu/grub.cfg  This grub.cfg  runs Ubuntu off the hard disk.  You can edit a menu item so when you see  grub, you know which grub.cfg is being used.  With USB boot before the  Hard disk priority, you should be able to insert the stick and boot  Ubuntu.  Without the stick you still boot Ubuntu, but you can go back to  Windows by copying the /boot/efi/EFI/Microsoft/bootmgfw.efi to  /boot/efi/EFI/Boot/bootx64.efi (overwriting the existing bootx64.efi  which is just a copy of grubx64.efi (unsigned).)  Windows should now  boot again off the hard disk.  Any efi files in the hard disk EFI/ubuntu  directory are probably the unsigned versions (you can confirm that they  have different sizes from the signed versions).  They should not be  used, but I'd make a copy of the working (signed) files and put them  there for the day when everything works as it should.  The Windows grub  items I found did not boot successfully, even with the correct  boot-repair syntax, so I added myself to the existing bug.  Good luck in  straightening things out.  Remember that you might have to go back to  Windows and flash the firmware, before you can secure boot Ubuntu.

---

