---
title: "Installation Issues: No Unity, Grub Rescue, Windows 10 Gone."
date: 2016-07-10
forum: Installation &amp; Upgrades
---

### Post by arcofark on 2016-07-10
Hello,

I am installing Ubuntu on my home computer because I wish to do some scientific computing. Unfortunately, I have no experience with operating systems and I have run into many issues that I don't understand. After hours of googling, however, I learned a little bit. Even still, I will need your help to solve these problems.

First, I want to tell you about the computer I have so that you can really understand everything. 

**Hardware**
Intel Core i5-6500 3.2GHz Quad-Core Processor
Asus B150M-A D3 Micro ATX LGA1151 Motherboard
Crucial Ballistix Sport 16GB (2 x 8GB) DDR3-1600 Memory
EVGA GeForce GTX 960 4GB SuperSC ACX 2.0+ Video Card
Samsung 840 EVO 250GB 2.5" Solid State Drive
WD Blue 1TB SATA 6 Gb/s 7200 RPM 64MB Cache Hard Drive

**Windows 10 was already installed on the Samung Solid-State Hard Drive (sda)**
Now, I am attempting to install Ubuntu on the Hard Disk Drive (sdb) so that I can **dual boot**.

Now I will list some issues that seem most important to me.
1. I made a bootable USB using Rufus. I can launch Ubuntu from the bootable USB, however, I do not have *any *graphical interface. I can see a desktop and mouse. But there is no other graphical interface, I cannot access the terminal using [Alt]+[Ctrl]+[T]. I did access the terminal using [Alt]+[Ctrl]+[F2]. Here, I was able to command "startx" so that files on the desktop appeared.
2. After installing Ubuntu, I cannot boot from Windows 10. I can't load Windows 10 from either hard drive on the YUMI-BIOS screen.
3. If I boot from the solid-state hard drive (sda), I am led to a grub-rescue screen. If I boot from the hard disk drive, I am led to a grub screen.

What is the best way to go about solving these issues?

Dan

---

### Post by grahammechanical on 2016-07-10
Did you follow these guidelines?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too.

