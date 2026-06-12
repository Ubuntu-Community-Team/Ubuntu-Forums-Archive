---
title: "Installing Xenial 16.04.X on MSI GF72"
date: 2018-04-16
forum: Installation &amp; Upgrades
---

### Post by casimirbaltasar on 2018-04-16
Hi, 
so I'm getting really frustrated and need some help. 
I had another [Thread ]("https://askubuntu.com/questions/1024109/ubuntu-xenial-16-04-02-command-lspci-lshw-system-wont-respond-cant-shutdown-r")open but I couldn't solve the problem.
I recently acquired [this new notebook]("https://aio.lv/en/computers/notebooks-ultrabooks/msi-gaming-gf72-7re-28ghz-i7-7700hq-173-1920-x-1080pixels-black-notebook:450360") and in order to use ROS Kinetic, I need to install Ubuntu Xenial 16.04 LTS.
It came with FreeDos, which I had never seen before. I haven't tried installing Windows, I wanted to instantly work on
Ubuntu. I tired the latest version, which always froze in either "Try Ubuntu" & "install". 
The Version 16.04.02 worked for a time, then I got the problem stated in my thread. 
Now I tried the Version 16.04.01 but I can't connect to the WLAN... 
I'm pretty desperate...

---

### Post by oldfred on 2018-04-16
MSI has several different models.It looks like yours has nVidia but types of drive(s) and configuration make a difference.
You need at least nomodeset boot parameter and probably additional boot parameter(s).

If new system, it probably is UEFI, but FreeDos is the way they sell without any operating system or just super basic DOS which was before Windows even existed. Microsoft sold DOS and FreeDos is now a version, but not from Microsoft. 

FreeDos may be on a MBR drive, but UEFI uses gpt.
I would backup your FreeDos partition, convert drive to gpt and install in UEFI boot mode. But some like the now 35 year old BIOS/MBR configuration as well known but UEFI is now 5 years old on PCs.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
Issues are often common across similar models of same Brand.

       MSi GT72VR-6RE Dominator Pro - some settings required
[https://ubuntuforums.org/showthread.php?t=2365997](https://ubuntuforums.org/showthread.php?t=2365997)
Failing to Boot Ubuntu 16.10 in MSI GP72
[http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72](http://askubuntu.com/questions/838212/failing-to-boot-ubuntu-16-10-in-msi-gp72)
[SOLVED] MSI GT72S 6QE - Freezes on boot unless acpi=off is used
[http://ubuntuforums.org/showthread.php?t=2303544](http://ubuntuforums.org/showthread.php?t=2303544)
MSI GS60 2QE 2xSSD RAID 0 + 1TB HDD dual boot w8.1/w10 problem 
[http://ubuntuforums.org/showthread.php?t=2297815](http://ubuntuforums.org/showthread.php?t=2297815)
MSI PX60 2qd 034us Haswell & Optimus libata.force=noncq for SSD hangup
[URL="http://ubuntuforums.org/showthread.php?t=2296878"]http://ubuntuforums.org/showthread.php?t=2296878
[/URL]
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
[URL="http://ubuntuforums.org/showthread.php?t=2296878"]
[/URL]

---

### Post by casimirbaltasar on 2018-04-17
Well ever since I ran the first try of installing the system, I clicked the option to delete the rest of my Drive.
So I guess the FreeDos is gone. 
So what I've been looking through so far:
My Notebook supports Hyperthreading, which i checked by issuing the command "lscpu" 
and it says 
"Thread per Core: 2"
I stumbled upon this thread:
[https://lists.debian.org/debian-devel/2017/06/msg00308.html](https://lists.debian.org/debian-devel/2017/06/msg00308.html)

Where it says I should update the microcode of my processor.
It's hard to figure out where to get it, which one and how to install it so it is supported for Ubuntu 16.04
I have this link open: 
[https://packages.ubuntu.com/de/xenial/intel-microcode](https://packages.ubuntu.com/de/xenial/intel-microcode)
or this one: EDIT: Ok these are the same.
[https://downloadcenter.intel.com/download/27591/Linux-Processor-Microcode-Data-File?product=97185](https://downloadcenter.intel.com/download/27591/Linux-Processor-Microcode-Data-File?product=97185)

Any advice?

---

### Post by casimirbaltasar on 2018-04-17
So I used the latest ISO Image Ubuntu Xenial 16.04.4 ,
created a bootable Disc with Rufus for GTP in UEFI mode and
deactivated Hyperthreading. System freezes.

---

### Post by oldfred on 2018-04-17
Do not mess with hyperthreading. But often some settings in UEFI are required.
With Linux almost all the drivers are included.
I have both Haswell & Skylake systems and they both have just worked. Issues you refer to is a year old, so not relevant. But since then many updates to both UEFI and operating systems because of the operating system issues for all types, AMD, Intel, IBM mainframe, etc.
Have you updated UEFI from MSI?

But your system need several boot parameters as posted above.

How you create disk does not matter, how you boot that disk does matter as how you boot USB flash drive live installer is then how it installs.
You want to boot in UEFI mode.
You should get grub menu and then must add the boot parameters you need.

This user with MSI, just got it working.
[https://ubuntuforums.org/showthread.php?t=2389372](https://ubuntuforums.org/showthread.php?t=2389372)

---

### Post by casimirbaltasar on 2018-04-17
Thanks alot for all the help, I just made it work:
What I did:
Disabled: CPU Hyperthreading, Intel SPeedStep, Fastboot, Attempt Secure Boot

Boot mode select: UEFI

replaced the boot parameter "quiet splash" with "nomodeset"


I did disable Hyperthreading though, not sure if I should enable it again?
I haven't updated my BIOS or UEFI from MSI yet, I'm currently at this page: 
[https://www.msi.com/files/pdf/How_to_update_bios_en.pdf](https://www.msi.com/files/pdf/How_to_update_bios_en.pdf)
Which i don't really understand. 
So I guess that's gonna be the next steps & I also want to update the microcode.
Any helps on those 2 issues (and maybe hyperthreading)?
Thanks alot for your help.

---

### Post by oldfred on 2018-04-17
Looks like your UEFI is similar to my motherboard.
I have 3 ways to update, one is from within Windows and I do not have Windows.
I could create a DOS bootable flash drive and include the executable file & update file on it.

But I download correct UEFI update file, extract it (if needed, some are not compressed) and copy it into my ESP - efi system partition. UEFI can only read FAT32 formatted partitions. I could reformat a flash drive as FAT32 and use it also. And then from within UEFI, I can drill down to where I saved extracted update file and run the update.

Note that update to UEFI, resets most UEFI settings to defaults. With BIOS all settings were reset.
So I keep a list of changes, my Asus Haswell UEFI gives me a change list when I change settings & save them. With my old BIOS I had to take photos, but new UEFI lets me take screenshots and save (again only to FAT32 or part of reason I like larger ESP).

My Gigabyte Skylake system is not as convenient. The UEFI update is on a almost hidden down arrow at bottom of save/exit UEFI screen. Then it shows EZ update option for UEFI.

---

### Post by QIII on 2018-04-17
I would re-enable hyperthreading.

All you have done there is to halve your expensive CPU's capabilities.

I have used all manner of CPUs and hyperthreading has never been an issue.

---

