---
title: "New bare metal  64 bit Install failed."
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by Billy Greenacre on 2012-05-14
I attempted to install a complete Ubuntu 12.04LTS on my new machine and it failed. I have downloaded 12.04lts in both 32 bit and 64 bit forms and neither one will work with my new box. I am not listing the new machine's innards to brag, I am seeking a solution to the installation problem. I am desperate to get this expensive monster up and running. It has the following bits and pieces inside:
 
Intel Z77 motherboard
Intel i5 3570k boxed cpu
3.4 GHz clockspeed 6MB L3 cache
2 - DDR3 1600Mhz 16GB RAM
2 - EVGA GTX 560 Ti 1GB SC
1 GB DDR5 WIT Boost HDMI/DVI support
1 terabyte, 7200 rpm ATA drive w/32 MB buffer

I have made repeated attempts to install Ubuntu on this machine. The first attempt, 64 bit disc image on a thumb drive, ended in failure because I did not have the correct kind of cable for my monitor. The second ended for reasons I still do not understand, but it came back and said that there had been an installer error and that it was sending a bug report to Canonical. The third attempt, 32 bit 11.04  via CD failed. It would not  allow me to partition the drive and then stopped once it had appeared to have installed, but was asking me for a confirmation of something, but did not enable the forward button. I tried installing 32 bit 12.04 via USB drive, but pretty much the same thing happened. When I tried to install 64 bit 12.04 via USB (a new disc image on a brand new thumb drive) it would not even boot. I double checked the boot sequence. It is set to check the USB ports first, then the DVDR/CDR second, and then the built-in hard disk. I tried the 64 bit 12.04 version on yet another thumb drive. It refused to even boot. I tried 32 bit 12.04 on a thumb drive, it would boot but only go so far in the installation process before coming to a complete insurmountable halt.
 
