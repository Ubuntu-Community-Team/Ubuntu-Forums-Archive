---
title: "How To Suscessfully Install Ubuntu Server From A Flash Drive?"
date: 2015-11-17
forum: Installation &amp; Upgrades
---

### Post by Benjaman_Woolner on 2015-11-17
Hi I'm hoping that this forum may be of more help to me than the AskUbuntu StackExchange based site has been, which won't be hard seeing as no one has even responded there.

[COLOR=#111111][FONT=Ubuntu][B]My Aim
[/B]I am trying to install Ubuntu Server 15.10 32bit onto an old PC. This is not a dual boot install nor is it to a partitioned HDD. I fully formatted the drive, including removing all partitions, using windows before I attempted this.I am trying to run the installer from a flash drive which Linux detects as sda, with my HDD being sdb.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][B]My Error
[/B]Installing Grub via the automated prompt returns the following[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]"Unable to install GRUB in /dev/sda. Excuting grub-install /dev/sda failed. This is a fatal error"[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu][B]What I've Tried
[/B]I tried manually telling it to install to /dev/sdb, all seemed well, the install seemed to finish just fine. I used the option to reboot, removed the flash drive as instructed (remove bootable media). All I get when loaded is a blank plain black screen, no blinking cursor or anything, which I assume is not correct. It also seems unresponsive to anything I type.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]The computer seemingly will not boot into Ubuntu with or without the flash drive inserted.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've tried to run a check for disk defects which just gave me a screen that constantly flicked from black to white and back again.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I've tried repairing the installation, installing the grub to /dev/sda and rebooting only to return to the same blank black screen.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This shouldn't be this hard. Where am I going wrong, what can I do to turn my old pc into a working web server?

The PC itself is an old Packard Bell with the following specs:
MS-6786 VER:2 Motherboard
AMD Athlon XP 3200+ Processor (AXFA 3299 DKV4E)
2x 1GB 400Mhz Ram
80GB Western Digital HDD[/FONT][/COLOR]

---