> 
[LIST]
[*]In your firmware, [disable QuickBoot/FastBoot]("http://ubuntuforums.org/showpost.php?p=12397979&postcount=9") and [Intel Smart Response Technology]("http://ubuntuforums.org/showpost.php?p=12460938&postcount=6") (SRT). If you have Windows 8, also [disable Fast Startup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"). 
[/LIST]


What install option did you choose? Alongside other operating systems? Something Else? The installer defaults to installing the Linux boot loader (Grub) into sda. Did you direct the installer to install Grub into sdb?

When you get to a Grub boot menu does an option for Windows appear?

What partitioning scheme does the hard drive have? MBR or GPT? With GPT and using the Something Else option we need to create a efi_boot partition (ESP) when installing Ubuntu in EFI mode. When installing Ubuntu in BIOS/Legacy/CSM mode we need to create a bios_boot partition. What is the situation?

Regards.

---

### Post by oldfred on 2016-07-10
You have a new advanced UEFI system with nVidia graphics.

Did you install Windows on SSD in UEFI or BIOS boot mode. With your new hardware you should have installs in UEFI mode with gpt partitioning.
And have you partitioned HDD with gpt, so you can install Ubuntu in UEFI boot mode?

You probably need nomodeset on live installer, and on actual install until you install the nVidia proprietary graphics driver from Ubuntu's repository.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Some with even newer nVidia cards, were able to install by connecting to Intel video output on motherboard and once system working install nVidia driver. But some Skylake based Intel may also need a boot parameter. I only have Intel video with 6500 chip and have had no issues.

       
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset. 
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

If you can boot into gui, post this:
sudo parted -l

If you have installed, do not run any autofix until someone has reviewed your system, it will not fix video issues:

 May be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by arcofark on 2016-07-10
Hi grahammechanical and oldfred.

Graham, this is the first time I read those guidelines. Allow me to explain what I am able to refer from the guidelines.
I have a computer that supports both BIOS and UEFI [I]because pressing [F2] during the loading screen takes me to Asus UEFI BIOS Utility.
[/I]I want to dual-boot, which requires that the boot modes match. Now, what boot mode was my original Windows 10 installed in? I don't know. I can't see Windows 10 in UEFI BIOS Utility. I would appreciate if you could tell me how I can find out. Perhaps this helps me: I installed Windows 7 first and then upgraded to Windows 10.

I did try **disabling Secure Boot **and **Fast Boot**. I disabled secure boot by deleting the PK Boot Key, following some directions online. I have the keys saved on a USB drive.

I used the installer ISO image made with the USB. Here, I believe the boot loader was installed in **sba**. To me, this makes sense to me because I no longer see Windows 10 in the Grub menu. (The Grub menu only appears when I boot from the ISO Image, grub rescue shows when I boot from **sba**.

I don't know what partitioning scheme I have. How do I find out? oldfred suggests that I have **gpt **partitioning.

oldfred, I wish I could tell you with certainty whether I do in fact have **gpt **partitioning or not, but I can't. Can you tell me how I can find out? And no, I didn't manually partition the HDD with gpt. I don't know if the installer did though. I will try setting NOMODESET, but before I do I want to make sure 100% this is relevant to my problems.

---

### Post by oldfred on 2016-07-10
This shows partitions and partitioning type.
sudo parted -l

If you installed with Windows 7, it probably is MBR.
The default install of Windows 7 from DVD is BIOS/MBR.
And Windows only boots in BIOS mode from MBR and only in UEFI mode from gpt.
You can convert a Windows 7 DVD to flash and move some files around to make it a UEFI installer but have to know to do that if you have a newer system. Microsoft assumes you are installing newer Windows on newer systems. 

You should not delete keys. Restore them, before you have major issues. If you installed Windows 7 in BIOS boo tmode, Secure boot had to be off as BIOS is not UEFI Secure boot. 

There are 3 boot modes with new UEFI systems. UEFI with Secure Boot, Standard UEFI and CSM.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Some vendors still call UEFI as BIOS so as not to confuse users, but then creates more confusion.

---

### Post by arcofark on 2016-07-10
[FONT=courier new]So I've used *sudo parted -l *and *fdisk -i *to look at the devices. I don't see any obvious indication of MBR vs GPT. Here is what I see.

fdisk -l 

Device     Boot Start      End        Sectors   Size   Id  Type
/dev/sda1 *     2048       206847     204800    100M    7  HPFS/NTFS/exFAT
/dev/sda2       206848     487473151  487266304 232.4G  7  HPFS/NTFS/exFAT 
/dev/sda3       487473152  488394751  921600    450M   27  Hidden NTFS WinRE

/dev/sdb1       2048       969919405  969917358 462.5G  7  HPFS/NTFS/exFAT 
/dev/sdb2       969920510  1953523711 983603202 469G    5  Extended
/dev/sdb5       1920141312 1953523711 33382400  15.9G  82  Linux swap / Solaris
/dev/sdb6       969920512  1920141311 950220800 453.1G 83  Linux


parted -l

For sda (the SSD),

Number Start  End   Size  Type    FileSystem Flags
1      1049kB 106MB 105MB primary ntfs       boot
1      106MB  250GB 249GB primary ntfs       
1      250GB250GB 472MB primary ntfs       diag

For sdb (The HDD),
Number Start  End    Size   Type     FileSystem Flags
1      1049kB 497GB  497GB  primary  ntfs
2      497GB  1000GB 504GB  extended 
6      497GB  983GB  487GB  logical  ext4
5      983GB  1000GB 17.1GB logical  linux-swap(v1)[/FONT]

---

### Post by oldfred on 2016-07-10
Does not look like you posted the full output from either fdisk nor parted.

Mine has about 4 lines from the top this, your will say : dos.
Disklabel type: gpt

You have MBR(msdos) since you have an extended partition. Gpt does not have extended and logical partitions.
       MBR tech details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

You can use BIOS & MBR, but it is 35 years old, well known with lots of kludges to let it work with newer systems.
With UEFI, BIOS is emulated.

       
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by arcofark on 2016-07-11
Hi oldfredi, thanks for all your help so far.

Yes, the MSDOS is what it says.

I booted Ubuntu (Try without installing) with the nomodeset option.
The first time I replaced quiet splash with nomodeset like you said. It was not able to boot all the way, I believe it said it couldn't load sba2 because it was unsafe.
The second time I added nomodeset after quiet splash. Booting was successful and I could tell that the screen looked a little grainier (Like the safe mode in Windows XP). However, I could already get to this screen before trying nomodeset so I am back to square one.

---

### Post by ubfan1 on 2016-07-11
Run in a terminal the command: lshw -C video to see what hardware and driver is being used for video.  It could be either the integrated Intel video with the i915 driver, or the Nvidia with the nouveau driver.  The best performance would be with the proprietary Nvidia driver, which you need to explicitly install.  From the Dash, find the software updater (type "up" in the search bar and it should be found), and run it.  It will update the package information, then offer you updates.  You probably should update, then run again, and click on the settings button.  in the "Ubuntu Software" tab, select the "proprietary drivers...", and if you want the copyrighted button too.  Under the "Other Software" tab, I check the partners button.   Then exit and run the software updater again, and get the updates.  Now under the settings button, click on the "additional drivers" tab.  There should be a list of Nvidia drivers, including the nouveau.  Select the proprietary, tested one, let it install, and reboot.  You should no longer need the nomodeset, and your resolution should be better.

---

### Post by yancek on 2016-07-11
> 
The first time I replaced quiet splash with nomodeset like you said. It  was not able to boot all the way, I believe it said it couldn't load  sba2 because it was unsafe.

sda2 is a windows partition.  If you get a message indicating that it is in "an unsafe" state, that means you have left windows hibernated and no Linux system will mount it or try to access it.  If you could post the total exact message it would be useful.  Actually, the best thing to do is to post a link to the output of the boot repair software which you can get frorm the last link posted above by oldfred in his initial post.

---

### Post by arcofark on 2016-07-19
Hi, I am back!

I actually got the boot-repair to run this time. Here is the link:

[http://paste2.org/65kNvhM2](http://paste2.org/65kNvhM2)

---

### Post by oldfred on 2016-07-19
I would use Boot-Repair's advanced mode and install the Windows type boot loader to sda, so you can directly boot Windows which you occasionally need as grub only boots working Windows.
And reinstall grub to sdb, and set BIOS to boot sdb directly. You can normally dual boot then from grub menu.

Even with BIOS installs, you need to have Windows 10's fast start up off. That is always on hibernation and grub will not boot it. You only can then boot from BIOS if you have Windows boot loader in sda.
       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) 
    
With nVidia, you may need nomodeset to get into gui in lower quality mode. Then install nVidia driver. Or use recovery mode, second line in grub menu to boot to command line and install nVidia driver.
       # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended  
   sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall

---

### Post by arcofark on 2016-07-20
I look in the advanced mode, but I don't see the option to install Windows-type bootloader. There is a box for "Repair Windows Boot Files" but I can't put a check mark on it.

---

### Post by oldfred on 2016-07-20
Under MBR options, can you choose sda and Windows?
If Windows is hibernated then it cannot see it to offer Windows as a boot option.

You then have to manually install a Windows type boot loader or use your Windows repair flash drive to run fixMBR command.

       sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda 

dd is also known as Data Destroyer. any typo can totally destroy system. Best to copy and be sure command is doing what you want.

---

### Post by arcofark on 2016-07-20
Hi, so the MBR options tab is inaccessible. It won't allow me to click on that tab to access options there.

So let me really make sure what you are saying is:

I should type in this command:
> [COLOR=#000000]sudo apt-get install syslinux[/COLOR]
[COLOR=#000000]sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda [/COLOR]

---

### Post by oldfred on 2016-07-20
Yes those two commands. You do not want a full install of sysLinux, just the MBR portion.

Syslinux is a Windows type boot loader that the MBR portion of it just jumps to the partition with the boot flag. That is how Windows boots.
Syslinux is the boot loader used by many Linux installers to boot in BIOS mode. But that adds Syslinux boot code to the partition with the boot flag.

---

### Post by arcofark on 2016-07-21
Hi, the second command did not do anything, so I went to check the directory. 

Did you mean:
[COLOR=#000000][I]sudo dd if=/usr/lib/syslinux/mbr/mbr.bin of=/dev/sda
I also noticed that there are several syslinux directories: syslinux, SYSLINUX, and syslinux-legacy.
[/I][/COLOR]

---

### Post by oldfred on 2016-07-21
You will not see anything, but if you run Boot-Repair it will show a syslinux boot loader in the MBR of sda.

And if in BIOS you choose to boot from sda, it should directly boot Windows. If Windows has issues f8 may get you into a Windows repair console.

---

### Post by arcofark on 2016-07-21
Hi, when I run dd it says no file or directory.

---

### Post by oldfred on 2016-07-21
I show the mbr.bin in that file path.
If you have the various syslinux folders, do you not show the mbr.bin in [COLOR=#000000][I]/usr/lib/syslinux/mbr  ?

```
fred@Z170N:~$ ls -l /usr/lib/syslinux/mbr
total 12
-rw-r--r-- 1 root root 439 Feb 24 08:32 altmbr.bin
-rw-r--r-- 1 root root 440 Feb 24 08:32 gptmbr.bin
-rw-r--r-- 1 root root 440 Feb 24 08:32 mbr.bin

```
[/I][/COLOR]

---

### Post by arcofark on 2016-07-21
Hi, 

Thank you for returning Windows to my computer! I can boot into sda and run Windows with no problem. I am also working directly on the computer now, not on an Ubuntu image.

I also installed the nvidia drivers as you said. The results are improved but some issues still remain:

Booting Issues:
I can only boot Ubuntu from BIOS.
I cannot switch boot order between sda and sdb. I only see sda available in the Boot Order menu in BIOS.
These issues above are very minor. I actually prefer that I automatically boot into Windows. I only plan on using Ubuntu for special circumstances.

Ubuntu Issues:
There isn't the familiar GUI I am familiar with Ubuntu desktops. There is a background image (purple and red) but nothing else.
I can open the terminal now with a right-click.
I cannot open the terminal with Ctrl+Alt+T.

---

### Post by oldfred on 2016-07-21
Glad Windows is now working.
I would expect UEFI/BIOS to show sdb as a bootable device in BIOS mode? Not sure then why not.
But ok, it you just want to use one time boot key like f10 or f12 to choose what to boot.

Did you install a nVidia driver? Sounds like you still have video issues.
Have you tried nomodeset? Only required until you install nVidia driver.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 
    

If you can get to terminal you can just install nVidia driver directly.
       # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended  
    
If any nVidia driver installed you must purge it first. New driver does not delete old and then you get major conflicts.
If not installed command will just return.
 sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall 

I do not know with latest versions if you automatically get nvidia-config (may now be part of settings?) and nvidia-settings?

sudo apt-get install nvidia-settings

---

### Post by arcofark on 2016-07-21
Thank you so much for your help. I needed a lot of spoon-feeding.

I followed this person's answer to get the GUI. At the moment, everything seems OK.
[http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears](http://askubuntu.com/questions/17381/unity-doesnt-load-no-launcher-no-dash-appears)

I get this error message, but I think it is trivial.
```
[SIZE=2]**[FONT=arial]snd_hda_intel 0000:00:1f.3: failed to add i915 component master (-19)[/FONT]**[/SIZE]

```
[https://ubuntuforums.org/showthread.php?t=2301908](https://ubuntuforums.org/showthread.php?t=2301908)

It makes sense since I have a video card, and the onboard one is disabled.

---

