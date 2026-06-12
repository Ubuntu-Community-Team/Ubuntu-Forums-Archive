---
title: "[SOLVED] Trouble installing from USB - Toshiba Satellite Clean HDD"
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by david268 on 2014-08-22
Hello Everyone, 

I'm really excited about switching over to Unbuntu, however, I'm have a few issues and most of them are user error.  Here's the problem that I'm having:

I'm booting Kubuntu 14.04 64 bit from an .iso on USB.  I have no problem loading Kubuntu, I'm currently using "Try Kubuntu" on the machine I'm trying to install to while visiting this forum.  However, after selecting "Install" and working through the installation process, my machine isn't able to boot from the hard drive.  I've tried formatting the disk manually according to directions I've found from this community, and I've used the guided installer.  However, I originally made a few serious mistakes which I'll remedy later, but these are the exact processes I performed:

Downloaded .iso file directly from Kubuntu to my USB drive. I dragged/dropped file to Desktop on Windows, then used the provided program suggestion to format my USB drive with fat32 (entire drive) to boot Kubuntu from USB and rewrote USB.

At that time, I had Windows 8.1 installed on my Toshisha Satellite.  I booted from USB and followed the prompts to install Kubuntu.  My computer shut off with 89% completion and file was corrupted when trying to load from dual boot.  I tried to reinstall, only this time I selected write to entire disk "guided".  This of course effectively erased my entire disk.  I only wanted Kubuntu on this machine anyway, but not with the problems that I've caused myself so far :)  

Now, the installer appears to work perfectly, and Kubuntu appears to recognize itself written to my entire machine when I reenter the install program, but I can not boot from the hard drive, only the USB which must remain plugged in. When I first turn on my computer, the toshiba loader appears, and then say that you must select proper drive to boot, even though the hard drive is first in the configuration.  I have to press f12 and boot from USB, and I return to the "Try Kubuntu" "Install Kubuntu" loading application.  

I really hope that someone can help me. Thank you, 

David

**EDIT**  I cuurently do not have access to DVD/CD drive or another machine, I'm traveling.  I also, Used Checksum to verify .iso

---

### Post by ubfan1 on 2014-08-22
Take a look at your EFI partition, and see what got installed.  There was a bug just mentioned (sorry didn't note it) which indicated that some file (grub.cfg) needs to be in /EFI/ubuntu, not /EFI/kubuntu .  If you just have a /EFI/kubuntu directory, try making a /EFI/ubuntu directory and copy everything over.  You can check your nvram paths with "sudo efibootmgr -v"  and see which path kubuntu is using.  Wherever it is, grub, when it runs, will look in /EFI/ubuntu.  Another "fallback" upon failure is to put a copy of the bootloader you want to run into /EFI/Boot/bootx64.efi.  If it's shim, put a copy of the signed grub.efi there too.  As before, the grub.cfg file needs to be in /EFI/ubuntu.

---

### Post by david268 on 2014-08-23
I've read a lot of material based on the information that you've given me.  Thank you.  You should know that there wasn't an EFI/kubuntu or EFI/ubuntu directory in either the USB or on the Hard Drive.  The only EFI file was located in the USB (except for efi in Boot on the HD..  I located the grub.cfg, but I could not create a new folder in EFI on the USB due to not having or being able to obtain root permissions (I would have attempted a new install).  I've since tried many other paths mostly through the terminal, but without success.  I ran boot-loader and ended up with this.. [http://paste.ubuntu.com/8119444/ ]("http://paste.ubuntu.com/8119444/")

---

### Post by ubfan1 on 2014-08-23
You shouldn't need to change the USB, but you could alter the USB's grub.cfg file to actually boot the hard disk.  Your EFI partition has the /EFI/ubuntu directory according to the boot-repair info, but the last efibootmgr listing on that output didn't have the /EFI/ubuntu/shim boot like the middle one did (near end of listing).  Try the efi boot menu, F12 I think on your Toshiba, select the HDD, then you should get another window in which you can choose ubuntu (or Windows).  You look like you have a secure boot enabled setup, which should work on your Toshiba too.  Once you successfully log in, you could use efibootmgr to put the ubuntu as the default boot, but Windows will keep resetting it anyway, so I just stick with the EFI boot menu.  When successfully booted, the EFI partition  gets mounted at /boot/efi, so you can edit and copy files around.

---

### Post by oldfred on 2014-08-23
Some other threads with Toshiba.
It seems many Toshibas have very limited UEFI.

 TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)

You may be able to create a /efi/boot folder and copy grub into that for booting hard drive or use rEFInd.

---

### Post by david268 on 2014-08-25
I want to thank you ubfan1 and oldfred for taking the time to offer your assistance. I have tried all that you have suggested, and I've come to a dead end.  It seems that my only option is to give up on using Linux.  

Everything that I've tried since my last post...

-Bought four new flash drives
-Downloaded a new copy of Ubuntu instead of Kubuntu, verified the .iso and prepped drive to boot. Same exact problem on install.
-Ran boot-repair again, received the same message.  
-I'm unable to create new folders or make any changes to anything without permission (I'm not the owner) I don't have a username and   password to log in as one.  
-Tried to download rEFInd, through a terminal, followed every direction explicitly and failed.  It seems my "file system" is located in /cow and so I can't proceed by any example located on his website for troubleshooting.  
-On start-up everything is the same.  I have my HDD first, USB second.  I can not load from HDD in BIOS with F12.  There is nothing to boot.  I have to have my USB plugged in to boot from it.  
-I've tried every possible combination for updating grub, allocating and creating my own partitions, including grub, efi, boot, home, etc based on the info from Ubuntu.  I've tried MANY installs with all possible combinations, secure boot on and off, booting without UEFI, Intel fast boot on//off, signed into internet to update files and third party software- and not, using the command promt to place grub back into sda... basicaly I've tried everything that has been noted in any solved thread here, on askubuntu, and any other bootloader/bootmanager related software site referencing problems for Ubuntu and the rest of the flavors.

