---
title: "Installing Ubuntu help needed"
date: 2015-08-02
forum: Installation &amp; Upgrades
---

### Post by michael14 on 2015-08-02
First off here is my computer specs so if you think its incompatible you could tell me before i do the installation: Gateway NE56R41u with Intel Pentium b960 with Intel hd graphics (I believe its 2nd gen intel), 4GB DDR3 sdRAM, 500GB hdd, realtek LAN Wireless, realtek audio. 

Ok so my question is this, How do i partition my HDD so i can keep windows 8.0 yet dual boot with ubuntu? I heard of the boot loader called Grub which i wouldn't like to use i would prefer to use the windows select operating system thing if possible but i wouldn't any problem with Grub. I know you give option to keep windows and dual boot but if i were to use that installation method How would i remove ubuntu if i were to ever decide on doing so in the future?

The only reaon i am thinking of installing ubuntu is because this computer is not at all compatible with windows 10.. I installed it and it caused a non-bootable machine i had to dig up my factory defaults flash drive and reinstall windows 8..

---

### Post by TheFu on 2015-08-02
> **michael14 said:**
> First off here is my computer specs so if you think its incompatible you could tell me before i do the installation: Gateway NE56R41u with Intel Pentium b960 with Intel hd graphics (I believe its 2nd gen intel), 4GB DDR3 sdRAM, 500GB hdd, realtek LAN Wireless, realtek audio. 

Ok so my question is this, How do i partition my HDD so i can keep windows 8.0 yet dual boot with ubuntu? I heard of the boot loader called Grub which i wouldn't like to use i would prefer to use the windows select operating system thing if possible but i wouldn't any problem with Grub. I know you give option to keep windows and dual boot but if i were to use that installation method How would i remove ubuntu if i were to ever decide on doing so in the future?

The only reaon i am thinking of installing ubuntu is because this computer is not at all compatible with windows 10.. I installed it and it caused a non-bootable machine i had to dig up my factory defaults flash drive and reinstall windows 8..

Don't know how incompatible the gateway is. Sometimes the really low-end systems from different vendors take shortcuts that barely work with Windows. Since you just reloaded the "other" OS, your risk of trying Linux is minimal.
The best thing to do would be to make either a liveCD or boot flash drive with whatever Linux OS you want and try it out on your hardware. Sure, it will be a little slower, but at least you can check the video, audio, mouse, touchpad,networking and see how well those all work with ZERO risk to your current setup.
If that all goes well, you can capture and post some data back here to get more detailed help.  The main things we need to advise is the output from something called **boot-info**.   [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

You don't HAVE to use grub, but you cannot use the Windows boot loader. It doesn't work with non-Windows OSes.  Grub is the easiest to use since it is built-in. There are other boot managers and you are free to use those, but very few people will using anything other than grub. That means you won't find much help here for anything else and the official documentation is for grub.

How to remove Linux?  You won't want to do that.  Soon you'll be asking how to purge Windows. ;)  Since Linux likes to have 2-5 partitions, when you want to remove it, just purge those partitions of data (delete them). Simple.  Then you just tell Windows to reinstall its boot loader - it will do this from time to time anyway. The last 2 yrs I've had to reinstall grub after MSFT wiped it duing their monthly patching about 4 times. How rude!

Partitioning.  The answer is "it depends."
* do you want encryption?
* do you want instant snapshots?
* how advanced of a user are you? Do you want LVM?
* how much storage will be dedicated to Linux?  10G, 50G, 2TB?  How to best partition is different for those choices.
* which partitioning method is used?  MBR or GPT?

Make sense? The answers to those questions will really help.

Oh ... and does your system use UEFI to boot or does it use BIOS still?

---

### Post by yancek on 2015-08-02
A default windows operating system is incapable of booting other systems so, as indicated above, you either need to use the Linux bootloader which can do this or get some third party software for windows.

You create separate partitions for Ubuntu or any other system you might want to try.  You can do this either from windows or during the install of Ubuntu and you need to format the partitions as the filesystem types for windows won't work with an installed Linux system.  If you no longer want Ubuntu, you select and format its partitions as ntfs.

