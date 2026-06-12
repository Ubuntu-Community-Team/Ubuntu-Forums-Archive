---
title: "HELP - Trying to install Ubuntu 7.10 OVER XP - NTLDR issue"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by michael.freedman on 2008-02-12
Ok - heres the deal. I have a desktop with windows XP on it. I hate windows (I have a mac lappy) - so wanted to install ubuntu 7.10 over it. No problem, went through the whole install process and rebooted - only to get NTLD is missing...

SO here is the deal - I DONT want windows - just my lovely Ubuntu. In the past when I have had Windows issues and I get this message, I have had to 'repair' windows or use a repair CD or something.... but I can only assume that the way Linux boots up is different to Windows - so the question has to be asked, why, when I have rid myself of windows, is the message appearing??

Please let me know - I want to get away from the darkside. I am a Windows 'professional' but I want nothing to do with it at home!!

Please respond soon,

Mike
:)

---

### Post by Pumalite on 2008-02-12
DBan your drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Delete anything left in your hard drive if any. Make 3 partitions in your hard drive:
10 GB for '/'
1 or 2 GB for /swap (/swap=RAM)
The rest for /home.
Install Ubuntu, go Manual and use already prepared partitions.

---

### Post by Herman on 2008-02-12
Take a look in your BIOS settings, you might need to [    Turn off MBR antivirus or write protect]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect") to allow any program to write to your MBR.

Regards, Herman :)

---

### Post by michael.freedman on 2008-02-12
ok,

3 further questions:

1) Why am I having this problem in the first place - does it have something to do with the differences in which Linux boots up to Windows? How do they differ (the way they boot up I mean!).

2) Why doesnt formatting the dirve using the partion manager on the CD based system of Ubuntu get rid of the Bootloader for windows?

3) I understand there being no drive letters and everything coming from root - but why do I need to segment my drive for different volumes

Mike

> **Herman said:**
> Take a look in your BIOS settings, you might need to [    Turn off MBR antivirus or write protect]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect") to allow any program to write to your MBR.

Regards, Herman :)

---

### Post by Pumalite on 2008-02-12
Follow Herman's advice first. Beyond that; Windows many times leaves your drive littered. You have to clean it. Second, you could hang everything from '/' (root), but is better to have a separate /home partition because you can save your /home for future reinstalls. Third, if you use 'Guided>Use Entire Disk', the system will create 2 partitions at least: root and /swap.

---

### Post by Herman on 2008-02-12
> I understand there being no drive letters and everything coming from root - but why do I need to segment my drive for different volumes In Linux we use a separate partition called a 'swap' area or partition instead of a 'page file' for the slower moving items in memory. It's useful especially for older computers that lack RAM, but at least a small swap area is probably still a good idea even if you do have plenty of RAM.
You need at least one more partition for '/', (the root, or main part of the file system).
Some people believe it's also useful to have the /home directory in a separate partition. Your /home directory will contain all your personal files and settings. Therefore it's (theoretically) possible to destroy the rest of the your system somehow and re-install it again and have your personal files and settings remain intact. 
Personally, I prefer a single partition (plus swap area) installation for the sake of tidiness, (no separate /home partitions), since I like to multi-boot, and have three or four or more operating systems in each computer. Even if people do have /home on a separate partition doesn't mean they no longer need to back up their data to some separate media. For that reason I don't see the logic in creating a separate partition for /home myself, but a lot of better and more knowledgeable people than me do think it's best to have a separate /home partition. :)
> Why doesnt formatting the dirve using the partion manager on the CD based system of Ubuntu get rid of the Bootloader for windows? Because the MBR is not part of any file system.
The MBR is located in the first sector of the hard disk and neither the first sector or even the entire first track of the hard disk are allowed to be occupied by any file system. The first partition doesn't begin until sector number 63.
The partition editor write to the partition table in the MBR of course, but it leaves the boot loader section of the MBR for the boot loader program to deal with.  :)
> Why am I having this problem in the first place - does it have something to do with the differences in which Linux boots up to Windows? How do they differ (the way they boot up I mean!). When Windows boots up, the BIOS looks at the stage1 code in the MBR (roughly speaking) and is directed to the Windows boot sector, which is the first sector of the Windows partition, commonly sector 63 but it could be any sector on the hard disk. If there's no stage1 for Windows in the MBR, the BIOS boots whichever partition is marked 'active' (with the boot flag). From the boot sector, code engages NTLDR, NTdetect.com, and boot,ini to begin booting  Windows. You are getting an error message because there's no Windows boot sector there anymore. Your error message about NTLDR being missing is part of the MBR code, you would be able to see if if you do,```
sudo dd if=/dev/hda count=1 | hexdump -C
``` from a Linux Live CD or operating system, where 'hda' is your first hard disk, replace with 'sda' id SCSI or SATA.

