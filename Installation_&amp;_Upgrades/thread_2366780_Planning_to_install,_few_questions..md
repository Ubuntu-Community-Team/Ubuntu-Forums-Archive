---
title: "Planning to install, few questions."
date: 2017-07-21
forum: Installation &amp; Upgrades
---

### Post by Googleness on 2017-07-21
I'm using Windows 10 for some time now and latest updates caused me a lot of trouble. I decided to reinstall Ubuntu on my main machine instead for more stability and less headaches. 

It was some time since I've used a Linux distro as main OS I usually play around VMs and past year I've gained number of Microsoft based Certifications, so I'm bit rusted on linux department.

I plan to install Ubuntu 17.04 and I've got some planning to do first,

My system spec:
Intel Core i7 4790K 
32.0GB Dual-Channel DDR3
ASUSTeK COMPUTER INC. MAXIMUS VII RANGER
Asus Strix NVIDIA GeForce GTX 970
HL-DT-ST DVDRAM GH24NS70
Storage:
2794GB Seagate ST3000DM001-1ER166 (SATA)  
223GB Corsair Force LS SSD (SSD)    
223GB Corsair Force LS SSD (SSD)
- Also using a keyboard and mice from company called speedlink which only the mice requires a driver in order to program it. (Decus & Rapax).
- Asus Generic BT dongle
- only piece of hardware which might cause trouble (maybe) is usb Analog-to-Digital Adapter which I use to convert VHS tapes to video files - not very friendly to use but we might get around it.

My general use is on first SSD I install the OS itself, on the large 3TB HDD I dump all my data (so called /home) and on the second SSD (in windows at least) I install some video games or place important VM disk files which I want to boost their speed.
I also got 2TB external (USB3) HDD which I use with robocopy script to backup my /home equivalent area on the 3TB disk (I cherry pick certain paths to backup and robocopy just update the external hdd to mirror the local hdd state).

So questions,
1. I understand with Ubuntu 17.04 Swap is no longer needed and it is a file based now?
2. Which file system I should use? 
   - Does EXT4 still the way to go?
   - My external backup drive uses NTFS right now, should I use EXT4 as well for it ? any beneficial external drive FS when using linux distro as main os?