You have several options and one is as suggested to use a Live DVD or flash drive with Ubuntu.  You could also install virtual software such as virtual box on windows and run Ubuntu in it.  Try reading the detailed tutorial below which has excellent information for beginners on installing Linux with windows as well as a lot of other useful information.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by michael14 on 2015-08-02
> **TheFu said:**
> Don't know how incompatible the gateway is. Sometimes the really low-end systems from different vendors take shortcuts that barely work with Windows. Since you just reloaded the "other" OS, your risk of trying Linux is minimal.
The best thing to do would be to make either a liveCD or boot flash drive with whatever Linux OS you want and try it out on your hardware. Sure, it will be a little slower, but at least you can check the video, audio, mouse, touchpad,networking and see how well those all work with ZERO risk to your current setup.
If that all goes well, you can capture and post some data back here to get more detailed help.  The main things we need to advise is the output from something called **boot-info**.   [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

You don't HAVE to use grub, but you cannot use the Windows boot loader. It doesn't work with non-Windows OSes.  Grub is the easiest to use since it is built-in. There are other boot managers and you are free to use those, but very few people will using anything other than grub. That means you won't find much help here for anything else and the official documentation is for grub.

How to remove Linux?  You won't want to do that.  Soon you'll be asking how to purge Windows. ;)  Since Linux likes to have 2-5 partitions, when you want to remove it, just purge those partitions of data (delete them). Simple.  Then you just tell Windows to reinstall its boot loader - it will do this from time to time anyway. The last 2 yrs I've had to reinstall grub after MSFT wiped it duing their monthly patching about 4 times. How rude!

Partitioning.  The answer is "it depends."
* do you want encryption?
* do you want instant snapshots?
* how advanced of a user are you? Do you want LVM?
* how much storage will be dedicated to Linux?  10G, 50G, 2TB?  How to best partition is different for those choices.
* which partitioning method is used?  MBR or GPT?

Make sense? The answers to those questions will really help.

Oh ... and does your system use UEFI to boot or does it use BIOS still?

I've used ubuntu back when ubuntu 10.10 was the latest but it wasn't on this laptop.. I took your advice and booted from a live USB (btw could i install software on the live usb and use it without it effecting my regular HDD perhaps?) on the live USB everything ran fast! I went to the ubuntu device drivers program and it said something about intel hd graphics and under it a check box about don't use this software.. I like linux and yes my system does use UEFI.

---

### Post by TheFu on 2015-08-02
> **TheFu said:**
> 
 The answers to those questions will really help.

????

---

### Post by sudodus on 2015-08-02
Yes it is possible (to install with encryption to a USB drive).

And it is easier to help if you answer the questions we ask :-)

Install almost like you would do (into an internal drive), but into the pendrive. It is easier, if you remove the internal drive, otherwise you must use ***Something else*** at the partitioning window and ***point the bootloader into the pendrive***. Otherwise it will be installed into the internal drive /dev/sda.

There are complications in UEFI mode, and you may need a special installation, or you can use a ***persistent live*** system. An installed system may be slower than a live system if the USB pendrive is slow. A fast USB 3 pendrive makes things faster also via USB 2 ports.

See this link and links from it for more details

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by grahammechanical on 2015-08-02
An alternative is to have 2 hard disks. One with Windows and one with Ubuntu. Then you can either boot from the Ubuntu drive and get a Grub boot menu and select either Ubuntu or Windows, or boot from the Windows drive. You would make the switch from the UEFI boot system. Then, if and when you wish to remove Ubuntu just boot from the windows drive and delete the partitions in the Ubuntu drive.

When we run a Live session whether from DVD disc or USB memory stick everything is loaded into RAM. Yes, we can install drivers and software but it will only be installed in RAM. The other way of doing it would be to install Ubuntu to a USB sitck with persistence and depending on the size of the USB stick we may get from 1GB to 4GB space to hold applications and data. Ubuntu installed with persistence on a USB stick would be viewed as an external USB drive by the UEFI. Just make sure that Grub is installed to the USB stick and not the hard drive.

Additional Drivers may be showing you something called a microcode driver. Is it? It is not activated by default. It is for the CPU and not the video adapter. It is a way of changing the working of the CPU without flashing the BIOS/UEFI chip. Activate the driver and it is loaded as part of the loading of Linux. It is our choice.

Regards.

---

