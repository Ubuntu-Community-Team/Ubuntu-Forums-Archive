---
title: "Installation Problems - n00b"
date: 2011-07-23
forum: Installation &amp; Upgrades
---

### Post by Grafeldr on 2011-07-23
Hi everyone,
 
I am new both here, and to Linux, but I want to teach myself the OS.
 
However, I am having quite some difficulty installing the program.
I have bought myself a brand new system, and everything 'seems' to be ok with the Ubuntu Supported Hardware List, but maybe I am missing something..?
 
I have tried several installation disks, versions and methods, but am really at a loss.
When I try to install via the GUI bootable (both on the 'live' install, and the 64 and 32 bit 'alternative' installs), or with the 'text-based' installers, I get stuck with the following:
GUI Installer:
*BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1) built-in shell (ash)*
*Enter 'help' for a list of built-in commands.*
 
*(initramfs) Unable to find a medium containing a live file system*
 
Now, I am installing on to a brand new drive, never had anything installed on it, (not windows, dos... nothing) so I thought that maybe Linux cannot format drives; so I formatted it to NTFS using a windows format; still no joy.
 
Text Based Installer:
*[!!] Detect and Mount CD-ROM*
 
*Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive. If so you can insert it and try again*
 
Obviously it 'is' in the drive, but for some reason it is not detecting it.
 
I know there are similar posts regarding this issue, but I can't make sense of them. I have never used Linux before, and don't know how to use the commands (yet), so can someone please spell it out in layman's terms so I can get this going?
It will be greatly appreciated :)
 
Also, please do ask if you need any more information, or if you need any specs of my hardware, etc.
 
Cheers

---

### Post by leilei1 on 2011-07-23
Okay boot the live cd then go to System -> administration -> Gparted/partition editor(not sure which name its under.) Then click on device and then set partition table. Everything should be unallocated space. Then go to the icon on the Desktop and follow the instructiuons for the live install. Just select largest continuous free space for the place to install.(If you have more than one hard drive make sure to select the one with unallocated space)

---

### Post by linuxman94 on 2011-07-23
> **leilei1 said:**
> Okay boot the live cd then go to System -> administration -> Gparted/partition editor(not sure which name its under.) Then click on device and then set partition table. Everything should be unallocated space. Then go to the icon on the Desktop and follow the instructiuons for the live install. Just select largest continuous free space for the place to install.(If you have more than one hard drive make sure to select the one with unallocated space)

Please read the post thoroughly.  He can't boot into the live cd.  And having all the space unallocated doesn't matter because the installer has a partitioning step.

OP: Did you check your image before you burned it and burned it at the lowest speed?  See here for proper burning technique.

[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by Grafeldr on 2011-07-23
Hi, thanks for replying.
 
No, the installer does not get to the partitioning stage. I just get to choose 'install' from the boto menu, then i get the 'no live file system' error.
 
When I burnt the .iso I used Infra Recorder in Windows 7, as per those instructions on that link... I did not slow the speeds down, however, as they were not part of the oringinal instructions. Do you really think that will help? The data on the DVD seems to be fully intact and properly operational, and the .iso is actually at another location to where I am now, so burning it again will have to wait until Monday (and this is not something I really want to wait for :( )
 
The DVD loads up and I get the purple menu screen where I select 'Install Ubuntu', but I am thinking that it either does not detect my hard drive, 'or' does Linux need another operating system 'already installed' to work?
I really hope the latter is not the case, else it would seem pointless running Linux... ever!?!

---

### Post by Bucky Ball on 2011-07-23
You might find 10.04 LTS a smoother ride for a newcomer. Longer support also. You can always upgrade later if you feel you want to.

Best, most reliable way to download is to torrent as mdsum is checked in the process.

[http://www.ubuntu.com/download/ubuntu/alternative-download#bt](http://www.ubuntu.com/download/ubuntu/alternative-download#bt)

---

### Post by Grafeldr on 2011-07-23
Well I downloaded three different versions from the 'official' site. If I can't get a legitimate, working copy from there, where else can I?
 
I'm starting to wonder why anyone would want to run Linux at all. I really don't want to give up on this, but I am feeling pretty bummed right now :(
 
Can anyone give me a solution to this problem, except to just 'try another version'?

---

### Post by thefasterblueone on 2011-07-23
Don't get disappointed with Linux yet, give it a chance first. The learning curve is a little steep at first but then you will start catching on and new challenges will come, or you can just get comfortable and enjoy your new Operating System at a leisurely pace.

Burning your disk at the slowest possible speed is _HIGHLY_ recommended.
Checking the md5 hash is a good thing also. All of this is explained in the link linuxman94 gave you, read that page carefully.

Bucky Ball has a good point using torrents as your download process and checking the md5 as it downloads.

Give it a try, it's free!

---

### Post by akand074 on 2011-07-23
I would also try reburning it at a slow speed.

You said the hard drive has no partitions on it at all? In the Live CD can you get to "Try Ubuntu" part? If so do that and test your hardware (should be fine) then select install and have it use your entire disk for Ubuntu. You can also choose "Something Else" if you want to try a manual install which might work better. All you have to do is:

1. Make a partition for your Ubuntu filesystem (minimum 20GB I'd recommend) and set it as EXT4, format it and put it's mount point to "/" without the quotations.
2. Make a swap partition equal to the size of your RAM
3. OPTIONAL make another partition for your config files and data, same as step one make it EXT4, format it but this time make it's mount point "/home" without the quotations.

I hope either works. If you just bought your parts new, you shouldn't have any trouble with Ubuntu 11.04.

---

### Post by Grafeldr on 2011-07-23
Ok, I have tried everything you guys have suggested, save the re-burn at the slowest speeds. I will have to do that Monday though.
 
Thanks for all your help so far. I will let you know how I go Monday evening :)
 
Cheers

---

### Post by jpjohnj on 2011-07-23
currently i had a problem with system performance..........


i installed ubuntu in my laptop.i made 20gb for root and 300gp for swap.does this affect my system performance....


if yes...how to chance the partition size in ubuntu or do i have any solution for that..


i need your help ...............

---

### Post by Bucky Ball on 2011-07-24
> **jpjohnj said:**
> currently i had a problem with system performance..........


i installed ubuntu in my laptop.i made 20gb for root and 300gp for swap.does this affect my system performance....


if yes...how to chance the partition size in ubuntu or do i have any solution for that..


i need your help ...............

Please start a new, separate thread rather than trying to get help on this one. You will get more help that way. Working on two issues at the same time is confusing.

---

### Post by Grafeldr on 2011-07-25
Ok, so I re-burnt the disk at low speed, and it did nothing beneficial...
 
However, I found some info after some googling and found that I simply needed to change my dvd drive to IDE rather than SATA in the bios :/
 
Anyway, it now works and has installed properly :D
 
Thanks for everyone who helped :)
 
Cheers

---

### Post by Bucky Ball on 2011-07-25
Excellent. Please mark as 'Solved' from 'Thread Tools', top right of page.

---