I now have two questions. :(
 
Is there a way to find out about the report on the installer error from my machine to Canonical? At least then I could possibly discover exactly which piece of hardware in my new box that Ubuntu does not like.

Does any Ubuntu desktop package work with a terabyte drive? I suspect that it may well be the problem. Does anyone want to suggest that I try install the server side software on this machine?

---

### Post by oldfred on 2012-05-14
You have to be the second or third Z77 board user posting with major issues. One user gave up totally, not positive if the others resolved with UEFI or BIOS. I have not done it, but use gpt partitioning with BIOS and hope to have a new system soon, so I have saved some links & info.

The issues you have are the new board is the new UEFI which also can boot in the old BIOS mode. Are you ever thinking of adding Windows on this drive? That complicates it a lot.

Ubuntu will install in UEFI or BIOS mode with a drive with the new gpt partitioning. Windows will only boot in UEFI mode with gpt partitioning.

Those systems that have worked with UEFI have partitioned in advance and from UEFI boot loader choose either UEFI mode on liveCD/USB to install in UEFI mode or choose BIOS mode to install in BIOS mode.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
If gpt(not MBR) partitioning include these first - all partitions with gpt are primary
    250 MB efi FAT32
    1 MB bios_grub  no format 
Ubuntu partitions - smaller root only where hard drive space is limited
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

If you're using UEFI mode to boot, you don't need a BIOS Boot Partition with gpt partitions (only for BIOS), but you do need an EFI System Partition (ESP). This is entirely different; it should be a 200-300 MiB FAT32 partition that's flagged as an ESP and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same). In gdisk, you'd give it a type code of EF00.
An EFI System Partition EF00 (~100 to -256MiB, FAT32) for UEFI, a BIOS Boot Partition EF02 (~1MiB, no filesystem) for BIOS, and whatever partitions you want for Linux. You must set the partition type codes correctly, but how you do this depends on the utility you use to create them. Also, you should be sure to create a GUID Partition Table (GPT) on the disk, not a Master Boot Record (MBR) partition table. In BIOS mode, Ubuntu's installer defaults to creating MBR partitions, at least on sub-1TB disks, so you may need to use another utility to do the partitioning. You do not need both but it does not hurt as both are small, and then you can configure easily to boot with either UEFI or BIOS. You can boot via bios AND efi (after setting up your efi boot entry using efibootmgr or via efi shell and running the efi binary)

Grub2 efi info ArchLinux - Arch but grub2 is grub2 with maybe minor differences by distribution
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)
[http://www.rodsbooks.com/efi-bootloaders/](http://www.rodsbooks.com/efi-bootloaders/)

[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell]("https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell")
Recompiling GRUB not required with newest versions of grub.
Creating efi partition & folders in advance works.

GUIDE: (U)EFI installation Also full install post *52 superfreak
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
Examples that worked, format in advanced with gparted, gpt with find efi output & demesg
[http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi](http://ubuntuforums.org/showthread.php?t=1954716&highlight=efi)
[http://ubuntuforums.org/showthread.php?t=1939094](http://ubuntuforums.org/showthread.php?t=1939094)

It does work.
Intel Preview: Z77 Motherboards Run Well With Linux
[http://www.phoronix.com/scan.php?page=article&item=intel_z77_chipset&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_z77_chipset&num=1)

Edit - a user who has Z77 and used BIOS mode.
[http://ubuntuforums.org/showthread.php?t=1979605](http://ubuntuforums.org/showthread.php?t=1979605)

---

### Post by Billy Greenacre on 2012-05-17
Thank you for responding, oldfred. FYI, I bought this machine with the intention of installing Ubuntu on it at the jump without ever using windows or a windows based program. If MacOSX would run on it I would be tempted. I am still scratching my head over some of the terms you used in your post.  I see now that I have bitten off a wee bit more than I can chew. It is not a problem. I'll just sprout some more teeth. :)

---

### Post by n2uad on 2012-05-17
Hi,

I just installed on a new DIY system similar to yours. The install went fine. 
Intel H77 Motherboard
256GB SSD drive (OS here)
2TB hard drive
DVD drive
etc....

I could not use the gui regular 64 bit install. Had to use the alternative CD install. The display was blank. Hooked up to a HDMI display. As a test Vista did the same thing. So don't know if the MoBo has a problem or not w/HDMI. Or Ubuntu has a HDMI issue.
With the system running there is no output on HDMI - only DVI. 

I think the Z77 boards only have HDMI?

Other than this issue the install went fine. So my advice is to try the alternative 64bit CD.
I think Phoronix.com used a Intel Z77 board and claimed it was working good.

---

### Post by Billy Greenacre on 2012-05-19
Mine is DVI on the graphics card, SVGA on the motherboard. The port on the motherboard as disabled when the machine was assembled.  I had to go buy a SVGA to DVI adaptrr to get my monitor to talk to th machine.  It also has a IEEE1394 (firewire) port available , but I do not if it works or not. What is the alternative CD install? Having read numerous articles on installing Ubuntu  on a 64 bit machine, have nearly concluded that it would be best to install Windows first, then download the Windows installer for Ubuntu.

---

### Post by darkod on 2012-05-19
The Alternate CD is a different ISO. There are versions for 32bit and 64bit the same as with the standard (live) cd.

It installs the same ubuntu system, the difference is that you can't run the alternate in live mode (from the cd), and the installer is text based, not GUI (like the win XP installer if you have ever installed XP).

Also, the support for raid and LVM is better on the alternate cd but that's besides the point in this thread.

I guess because the installer is text based and not GUI, it has a greater chance to work when there are video problems during the install.

You can get any of the ISOs here:
[http://releases.ubuntu.com/precise/](http://releases.ubuntu.com/precise/)

---

### Post by Billy Greenacre on 2012-05-19
Thank you very much, Darkod. I will give one of them a try.

---

### Post by Billy Greenacre on 2012-05-19
Okay, I have downloaded the alternate CD version of the 64 bit installer. Can I use my 32 bit laptop to make a CD or bootable USB drive?

---

### Post by darkod on 2012-05-19
Yes, you don't need 64bit machine just to burn the ISO.

---

### Post by Billy Greenacre on 2012-05-19
Okay. I will give it a try late tonight or early tomorrow morning. I prefer quiet whenever I am in the terminal. I can't think clearly when there is a lot of noise in the background.

---

### Post by darkod on 2012-05-19
The text installer is hardly a terminal, just that it's not a fancy GUI.

However, it's best that you do it when ever you feel it's best for you, of course. :)

---

### Post by Billy Greenacre on 2012-05-24
Okay, I have good news and bad news. The good news is that the alternate install cd image worked perfectly. I made an image, installing it on an USB thumb drive. It booted from the thumb drive and installed Ubuntu 10.10,. This version of Ubuntu ran fine, but I received a notice that it was no longer supported by Canonical. It advised me to upgrade. 

After I began upgrading, it stopped at  11.04.  After the upgrade, it refused to boot from the hard disk.  Having decided that I would have to start over from scratch, I put the USB drive back into a port and rebooted. The operating system came up that time. I am still uncertain of what I did to get the bloody thing started.  I can tell you that the software update tool does not see an available update for that machine. I am not even certain that it loaded a 64 bit version of Ubuntu on the machine. 

Now I am stuck. I cannot upgrade to 12.04 and I cannot boot from USB. At least, I don't think I can. I have been afraid to shut the machine down knowing that it would be a problem to restart.

---

### Post by darkod on 2012-05-24
And why did you install 10.10? Can't you get the latest 12.04 LTS image and create the usb stick with that?

After that do the same install as you did and it should work out fine. If there are any issues they can probably be resolved.

There is no point installing 10.10 now and doing three upgrades in a row to get to 12.04.

---

### Post by oldfred on 2012-05-24
You may have been booting thru grub, but needed nomodeset to get the nVidia to let you boot. I have had to use nomodeset on every CD, USB or first install boot until I get nVidia driver installed. Some very new or very old systems also need other boot parameters.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Billy Greenacre on 2012-05-25
Okay, software update just told me this evening that version 11.10 of Ubuntu was available. I shouted, "Oh, goody!" and  told the software update tool to go ahead and upgrade. It did, but now my computer will *not* reboot.  The system setup was set to a single monitor, so I set it to multiple monitors. Now it does not light up my screen. I will reset that to single monitor. Right after I post this message. 

System set up shows this machine to have the following:

CPUID/Microcode: 306a9/10
BIOS version E7758IMS V2.2
Build date: 04/02/2012
ME Version: 8.0.3.1427
Physical Memory: 16,384 MB
Cache Size: 1024 KB
L3 Cache: 6144 KB.
 
Intel Rapid Start Tech is disabled and I cannot start from the system monitor, so I am guessing that this is set with a jumper or a DIP switch.

---

### Post by Billy Greenacre on 2012-05-25
> **oldfred said:**
> You may have been booting thru grub, but needed nomodeset to get the nVidia to let you boot. I have had to use nomodeset on every CD, USB or first install boot until I get nVidia driver installed. Some very new or very old systems also need other boot parameters.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
 
Thanks, old fred. I'll give it a try as soon as I get the monitor communicating with the CPU again.

---

### Post by oldfred on 2012-05-26
The very first time I had this happen I was installing from a USB. The install started & all of a sudden my monitor just turned off/went to sleep. But I could see USB flashing like it still was booting. It took me a while to learn to use nomodeset, but now I have it everywhere until I get nVidia installed.

---

### Post by Billy Greenacre on 2012-05-26
Okay, guys. Here is what I wound up doing. I could not, no matter how I tried it, get this machine to boot from the CD image stored on the USB stick. The graphics setup is for multiple monitors so that made it necessary for me to change from the DVI port on the graphics card back to the SVGA port on the motherboard.  I suspect it will be necessary for me to buy another cable before this issue will be resolved. 

To get at the System Menu on this machine, you hold down the F11 key while pushing the start button (part of the hardware) on the machine. This will bring up the system setup menu.  As I said at the start of this message, I tried every combination that I could think of to get the machine to boot. It flatly refused. I could not get it to boot from the USB port nor from any of the built in drives. Finally,  out of desperation,  I told the system menu to** disable all of the drives but the CD image on the USB drive.** That worked. The computer booted from the CD image on the USB stick with no trouble at all. 
 
I told it to install Ubuntu. This time the list of things it wanted me to do was much longer than the last time I installed from USB, and it did not jump into graphics mode the way it did the last time I installed Ubuntu on this machine. Once the install completed, I had to go back into the setup menu and re-enable all of the built-in drives. After I saved those settings and rebooted the machine, it came up without a hitch--in Ubuntu 12.04 instead of Ubuntu 10.10. This was a great surprise to me and it made mey very happy. 

Update Manager immediately informed me that there were updates available, so I let it do its thing. It wanted to reboot at the end of that install so I told it to go ahead. The machine rebooted without a hitch. I checked to see if there were any additional updates available, and there were.  Update Manager once again went to work and for the third time, the machine has rebooted without a hitch. 

I am not quite ready to declare this problem solved. There are still issues with the graphics cards to settle, and I still want to download MyPaint, The GIMP, and Blender. I will leave this thread open until I have downloaded and installed that software on this machine.  

For now though, I am very relieved and happy.

---

### Post by oldfred on 2012-05-26
Did you install in UEFI or BIOS mode. Is drive formated MBR(msdos) or gpt(GUID)?

For others with similar new systems it may be good to document what you did to install. (In addition to the hoops you had to leap thru).

---

### Post by Billy Greenacre on 2012-05-26
I enabled something called EFI, I think. All it seemed to do is to get in the way when the machine tried to reboot, so I disabled it. I neglected to mention that, didn't I? It is very hard to remember everything you did when you are in the throes of getting a recalcitrant machine to boot. 

I have since installed all of the major graphics package available for Ubuntu. The GIMP, Krita, MyPaimt, Inkscape, and Blender. All of the appear to run fine--better than fine. They are much faster on this new machine than they were on my old machine. I do have a couple of remaining kinks to straighten out. One is getting the two graphics cards working. The other is that the machine will sometimes freeze during a series of downloads. I found this out once I started rebuilding my e-library by downloading my favorite books from Project Gutenberg. 
 
The machine suddenly freezes and no matter how long I wait, it does not recover. I tried everything I could think of or make up to get it to move on, but it stayed hard frozen, ignoring all inputs from both mouse and keyboard. I gritted my teeth and did a hard shutdown. It rebooted without a problem and I did not lose anything. It has done it twice since that time. 

I am also getting an error message from Ubuntu 12.04 that says there has been some sort of internal error. I get the same message from time to time on this laptop.  I read somewhere that this is a well known problem and that Canonical is already working  on it. 
 
The first time I saw it was on my laptop. It suggested that it would report the bug, but then asked me for my password. Thinking that someone had slipped a Trojan Horse into mys system, I canceled it rather than giving it my password.

Still not quite certain that I have everything right, yet.

---

### Post by Billy Greenacre on 2012-06-05
Having read numerous reports about the system error message and unexpected freezes, I am convinced that the installation is not the cause. They are separate issues.

---

