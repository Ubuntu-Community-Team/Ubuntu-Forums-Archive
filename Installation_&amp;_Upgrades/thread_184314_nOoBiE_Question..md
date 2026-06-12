---
title: "nOoBiE Question."
date: 2006-05-29
forum: Installation &amp; Upgrades
---

### Post by Gymmic on 2006-05-29
Mr. Greenhorn here.

I have attempted to install, in the following setup a dual boot system with windows XP

The Set up: 
Amd Athlon 2800.
Soso KT800 Dragon 2 Board.
running 2gigs of RAM.
Nvidia 5700gt graphics card.
Wireless lan. 

In my system I have 3 Hard drives
1-120 GB
1-60 GB
1-60 GB

and 2 cd/dvd drives

The 2 60GB Drives are raided to create an Raid 0 of 120

The original 120 is partioned one side running windows and the other is attempting to run Ubuntu.

When windows is running it shows windows running from drive D:\.
which is no bing deal, however durring my first attempt at running ubuntu after the install I let the installer dictate what it was going to do.

When it said remove cd. I did, and restarted the system. When the system started to boot, I got the unable to load the operating system error. I searched around and came across an entry here that suggested I tried GAG.  
The boot manager. No solution.

I spoke to my room mate who is running gentoo on his machine and he immediately said, I know whats wrong with your machine.. Let me install GRUB that will solve all your issues.

Well, grub now creates a different error. I get the splash screen from Ubuntu, but then boot fails and i get a dev/hd2 "something" {not actual message} does not exist. I am away from my computer right now so I can not give you the exact error message. Anyhow...
 
the Ubuntu installer does not recognize the Raid so it lists them seperately. 
The main 120 it has it listed having three partitions:

1 ntfs roughly 55gb
1 the partition created by the ubuntu installer. about 52gb
1 swap. 4gb

After going rounds and rounds, i noticed that the ubuntu partition was not set up as bootable so i changed that flag on the install.

Still nothing. ](*,) 
Any sugestions? Or do I have to wipe everythying and start with Ubuntu First?

THANKS !

---

### Post by Monster_user on 2006-05-29
[QUOTE=Gymmic]In my system I have 3 Hard drives
1-120 GB
1-60 GB
1-60 GB

and 2 cd/dvd drives[/QUOTE]

Okay, we need to know the exact order, and connection of those drives. I would guess that your problems lie either with the RAID setup, or the fact that your using an odd mix of drives.

Linux uses the 'hda#' system to list the drives and partitions.

hd = ATA, or SATA Drive

sd = SATA or SCSI Drive. It can also mean any non-ATA drive, that is not specifically supported.

a = The first drive - Primary Master
b = second drive - Primary Slave
c = third drive - Secondary Master
d = fourth drive - Secondary Slave

1 = Is the number of the partition.

hda1 would be the very first partition, usually C:\ in Windows.

hdc4 would be the fourth partition on the third drive. Hdc is usually the CD/DVD drive.

"dev/hd2" Is most likely refering to the second drive(s), or hdb. If the RAID setup is not compatible with Ubuntu, then it may be causing a conlfict. Although that should not have affected the Windows bootup.

SATA drives can start at hda, or hde, or sda, depending on how your hardware is being detected. If it starts at "hda", then your old IDE/ATA drives will start at either hdc if you have only 2 SATA ports, since each port gets a letter.

Are you running a SATA RAID, SCSI RAID, or ATA RAID setup?

Did you install any SCSI, or IDE/ATA cards?

---

### Post by Gymmic on 2006-05-29
The system has the single IDE drive the 120GB Drive listed as the primary.
The 2 other drives that are set up as a RAID are not detected by the board bios. So they do not show up. 

The MB Has onboard raid controllers so the answer to the question being no I did not install a Raid Controller Card.

According to the manufacturerl, when not in use the Raid channels can be used as ide 3 and ide 4.

I think the issue I am having is that the ubuntu installer is looking at the drive differently than when the computer calls up the drive. 

The error i get when i get to the grub screen is 

Booting 'Ubuntu, kernel 2.6.12-9-386'
root (hd2,1)
Error 21: Selected disk does not exist.

But when you look at the edit option of grub, this shows up as a possible option...

Can you  please explain the proper positioning and calling of partitions occurs within Linux.  If this makes sense?:confused: 

I know that there is an issue with the MBR (master boot record) because I installed GAG on there. I want to reinstall Ubuntu because XP works fine on the partition that it is in. 

When the partition tabel shows up on the Ubuntu Installer

It recognizes the Xp partition the Ext3 partition and the swap file. 

How do I know that the installer is putting the information in the right place, and How do i tell grub where to look for the boot information for the Ubuntu and the XP partition.

Because when I am on Grub, and try to launch XP i get an error also.

Thanks in advanced for your help.

---

### Post by Monster_user on 2006-05-30
[QUOTE=Gymmic]Booting 'Ubuntu, kernel 2.6.12-9-386'
root (hd2,1)
Error 21: Selected disk does not exist.[/QUOTE]

Okay, Linux and Grub are two different things.
Linux uses either 'hda1', or 'hdc1' for XP, while grub uses 'hd0,0', or 'hd2,0'.

Try this.
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub)

[quote=Ubuntu Wiki]Using the LiveCD and Overwriting the Windows bootloader

1. Pop in the **Ubuntu Live CD**, boot from it until you reach the desktop.

2. Open a terminal window or switch to a tty (Ctrl + Alt + F1).

3. Type "**grub**"

4. Type "**find /boot/grub/stage1**". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "**root (hd0,1)**", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).

6. Type "**setup (hd0)**", ot whatever your harddisk nr is.

7. Quit grub by typing "**quit**".

8. Reboot.

From: [WWW] [http://ubuntuforums.org/showpost.php?p=117829&postcount=2](http://ubuntuforums.org/showpost.php?p=117829&postcount=2) [/quote]
*I edited it a little bit.*

At step 5.

*"5. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are".*

Your "root" is either '(hd0,1)', or '(hd2,1)'. Since 'hd2,1' is not working, I would try 'hd0,1'.

---

### Post by Gymmic on 2006-05-31
Ok. Let me see how this works.
Would you suggest another way of arranging my drives?
maybe 1 60 for windows.
the other 60 for ubuntu
and the 120 for storage. Any reason why this would not work?

---