I don't mind paying someone to fix this, and I need it done now, I've spent two days on this, and over 10 hours reading and trial by error, to solve this problem.  It's beginning to get absurd.  Software that you can download, but not boot after installing.  This includes Lubuntu, Kubuntu, and Ubuntu, all on different types of usb's, all .iso sd5sum verified, and created using Ubuntu startup disk creator, installed with each individual installer, and (minues my trials with formatting manually) using the guided installs.  I don't even have another OS on this system.  It is a clean fresh install.  

I'm truly at a loss.  I know I will like this system, and even come to love it and be a part of the community.  I'm aware the the majority of users of this system are programmers and developers, and that 90% of those who install this can find 150 work arounds for solving this problem.  I'm competent as a user, and even have some very advanced skills, but they are all peicemeal from 15 years of solving my own problems and finding solutions as I was confronted with them.  This it seems, is beyond me, at least with my time constraints.  I have to have a functioning machine tonight, or I have to run back to Windows with my tail between my legs.  

Despite my rant, I just wanted this on record on the forum.  But I truly thank you guys for your contribution here, and for doing what you could to help me.  

David

New boot-repair for Ubuntu [http://paste.ubuntu.com/8138153/](http://paste.ubuntu.com/8138153/)

---

### Post by christopher9 on 2014-08-25
I have a Toshiba P50 and have been through this more than a few times myself...

If the USB boots up ok, use the Software Center to download a program called GParted. Use the File Manager on the USB  to look at the entire computer.  The hard drive should appear as an unamed item with a large capacity count. Use Gparted to wipe out all the partitions on the hard drive. You will lose everything on there but since you can't use it anyway it's of little value right now.  Next reboot from the USB and Install the OS. Since you wiped out all the partitions, you should get a clean install and it will manage setting up the new partitions and installing the boot loader.  Once it's done installing, shutown the computer, remove the USB. Restart the computer.

---

### Post by david268 on 2014-08-25
I've attached a photo of Gparted.  I've erased my disk several times during the install process.  The last install was partitioned manually, as you can see.   Do you believe that your suggestion would still apply in this case?  

Thank you, 

David

Most recent boot-repair [ http://paste.ubuntu.com/8139201/]("http://paste.ubuntu.com/8139201/") Manually partitioning the EFI and giving it a boot label made a difference for writting the grub.efi files. This is the only partition with a primary designation.  I also turned off the LAN in bios.  I'm sure I'm getting to the very end of possible combinations to check if this is some kind of systems incompatibility.  My bio's version is 1.20

---

### Post by christopher9 on 2014-08-25
Delete those partitions....that space should ALL be unallocated. Give boot-repair a rest...since you are not trying to dual-boot right now a clean install is what you want.  Once you get it installed and booted up on the HDD, then configure (you DON'T want to install software updates from a CD so leave that unchecked) and run Software Updater to get the latest updates before you do anything else.

---

### Post by david268 on 2014-08-25
Thank you for your help christopher9

All instructions explicitly followed.  Grub will not recognize the install on HDD, or more accurately, GRUB will not load if my USB isn't plugged in.  I checked by entering bios, and manually selecting the HDD, even though it is first in order.  I have to boot from USB.  I only have 2 options for Ubuntu, try or install.  I've tried this too many times.  Where can I find paid support?  I've just been going in circles for days now.

---

### Post by christopher9 on 2014-08-25
There are many folks are here a LOT smarter about Linux than me, perhaps one of them will respond soon....I guess I'm a little confused that wiping out the entire HDD doesn't allow a clean install.  I'm wondering now if your ISO might not be corrupted.....did you run the checksum against your download to insure its validity ?  BTW, just to be clear you are booting up to a Grub> prompt, correct ?

---

### Post by oldfred on 2014-08-25
If you look at lines 8665 Boot order, it does not show Ubuntu as a boot option anywhere. There are three boot order entries.
Your previous report showed ubuntu as the entry only on one of the Boot Order lists, and then you had secure boot kernels installed.
I do not know but believe the boot orders are for UEFI secure boot, UEFI (not secure boot) and next boot as those all are UEFI boot options. And then there is a BIOS boot option.

Do you have a one time boot key like f12? Some systems will boot from that when directly booting from UEFI does not work. You do not show secure boot kernels installed now, so make sure secure boot is off.

It does not look like the installer creates a /EFI/Boot folder anymore. That would have bootx64.efi which directly booted from hard drive. Some have had success creating that folder and copying grub into that folder and setting system to boot hard drive.

       From live installer mount the efi partition on hard drive:
mount /dev/sda1 /mnt
mkdir /mnt/EFI/BOOT
cp /mnt/EFI/ubuntu/* /mnt/EFI/BOOT
mv /mnt/EFI/BOOT/grubx64.efi /mnt/EFI/BOOT/bootx64.efi

I have seen Toshiba boot the ubuntu UEFI entry, but HP and Sony do not. They have modified UEFI to only boot the entry in /EFI/Microsoft/Boot. You could also recreate the Microsoft folder and put grub into it like this thread.
 Ubuntu only on HP, recreate Windows folder and grub as Windows boot file
[http://ubuntuforums.org/showthread.php?t=2238714](http://ubuntuforums.org/showthread.php?t=2238714)

---

### Post by david268 on 2014-08-25
I have created all the folders for Boot and EFI following the two tutorials for example...

drwxr-xr-x 2 root root 4096 Aug 25 22:25 Boot
drwxr-xr-x 3 root root 4096 Aug 25 22:17 Microsoft
drwxr-xr-x 2 root root 4096 Aug 25 21:54 ubuntu

I just realized something.  Even though I've been running all of these processes, they are not permanent.  My USB contains the mnt/EFI/xxx but my HDD does not.  I can not gain permission to move them over, or to gain write access to the media (I've follow several tutuorials).  When I turn my computer off and on, everything that I've done is wiped from USB.  It is the same with running boot-repair and anything else that I run through the command prompt - the changes made are not happening to my HDD.  Of course, when I try to "view" the root file in my HDD it won't allow it.  So, I've followed the tutorials for creating a Boot file and a Microsoft files (on my USB only), what is the next step?  I've tried to search for it on my own, but I don't know the right question to ask.


> **christopher9 said:**
> There are many folks are here a LOT smarter  about Linux than me, perhaps one of them will respond soon....I guess  I'm a little confused that wiping out the entire HDD doesn't allow a  clean install.  I'm wondering now if your ISO might not be  corrupted.....did you run the checksum against your download to insure  its validity ?  BTW, just to be clear you are booting up to a Grub>  prompt, correct ?

My ISO (all of them) are verified.  When I boot from USB, I boot into Grub 2 with three options, try ubuntu, install ubuntu, check disk for errors.  If I hit "c" then I will go to Grub>.  If my USB isn't plugged in, or I try to boot from HDD, then I get an error message paraphrasing "please install boot media and hit any key to boot"  or something like that.  Basically, toshiba screen appears, then goes blank with the error message.    

Thank you, 

David

---

### Post by christopher9 on 2014-08-25
So it's important that you have a dual-boot situation to Windows ? I must have missed that....all I know is that I've had the same exact error message and only the grub prompt on several occasions and in my experience, if I used the USB OS to utilize GParted to completely delete EVERY partition on the HDD and then rebooted and chose 'INSTALL {Operating System of your choice}' the install worked on a Toshiba P50 w/Nvidia GT740M I have been able to successfully install Ubuntu 14.04 (many times over), Xbuntu, Lubuntu, Linux Mint, Deepin, etc. at will...I truly hope you solve this! Wish I could have been more help

---

### Post by oldfred on 2014-08-25
Did you reinstall again?

Your last boot info report showed this:

/dev/sda1           2,048     1,050,623     1,048,576 EFI System partition

---

### Post by david268 on 2014-08-26
Solved.  The answer... SuperGrub2.  I flashed an USB with the supergrub2.iso using dd.  I removed all removable media accept for the USB with the supergrub2.iso. I turned of my laptop, powered on,  and pressed f12 for bios and set the boot order to load USB first.  Save and exit.  Toshiba start screen came on then something amazing happenend... something else.  A little window I haven't seen before popped up and indicated that there was a file that couldn't run because secure boot was on.  So, I Control alt delete, and went back into bios and disabled secure boot.  Save and Exit.  After about 10 seconds of some screen flickering, Grub booted.  (screen was purple this time, instead of black.   I selected Ubuntu, and for the first time, logged into my fresh install.  

Wow, I'm happy.  Anyway,  I made a change to the Desktop so that I could verify everything was working properly, and I shut down.  I removed the USB with the SG2.iso, restarted and went directly into bios to change the boot order back to HDD, save and exit.  My laptop now boots directly into Ubuntu.  I've tested everything, and all is 100%!   Thanks you guys for taking the time to help me.  You have no idea how much I've learned over the past several days.  In the end, it was time well spent with my first crash course with linux.

---

### Post by christopher9 on 2014-08-26
Hooray!! I have been where your were and it wasn't fun....be sure and run Software Updater after first configuring it to catch all the repositories and be sure to uncheck the updates from CD-ROM...you don't want that everytime you try to update...have fun !!!! It's SO much advanced from W*****S....

---