3. Can I choose location when installing games\apps etc so I can pick the second SSD drive I've got? or that is a feature of the software itself (let's say steam of going for GOG path?)
   - when setting up a whole different disk for storage considering the linux file system schematic, how does it work? I mount it to /*insert name here* or something? also I guess I will need to set proper permissions so my user account will be able to utilize it?
4. Looking at my hardware - any red flags pops up? drivers I should avoid ? (example, is it safe to use nVidia drivers etc?)
5. I would very much appreciate if you could point me to a recommended book or online guide for Ubuntu17.04\Linux day-to-day use. In my profession I am PC&Network technician but most of my training and professional experience is Microsoft tech based. I would like to fill the gaps in my knowledge.

Thanks for the help!

---

### Post by vocx on 2017-07-21
> **Googleness said:**
> I'm using Windows 10 for some time now and latest updates caused me a lot of trouble. I decided to reinstall Ubuntu on my main machine instead for more stability and less headaches. 

It was some time since I've used a Linux distro as main OS I usually play around VMs and past year I've gained number of Microsoft based Certifications, so I'm bit rusted on linux department.

I plan to install Ubuntu 17.04 and I've got some planning to do first,

My system spec:
Intel Core i7 4790K 
32.0GB Dual-Channel DDR3
ASUSTeK COMPUTER INC. MAXIMUS VII RANGER
Asus Strix NVIDIA GeForce GTX 970
HL-DT-ST DVDRAM GH24NS70
Storage:
2794GB Seagate ST3000DM001-1ER166 (SATA)  
223GB Corsair Force LS SSD (SSD)    
223GB Corsair Force LS SSD (SSD)
- Also using a keyboard and mice from company called speedlink which only the mice requires a driver in order to program it. (Decus & Rapax).
- Asus Generic BT dongle
- only piece of hardware which might cause trouble (maybe) is usb Analog-to-Digital Adapter which I use to convert VHS tapes to video files - not very friendly to use but we might get around it.

My general use is on first SSD I install the OS itself, on the large 3TB HDD I dump all my data (so called /home) and on the second SSD (in windows at least) I install some video games or place important VM disk files which I want to boost their speed.
I also got 2TB external (USB3) HDD which I use with robocopy script to backup my /home equivalent area on the 3TB disk (I cherry pick certain paths to backup and robocopy just update the external hdd to mirror the local hdd state).

So questions,
1. I understand with Ubuntu 17.04 Swap is no longer needed and it is a file based now?
2. Which file system I should use? 
   - Does EXT4 still the way to go?
   - My external backup drive uses NTFS right now, should I use EXT4 as well for it ? any beneficial external drive FS when using linux distro as main os?
3. Can I choose location when installing games\apps etc so I can pick the second SSD drive I've got? or that is a feature of the software itself (let's say steam of going for GOG path?)
   - when setting up a whole different disk for storage considering the linux file system schematic, how does it work? I mount it to /*insert name here* or something? also I guess I will need to set proper permissions so my user account will be able to utilize it?
4. Looking at my hardware - any red flags pops up? drivers I should avoid ? (example, is it safe to use nVidia drivers etc?)
5. I would very much appreciate if you could point me to a recommended book or online guide for Ubuntu17.04\Linux day-to-day use. In my profession I am PC&Network technician but most of my training and professional experience is Microsoft tech based. I would like to fill the gaps in my knowledge.

Thanks for the help!
1. A swap partition was always optional. It was never mandatory. In the old days people had 512 MB or less of RAM, so having swap was beneficial to run heavier loads. Also to hibernate the computer (suspend to disk), you could easily copy the entire contents of your RAM to a swap partition of 2 GB, for example. Nowadays machines very commonly have 8 GB to 16 GB of RAM, so there is plenty of memory to go. If you have an equivalent of 16 GB partition for swap, this is mostly wasted space and you will rarely use it. That is one reason Ubuntu will no longer recommend the swap partition. If you want you can create a swap file, which would work like the "pagefile" in Windows; it is system memory, which will just sit there, and probably will not be used either.

However, if you actually use all 32 GB of RAM, because, I don't know, you are running multiple virtual machines at the same time, then you could still create a swap partition of 30 GB, or whatever you want. It is entirely up to you, depending on how you use your system. If in Windows you never run out of memory, and the pagefile is never used, then in Linux the swap file probably won't be used either.

2. Ext4 is okay. Sure, you can read more opinions, and people can recommend you XFS, btrfs, reiserfs, etc. because they have specific advantages like better journaling or parallel read-write or whatever. But for the regular user, ext4 is as common as NTFS is for Windows. For an external drive maybe you should keep it as NTFS if you need to have the data readily accessible by a Windows machine.

3. If you install things normally from the repositories, using the "apt install" command, or Software Center, Synaptic, etc. it will install to the regular directory "/usr", and depending on the program, it could also install files in "/etc", "/var", "/lib", etc. You should let it install in those directories. Only if you know what you are doing, and if you download manually some programs from source code, in a compressed ".tar.gz", or things like that, you could manually place things in other places, such as "/opt", or "/usr/local". And you could decide in which hard drive to place these directories, for example, "sda1" or "sdb1", etc.

You can mount hard drives in whichever directory you want, just create it first. Very commonly disks are mounted in "/media", such as "/media/extradrive", "/media/backups", "/media/games", or whatever you want. But you can also create directories as a top level directory "/games", or under your "/home", "/home/user/backups", however you want! See these threads [https://ubuntuforums.org/showthread.php?t=2366686](https://ubuntuforums.org/showthread.php?t=2366686) [https://ubuntuforums.org/showthread.php?t=2366697&p=13668208#post13668208](https://ubuntuforums.org/showthread.php?t=2366697&p=13668208#post13668208)

4. I don't see a particular problem with your hardware. Check the Nvidia pages to make sure your card is supported [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
A driver for a mouse? I hate these types of keyboard and mice with many configurable buttons, and flashy colors, but oh, well, who am I to judge. You may notice your keyboard and mouse work, but you cannot use media keys, or configure the keys. I would have a spare, simple USB keyboard and mouse, just in case.

5. There is no point in recommending a day-to-day book on Linux, for several reasons. First, the Linux world changes all the time. Ubuntu 17.04 will be superseded in October by 17.10. In one year, the 17.04 version will be obsolete, so most people will have moved to the next version, and then the next version will come out in April 2018, and then the next, and so on. It's better if you just start using your system and keep having questions, and keep asking yourself, "how do I do this in Ubuntu 17.04?" That will force you to search for the information online, and little by little you will gain a better understanding of the system, and learn actually useful and persistent knowledge like the terminal. You can probably gain a certification of Linux by studying Bash programming (the terminal) and other tools like "grep", "sed", "awk", and whatnot, but it is unnecessary if your job does not actually demand it. Just learn what you need at the moment and build your knowledge by using the system, and trying to solve actual problems that you encounter.

---

### Post by Googleness on 2017-07-21
Thanks you very much for your answer.

some updates,
1. I had to disable secure boot. even though the installer offer to disable it itself without manually disabling it the grub portion of the installation went badly and no bootloader was recognized.
2. proper way was to create uefi usb boot only using tool (I used rufus) and then boot in uefi mode. On partition section of the installer I created 650 MB efi partition and then used rest of the disk for / path.
3. to boot the usb I used e to edit the option and the boot menu and added "nomodeset" to avoid random errors or black screen issues. after the installation completed no problems were encountered and I've installed the proprietary nvidia drivers - no problems at all.
4. Switched to gnome (my proffered environment) and tested, nVidia is not playing nice with wayland so I use the non wayland one.

overall everything worked smoothly only hickup was that I needed to run chown on the second ssd drive so I could use it but steam managed to install a game on that drive so works great.

Advancing as I go I think the only issue will be currently to identify the analog video adapter drivers, but that is a project for another time.

---

### Post by vocx on 2017-07-22
> **Googleness said:**
> Thanks you very much for your answer.

some updates,
1. I had to disable secure boot. even though the installer offer to disable it itself without manually disabling it the grub portion of the installation went badly and no bootloader was recognized.
2. proper way was to create uefi usb boot only using tool (I used rufus) and then boot in uefi mode. On partition section of the installer I created 650 MB efi partition and then used rest of the disk for / path.
3. to boot the usb I used e to edit the option and the boot menu and added "nomodeset" to avoid random errors or black screen issues. after the installation completed no problems were encountered and I've installed the proprietary nvidia drivers - no problems at all.
4. Switched to gnome (my proffered environment) and tested, nVidia is not playing nice with wayland so I use the non wayland one.

overall everything worked smoothly only hickup was that I needed to run chown on the second ssd drive so I could use it but steam managed to install a game on that drive so works great.

Advancing as I go I think the only issue will be currently to identify the analog video adapter drivers, but that is a project for another time.
Ha, I find it funny you didn't reference a specific part of my post, ha!

Anyways, 1,2, I haven't installed in UEFI mode ever because my computer came setup with legacy BIOS, so I just did a regular installation. I dread the day I will have to mess with those EFI partitions and stuff.
3. Yeah, "nomodeset" seems to solve issues
4. Did you install the most recent Ubuntu? Again, no experience with Wayland. Good ol Unity in 16.04 works nicely.

Yeah, you mentioned that you wanted to put your steam games in the other partition. I don't use steam so I have no idea about that. But I'm glad it works for you.

Yes, that analogue video adapter to digitize VHS, I have not even seen one in my life. I honestly feel you will have problems finding a suitable driver. I feel photographic and video hardware, especially if it's old, tends to only work in Windows. I don't blame Linux on this. I feel that when the device was launched, they only thought about the Windows users so they never released drivers for Linux. So good luck.

---

### Post by oldfred on 2017-07-22
Even if you created an ESP - efi system partition on drive you installed Ubuntu into, it normally installs /EFI/ubuntu into drive seen as sda, or usually the Windows drive's ESP. 

I like to copy /EFI/ubuntu from sda to my sdb more as a backup as fstab has the UUID of the ESP it installs into & will use for updates. New installs set permissions via fstab so you cannot see it from your install, or normally you then have to use live installer to copy files.

---

### Post by drsxr on 2017-08-18
Well, this is a great thread and instead of creating a new one, since my questions are similar, I will post my setup:
   
  Asus X99 E 10g WS
  I7 6850k
  Nvidia 1080Ti (Geforce GTX FTW edition)
  64 GB Corsair vengeance 2666 DDR4
  1 Tb Samsung 960 Evo (Main Drive, windows 10 loaded, 930 GB free currently)
  8 TB Seagate Barracuda Drive in NTFS
   
  So, I’m having the usual existential crisis of how best to configure the system with the two drives for dual boot.  Win 10 is for general computing, Ubuntu 16.04LTS is for devops and statistical computing: R and python with tensorflow– hence the 8Tb drive to hold gobs of data & 64 GB ram.  Sticking with LTS versions as I’m green in Linux. 
   
  My thoughts are to partition 100GB on the SSD as EXT4 for Ubuntu, 25GB for root & 75GB for programs, not data. 
   
  I considered a 4GB swap partition  on the SSD vs a 256 GB swap on the Hard drive.  I could see multiple virtual machines running in the same instance in the future, and I certainly have the space.
   
  The other option is to just install linux on the HD and run it purely there.  Its not unreasonable, although some of the larger algorithms I am going to be running on the GPU will take a hit.
   
  Any opinions?  What is an optimal configuration from someone who has done it before?

---

### Post by drsxr on 2017-08-18
I'll answer my own question after reviewing the valuable document by oldfred on UEFI installs:
1.  Going to install root to SSD after using windows disk tool to shrink partition to 100GB.
2.  Allocating 25GB to root.   
3.  64BG HDD swap partition.   /home on HDD.
4.   disabled fast boot in windows and UEFI

Thank you very much for all the info here.  Valuable stuff.  I'll be back when I screw something up.

---