### Post by yancek on 2015-11-17
> [COLOR=#111111][FONT=Ubuntu]I fully formatted the drive, including removing all partitions, using windows before I attempted this[/FONT][/COLOR]

Can you clarify the above statement?  I read it as you tried formatting for Linux from windows.  That won't work as windows isn't capable of formatting for a Linux filesystem.  Or did you simply mean you had been using windows as your OS before trying this? 

Did the actual installation finish and the problem is simply with Grub?  From your post, you would have needed to select Device for bootloader installation as /dev/sdb as that is the hard drive you want to use. The default would have been /dev/sda and that wouldn't have worked as that is what you were using for the install.  I haven't done an install of the server version so I don't know what options you have, if they are the same as the standard Desktop?

---

### Post by Benjaman_Woolner on 2015-11-17
The HDD was previously installed and running windows with a partition so I installed in into another window's machine, removed the partitions and formatted the drive so it was to the best of my abilities a clean slate as it were.

Running with the grub install automatically selected to /dev/sda I couldn't get beyond the error message posted above, when manually selecting to install the grub to /dev/sdb it carried on the install with no messages, asks about universal time then says it's ready to reboot so I assume it's all worked and installed as it's meant to.

This is my first time of installing Linux of any form so I'm not 100% sure what to expect. Thank you for replying too

---

### Post by Bucky Ball on 2015-11-17
You don't want to format the drive with Windows. Just leave it as free space. Windows can't create partitions that Ubuntu can install onto. 

Drive with nothing but free space, boot from your install USB, install Ubuntu server. You will be given the option to create the partitions for Ubuntu during install when you choose 'Something Else' at the partitioning section.

There are many sites explaining how to install Ubuntu server. [Here's one]("http://www.ubuntu.com/download/server/install-ubuntu-server") that might help. Just read 'DVD' as 'USB'.

---

### Post by Benjaman_Woolner on 2015-11-17
I've ran the installer, I've told Ubuntu to use the entire 80GB space on the HDD. Thats not my issue. My issue is if I let the system decide where to install the grub it selects /dev/sda and throws an error, if I select no to automatically installing the grub, then tell it to install to /dev/sdb the install process seems to finish but when it reboots all I seem to get is a blank black screen, no cursor blinking away, no text output or anything and seemingly no response to my attempts to type on that screen.

---

### Post by Bucky Ball on 2015-11-17
Well, it sounds like you are rebooting either with the install media still in and/or you're not entering BIOS and changing the boot device back to the hard drive. 

Reboot with the install media out. If you have Ubuntu installed, put that aside.

---

### Post by Benjaman_Woolner on 2015-11-17
The bios is set to flash-hdd, cd-rom, hdd, as the system reboots the flash drive is already removed, there is no disc in the cd-rom so it should be starting from the HDD right?

Assuming it's all installed correctly what would I see after bios, a Ubuntu logo loading screen, a cursor of some sort?

---

### Post by Bucky Ball on 2015-11-17
You would eventually get to a login screen. 

- When you are at the black screen, can you hit control+alt+F1 and login to the TTY there? 
- Have you tried [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair")? 
- Does Ubuntu run okay from the install media when you 'Try Ubuntu' rather than install it? 
- Where did you download the ISO, how did you create the install media, did you 'Check installer for defects' prior to installing (an option at the initial menu when you boot from install media) or check the md5sum?

---

### Post by Benjaman_Woolner on 2015-11-17
I'm wondering if maybe when I've tried to install if it's tried to install nearly everything to the flash drive as I've not seen option prior to the grub installer where I have the opportunity to change locations.

Having made sure that there is no disc in the cd-rom and that the flash drive is removed the system loads the Packard Bell splash screen with the options of hitting f2 for bios and f10 for boot options. After that the bios seem's to sit waiting for the cd-rom, another reason I think it may not have installed correctly to the HDD.

Next time I get to the blank black screen I will try the control+alt+f1 option and see what happens.

I tried a boot repair but only so I could install the grub to /dev/sdb, when I run the system of the flash drive I don't see options for Try Ubuntu.

The ISO came from [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads). On that page under the Ubuntu 15.10 I selected Ubuntu 15.10 Server (32-bit). I've used PenDriveLinux to create the bootable flash drive, I ran the "check disc for defects" option but when I do that I get a blinking cursor in the bottom left corner of the screen, whilst the screen itself flickers black and white repeatedly.

---

### Post by yancek on 2015-11-17
I would try setting the HD to first boot priority even though no flash drive or CD is in.  Simple to eliminate this as a problem.

If you tried boot repair, you should have posted a link suggested with the detailed info.  Run it again and select the Create Bootinfo summary option and post the link here.

If the check disk for defects isn't successful, it may be a bad download or a bad burn to the flash drive.

---

### Post by sudodus on 2015-11-18
> **Benjaman_Woolner said:**
> ...

The ISO came from [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads). On that page under the Ubuntu 15.10 I selected Ubuntu 15.10 Server (32-bit). I've used PenDriveLinux to create the bootable flash drive, I ran the "check disc for defects" option but when I do that I get a blinking cursor in the bottom left corner of the screen, whilst the screen itself flickers black and white repeatedly.

The download site is OK, but maybe there was a transfer error during the download.

Please check the iso file with md5sum, that the result matches the string listed at [UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

There might also be problems when you transferred the content of the iso file to the pendrive. You could try another tool, [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) which is a very reliable tool because it simply clones/flashes/burns/ the iso file into the pendrive.

But all these things might work, and real problem might be related to the graphics, that there is no good driver in 15.10 for your old graphics chip/card. If that is the case, you might have better luck with an older version. It is worth trying one of the long time support versions (with 5 years support from the release date), 12.04 LTS or 14.04 LTS.

The installer of Ubuntu Server 12.04 LTS might boot only from CD/DVD (not USB), while the installer of Ubuntu Server 14.04 LTS boots also from USB.

---

### Post by Benjaman_Woolner on 2015-11-18
> **yancek said:**
> I would try setting the HD to first boot priority even though no flash drive or CD is in.  Simple to eliminate this as a problem.

If you tried boot repair, you should have posted a link suggested with the detailed info.  Run it again and select the Create Bootinfo summary option and post the link here.

If the check disk for defects isn't successful, it may be a bad download or a bad burn to the flash drive.


I tried changing the boot priority to HDD first to no avail. I don't know if the check disk is working as the screen flickers black and white with the cursor in the bottom left corner, no text is displayed to say progress is being made so after 10-20mins I turned the pc off.

I just tried the boot repair option again and this is what I've found

Sits on Bios screen, blinking cursor after Verifying DMI Pood Data ... Update Success


Ubuntu Installer Boot Menu

[LIST]
[*]Install Ubuntu Server
[*]Multiple server install with
[*]Check disc for defects
[*]Test memory
[*]Boot from first hard disk
[*]Advanced Options
[LIST]
[*]Back
[*]Rescue a broken system
[/LIST]

[*]Help
[/LIST]

During Rescue Mode I am asked to enter the device you wish to use as my root file system

[LIST]
[*]  /dev/sda1 (my flash drive)
[*]  /dev/sda5
[*]  /dev/sdb1 (my hdd)
[*]  Assemble RAID array
[*]  Do not use a root file system
[/LIST]

Choosing /dev/sdb1 (my hdd) gives me the following error:
An  error occurred while mounting the device you entered for your root file system (/dev/sdb1) on /target. Please check the syslog for more information.

Choosing /dev/sda1 (my flash drive) gives me these options:

[LIST]
[*]  Execute a shell in /dev/sda1
[*]  Execute a shell in the installer enviroment
[*]  Reinstall GRUB boot loader
[*]  Choose a different root file system
[*]  Reboot the system
[/LIST]

Clicking *Go Back* from the Device Selection stage of rescue mode takes me to the Ubuntu Installer Main Menu with the following options:

[LIST]
[*]  Choose language
[*]  Configure the keyboard
[*]  Detect and mount CD-ROM
[*]  Detect virtual driver disks from hardware manufacturer
[*]  Load installer components from cd
[*]  Detect newtork hardware
[*]  Configure the network
[*]  Configure the clock
[*]  Partition the disks
[*]  Install the system
[*]  Configure the package manager
[*]  Select and install software
[*]  Install the GRUB boot loader on a hard disk
[*]  Continue without boot loader
[*]  Finish installation
[*]  Change debconf priority
[*]  Check the CD_ROM(s) integrity
[*]  Save debug logs
[*]  Execute a shell
[*]  Eject a CD from the drive
[*]  Abort the installation
[/LIST]

This is the screen I've left it at for now, but it strikes me that the installer has probs tried to install on the flash drive and not the HDD. I might try my luck with an older version as suggested and see if I have better luck that way. I'm stopping to grab a bite to eat now but will check for other possible solutions before trying an older version.

Thank you all for the help so far

---

### Post by sudodus on 2015-11-18
We can wait a while, but one alternative is to move your thread to the [Server](http://ubuntuforums.org/forumdisplay.php?f=339) subforum, to find people who know more about Ubuntu Server.

---

### Post by Benjaman_Woolner on 2015-11-18
Ok I've just ran the "[COLOR=#000000]Check the CD_ROM(s) integrity" and it's come back saying test failed "The./install/netboot/ubuntu-installer/i386/pxelinux.cfg/default file failed the MD5 checksum verification.

I guess now my best option would be to try one of the older suggested versions.[/COLOR]

---

### Post by oldfred on 2015-11-18
Which drive is sda & sdb during install.
Normally your hard drive is sda. And grub always installs to sda as default.
But a few BIOS promote flash drive to sda and make internal hard drive as sdb. Then you have to install grub to sdb. But you should see whether sda or sdb is the 80GB drive.

Then when booting with just one install you do not see grub menu. You have to hold shift key to get a grub menu. And if boot issues or if you need boot parameter in grub to resolve a boot issue, you have to have grub menu to edit it.

---

### Post by sudodus on 2015-11-18
The first step when that test fails is to check the iso file

```
md5sum filename.iso
```

and download again until it matches the listed string. Using a torrent should be fail-safe.

The next step, when you know that the iso file is good, is to try again to make a CD/DVD/USB boot drive as suggested in post #11, maybe with another tool.

When "Check the CD_ROM(s) integrity" finds no error, it might work to install Ubuntu Server :-)

Otherwise the next step is to try another version (one of the older suggested versions).

---

### Post by Bucky Ball on 2015-11-18
Or even the [minimal install]("https://help.ubuntu.com/community/Installation/MinimalCD") and choose the Ubuntu server machine profile from tasksel during install? Just a thought ...

You'd need to be online with a cable for a mini install.

---

### Post by Benjaman_Woolner on 2015-11-18
OK that was a weird one. I decided to switch to Ubuntu Server 14.04 LTS, again I found myself with a initial menu that was missing the option to run a MD5 check.

When I tried to install it came up trying to mount/unmount something which failed, as I went to make a note of the error I was surprised to see the installation process had continued and was giving me the options to select my keyboard layout.

I followed the process through, created my own partitions and carried on with the installation and I'm pleased to say I seem to have a working system now.

Thank you for your assistance and perseverance with my issue. I'll try not to ask too many questions but should I find myself struggling with something I will definitely try for help here rather than on the Stack Exchange style sites.

---

### Post by sudodus on 2015-11-18
Congratulations and thanks for sharing your solution :KS

Welcome back with a new thread when you have another problem or question!

---