### Post by oldfred on 2015-08-02
With UEFI there is no conflict of having two or more boot loaders. The all create different folders in the ESP- efi system partition. And UEFI should offer its own boot menu so you can choose. If you set grub/ubuntu entry as default then you can also boot Windows from grub menu. You can also add grub/ubuntu to Windows BCD which lets you boot Ubuntu from Windows.

With old BIOS only one boot loader could be in MBR and controlled booting.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

It is important to turn off Windows fast startup which is really just hibernation. And if UEFI has a fast boot setting best to turn that off. My Asus Motherboard has different fast boot settings for cold boot or power on and warm boot or a reboot. So I set fast boot off for cold boot, and a 3 second delay on warm boot, so I could still get into UEFI. Some systems seem to only offer getting into UEFI from Windows and if Windows does not work, you cannot get into UEFI to boot repair flash drive.

Use Windows to shrink Windows NTFS partition to make space for Ubuntu. And reboot immediately so it can run chkdsk and repair itself. Do not use Windows to make new partitions with possible exception of a NTFS data partition to use for data you may want to share. Best not to write from Linux into Windows system partition.
 
Default installs create just / (root) and swap. If you want separate /home you have to use Something Else install option but then have to create, format & assign /, /home, swap to each partition as your create it in installer.

One or two others with Gateways have posted & I believe they have very limited UEFI. Best to make sure you have downloaded the latest version of UEFI from Gateway.

---

### Post by michael14 on 2015-08-02
> **TheFu said:**
> 

Partitioning.  The answer is "it depends."
* do you want encryption?
* do you want instant snapshots?
* how advanced of a user are you? Do you want LVM?
* how much storage will be dedicated to Linux?  10G, 50G, 2TB?  How to best partition is different for those choices.
* which partitioning method is used?  MBR or GPT?

Make sense? The answers to those questions will really help.

Oh ... and does your system use UEFI to boot or does it use BIOS still?

Here is the answers, Yes i do want encryption. 
I don't know what snapshots is so I'm just going to think yes?
I'd say about an about sightly above average PC user, what is LVM?
My Harddrive is 500GB so i'd give Ubuntu 100GB
I don't know which partition method is used.. 
<><><><><><><>

---

### Post by michael14 on 2015-08-02
> **oldfred said:**
> 
One or two others with Gateways have posted & I believe they have very limited UEFI. Best to make sure you have downloaded the latest version of UEFI from Gateway.

Yeah its kind of limited, I do have the latest for my computer..

---

### Post by sudodus on 2015-08-02
You want encryption. Then live or persistent live systems are no alternative.

I suggest that you use ***LVM with encryption (encrypted disk)***, which is an option at the installer's partitioning window. To get that into an external drive, I suggest that you remove the internal drive while installing.

But you must find out if you use BIOS or UEFI mode. One way to do it is to run the [Boot Repair](https://help.ubuntu.com/community/Boot-Repair) system from CD or USB. Do ***not*** repair. ***Only run the boot-info script***, let it upload the boot-info data, and post a link to it.

---

### Post by oldfred on 2015-08-02
Do not use default full drive with encryption install option. That is a full drive install or it erases everything on drive. You can manually do it but I do not know details.
Best to always have full backup of your current install and all your data.

Another encryption option is encrypted /home which is where you normally have your data. Or just another encrypted partition, but that would not be shareable with Windows.

---

### Post by TheFu on 2015-08-03
> **michael14 said:**
> Here is the answers, Yes i do want encryption. 
I don't know what snapshots is so I'm just going to think yes?
I'd say about an about sightly above average PC user, what is LVM?
My Harddrive is 500GB so i'd give Ubuntu 100GB
I don't know which partition method is used.. 
<><><><><><><>

There are multiple reasons for encryption. Each with trade-offs. If you are just trying to keep a little brother off the system, do whatever and don't worry. If you are afraid of the FSB - you aren't ready for that yet. OpSec is hard.

LVM makes all sorts of things easier - but only if you understand it.  Whole drive encryption is much easier with LVM.  If you don't understand LVM - it is a good way to get some data loss.

If you use LVM and/or encryption, then you need to have fantastic backups.  When bad things happen with those 2 things involved, often only a backup that can be restored is the only solution.  Think for a second - how do you recover data from a disk when the keys are gone and critical sectors of the disk are destroyed physically?  Either you have a backup or you are screwed.

The **boot-info** output requested above would be REALLY, REALLY helpful.

---