When Ubuntu boots, GRUB's stage1 code should be in the boot loader part of the [MBR]("http://users.bigpond.net.au/hermanzone/p6.htm#What_is_the_MBR_or_Boot_Sector").  The MBR directs the BIOS to the GRUB's stage2 files in the Ubuntu partition. It may use the optional GRUB stage1_5 code in the next fifteen sectors of the first track of the hard disk. stage1.5 understands file systems, so GRUB can find files by file name rather than just relying on sector numbers.
Grub's stage2 finds your [/boot/grub/menu.lst]("http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst") file (equivalent to boot.ini), and presents you with your [GRUB menu]("http://users.bigpond.net.au/hermanzone/p15.htm#gui"). From there the user can select GRUB or Windows. If there's only one operating system in the computer, you may not see the GRUB menu, GRUB will just boot Ubuntu automatically. If there's no menu.lst file or there's a problem, you may get [GRUB's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") instead. GRUB is almost an operating system of it's own, and GRUB's command line can be used to do all kinds of things to get your computer booted that aren't possible with any other boot loader, as explained in that link.
When GRUB boots Ubuntu, it loads the Linux kernel into the RAM.
GRUB doesn't boot Windows If present) directly, it hands over that job to Windows bootloader by 'chainloading' the code in the Windows boot sector and lets Windows boot loader boot Windows.
Here are two links that also might be useful, [The bootstrap mechanism used in GRUB]("http://www.gnu.org/software/grub/manual/html_node/Bootstrap-tricks.html#Bootstrap-tricks"). and [The Linux Boot Process]("http://oldfield.wattle.id.au/luv/boot.html")

Regards, Herman :)

---

### Post by Pumalite on 2008-02-12
WOW. My hat is off.

---

### Post by michael.freedman on 2008-02-14
Ok,

Thanks for all the info, but still nothing is happening here.

Allow me to provide you with more info....

- I have 2 drives - 1 SATA drive and 1 regular ATA drive. (both 80GB)
- The SATA in BIOS is booted first...and the IDE is last (i.e. it should never be booted from)
- In the Ubuntu 7.10 install, the ATA drive is picked up as SDA and SATA drive is SDB. - i.e. the ATA drive is seemingly picked up first????
- There is nothing on either system
- The desired effect is a whole Ubuntu install on SATA drive, with the ATA drive being used as storage.
- The system is an old Dell system (P4 based) with no options of antivirus overwrite (or something to that ilk) in the BIOS.

I dont do anything special in the install - I just use the sdb drive for the install and thats it - it should take over. But when I reboot - I just get the NTLDR problem. Time and time and time and time and time again this happens...................

AHHHHHHHHHHHHHHHHHHHHHHHHHHHH

---

### Post by Herman on 2008-02-14
>  - I have 2 drives - 1 SATA drive and 1 regular ATA drive. (both 80GB)
- The SATA in BIOS is booted first...and the IDE is last (i.e. it should never be booted from)
- In the Ubuntu 7.10 install, the ATA drive is picked up as SDA and SATA drive is SDB. - i.e. the ATA drive is seemingly picked up first????
- There is nothing on either system
- The desired effect is a whole Ubuntu install on SATA drive, with the ATA drive being used as storage.
- The system is an old Dell system (P4 based) with no options of antivirus overwrite (or something to that ilk) in the BIOS. AHA! It's the old PATA/SATA multiple hard disk issue! :)

Please boot your Ubuntu Live CD and post the output from 'sudo fdisk -lu' here please,
```
sudo fdisk -lu
```A look at your /boot/grub/device.map would be handy too,
```
cat /boot/grub/device.map
```We'll just need to manually install GRUB to MBR in the firsdt SATA hard drive and then we'll need to edit your /boot/grub/menu.lst file or you'll be stuck with GRUB error 17. 

Please post the bottom half of your /boot/grub/menu.lst file here as well and I'll fix it for you.
You can gain access to your hard disk installed /boot/grub/menu.lst from the Ubuntu Live CD after you mount your hard disk installed Ubuntu file system in the Live CD. Here's a how-to about that, [                                  Mount a Ubuntu ext3 or reiserfs filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD").

Regards, Herman :)

---

### Post by michael.freedman on 2008-02-15
Hey Herman,

Thank you so much for all the help...BUT.....

I took out the ATA HDD and it all worked. The ATA was getting a bit worn out - so I just decided to stick to the faster technology!! :)

UBUNTU 7.10 - here we come!! Now all I gotta do is figure out how to work the damn thing and turn it into a fileserver and use Samba - which is ultimately this machines destiny!!

Thanks again Herman, the world of GNU and open source just wouldnt work without people like you!!!

All the best,

Mike :guitar:

---

