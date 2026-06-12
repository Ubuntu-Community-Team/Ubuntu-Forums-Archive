---
title: "Can't boot from a new Ubuntu 20.04 USB drive"
date: 2020-11-24
forum: Installation &amp; Upgrades
---

### Post by pme 72 on 2020-11-24
My Bios boot based PC does not recognize a new Ubuntu 20.04 installation USB drive. I can access the files on the USB drive and I see a file named Boot with a file Grub that has a file named x86_64-efi. 

Does that mean that the drive can not be used on my PC?

---

### Post by CelticWarrior on 2020-11-24
It's possible indeed.

Some tools like Rufus, depending on the settings, either do a BIOS bootable or a UEFI bootable, not both.

---

### Post by sudodus on 2020-11-25
- Please tell us about your computer: brand name and model

- and tell us also how you created the USB boot drive: method and/or tool

Then it will be easier for us to help you.

---

### Post by pme 72 on 2020-11-27
This is not a time sensitive issue at all. Ubuntu 16.04 is my current OS and 18.04 is on another partition. 

Computer is a 2005 Compaq desktop rebuilt in 2013: 

Mother Board - ASUS M5A 78L-M LX
CPU - AMD 4100
Memory - 8 GB 
IGP - ATI Radeon HD3000

2019 - new Corsair CX430 power supply

This equipment has successfully accepted installs of Ubuntu, Xubuntu, Peppermint and multiple Virtual Box installs of Windows and assorted other Ubuntu's. Running a Live version of Ubuntu from a USB drive has never before presented any issues.  

Flash drive: ILamourCar Ubuntu  Ubuntu 20.04. Full and latest version of the Ubuntu OS 16 GB USB flash drive for desktop, laptop, PC. (Recently purchased from Amazon)
You can run Ubuntu straight from this USB, no need to install.
Minimum hard disk space: 25 GB free disk space. Minimum RAM: 4 GB RAM. Minimum processor speed: Dual Core Processor (2 GHZ). Media type: USB Flash. Language version: English. Other: VGA capable of 1024x768 screen resolution.

A message appeared briefly on screen when I first tried to run it. The message has not appeared during subsequent attempts to boot. Could the file access type have been changed at that time?  

 [IMG]https://postimg.cc/TKSk5Gx0[/IMG]

---

### Post by pme 72 on 2020-11-27
> **pme 72 said:**
> This is not a time sensitive issue at all. Ubuntu 16.04 is my current OS and 18.04 is on another partition. 

Computer is a 2005 Compaq desktop rebuilt in 2013: 

Mother Board - ASUS M5A 78L-M LX
CPU - AMD 4100
Memory - 8 GB 
IGP - ATI Radeon HD3000

2019 - new Corsair CX430 power supply

This equipment has successfully accepted installs of Ubuntu, Xubuntu, Peppermint and multiple Virtual Box installs of Windows and assorted other Ubuntu's. Running a Live version of Ubuntu from a USB drive has never before presented any issues.  

Flash drive: ILamourCar Ubuntu  Ubuntu 20.04. Full and latest version of the Ubuntu OS 16 GB USB flash drive for desktop, laptop, PC. (Recently purchased from Amazon)
You can run Ubuntu straight from this USB, no need to install.
Minimum hard disk space: 25 GB free disk space. Minimum RAM: 4 GB RAM. Minimum processor speed: Dual Core Processor (2 GHZ). Media type: USB Flash. Language version: English. Other: VGA capable of 1024x768 screen resolution.

A message appeared briefly on screen when I first tried to run it. The message has not appeared during subsequent attempts to boot. Could the file access type have been changed at that time?  

 [IMG]https://postimg.cc/TKSk5Gx0[/IMG]

[https://postimg.cc/TKSk5Gx0](https://postimg.cc/TKSk5Gx0)

---

### Post by sudodus on 2020-11-27
> **pme 72 said:**
> ...
This equipment has successfully accepted installs of Ubuntu, Xubuntu, Peppermint and multiple Virtual Box installs of Windows and assorted other Ubuntu's. Running a Live version of Ubuntu from a USB drive has never before presented any issues.  

Flash drive: ILamourCar Ubuntu  Ubuntu 20.04. Full and latest version of the Ubuntu OS 16 GB USB flash drive for desktop, laptop, PC. (Recently purchased from Amazon)
You can run Ubuntu straight from this USB, no need to install.
...

Thanks for the details.

- Please tell us also how you created the USB boot drive - which tool or method did you use?

- And can you boot another computer with this USB boot drive?

I can't say that I understand what causes the problem. And I don't understand how far the boot process works (until it fails). Maybe you can try to describe with more details how far it works, for example by removing the [boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) [FONT=Courier New]**quiet**[/FONT] and [FONT=Courier New]**splash**[/FONT], and watching the output to the screen.

- Maybe the graphics card of the old computer is not recognized by Ubuntu 20.04 LTS. If that is the problem, maybe it can work with the [boot option](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) [FONT=Courier New]**nomodeset**[/FONT].

- Maybe there is some other problem related to the graphics of standard Ubuntu. In that case it might work better with a light-weight flavour: Lubuntu, Ubuntu MATE or Xubuntu (of the same version 20.04 LTS).

---

### Post by C.S.Cameron on 2020-11-27
> **pme 72 said:**
> 
Flash drive: ILamourCar Ubuntu  Ubuntu 20.04. Full and latest version of the Ubuntu OS 16 GB USB flash drive for desktop, laptop, PC. (Recently purchased from Amazon)
**You can run Ubuntu straight from this USB, no need to install**.
 [IMG]https://postimg.cc/TKSk5Gx0[/IMG]

You can often just extract a Linux ISO to USB and run it in UEFI mode, but I have not heard of this working in BIOS mode.

Best to create a Live or Persistent USB installer drive using mkusb, Startup Disk Creator, Etcher or Rufus.

---

### Post by pme 72 on 2020-11-28
Sudodus, thank you for the reply.

I purchased the USB Boot Ubuntu 20.04 drive from Amazon, ILamourCAR Ubuntu 20.04:
 About this item:  ILamourCar Ubuntu Linux 20.04 Latest Version - 2020 16GB USB Flash Drive | English Version - Silver 

    Ubuntu 20.04. Full and latest version of the Ubuntu OS 16 GB USB flash drive for desktop, laptop, PC.
    Ubuntu, the World's Most Popular Linux, Contains a massive array of software - office software, browser, email, image editing and more.
    Simple to use: You can run Ubuntu straight from this USB, no need to install.
   Minimum hard disk space: 25 GB free disk space. Minimum RAM: 4 GB RAM. Minimum processor speed: Dual Core Processor (2 GHZ).          Media type: USB Flash. Language version: English. Other: VGA capable of 1024x768 screen resolution.

      I removed the older HDD that boots to 16.04 and enabled a newer HDD with Xubuntu 20.10. I also enabled a Radeon R7 240 GPU. With the USB drive inserted I received a similar result to the older drive. The machine did not boot from the USB, it immediately opened the Grub Menu and booted to Xubuntu 20.10. 

     I ran dmesg after the failure to boot the USB and ran it again after a subsequent boot without the drive. I have the two results side by side on a Calc spread sheet and am slowly checking for lines that do not match. 

     Almost at the end of the dmesg output of the first dmesg there is a line: [  141.819339] FAT-fs (sdg1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.

     Maybe that's why the USB is now recognized as a bunch of files, not an ISO. The ILamourCar USB is listed as sdg1. 

     When checking the BIOS Setup to verify that the USB drive was 1st priority I noticed that under Main Settings only two of 6 available slots/inputs(?) were listed as Detected, the #2 Boot Priority CD ROM and the #3 Boot Priority, the hard drive I had just enabled. The #1 Priority USB Generic USB SD Reader was listed as not Detected. 

     Later tonight or tomorrow early morning I hope to download a light-weight distribution ISO and burn it to a USB drive to verify that the USB port(s) will properly recognize the ISO file.  

     Again, this isn't any crisis. I am curious about 20.04 but 16.04 serves my needs well.

---

### Post by sudodus on 2020-11-29
While most USB pendrives work well as boot devices, some USB pendrives do not cooperate well with some computers. This might be a reason for your problems.

It is also possible that you use a tool/method, that does not work with Ubuntu 20.04 LTS. This is the reason why I ask for the tool/method that you use to burn from the iso file to the USB drive.

The following links and links from them may help you look for possible causes of the failure to boot.

[help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Why Doesn't a Bootable USB Boot](https://askubuntu.com/questions/1190764/why-doesnt-a-bootable-usb-boot/) - click on the flowcharts to get bigger pictures where the text is easier to read

[hr][/hr]
Anyway, good luck when you burn a light-weight distribution ISO and to a USB drive and try to boot :-)

---

### Post by GhX6GZMB on 2020-11-29
Just for reference: the contents of your USB drive should look like this:

---

### Post by pme 72 on 2020-11-30
Thank you ml9104, I show all those files and a couple of others. 

BIOS is not showing any available USB ports. My hard drives and DVD drive are listed but the other three ports show "Not Detected".  

To verify I downloaded CorePlus-current, a tiny, 230.6 MB, boot-able distribution and wrote it to a USB drive. The PC booted directly to GRUB, the USB was not recognized. Written to a DVD it booted up with out error.

I thought to write the USB to a DVD. The three programs I tried all recognized the USB as a potential disk to write to, but none would accept the USB drive as a Source Disk image. I fear the image has been corrupted.

---

### Post by CelticWarrior on 2020-11-30
You don't burn a DVD from a USB... You use the exact same ISO file.

Regarding your problem booting from USB... Have you by any chance disabled "legacy USB support"? Not to be confused with Legacy/CSM in UEFI.

---

### Post by rbmorse on 2020-12-01
I looked this thing up.  They're charging $14 USD for a small form factor USB key drive with Ubuntu 20.04 preinstalled.  Sold as a plug and play system.  No way to know how the Ubuntu installation was created. 

My guess is it's a UEFI mode install.  

I ordered one just because I'm curious about it and to see if there's any "bonus" features they aren't advertising.

---

### Post by pme 72 on 2020-12-01
Thank you, CelticWarrior, news to me, good to know!

     None of the write to USB programs would recognize the ISO file as an appropriate medium either. However, the file name is now UBUNTU 20_0. I did get an error message when I ran dmesg after an unsuccessful attempt to boot from the USB:

     [  141.819339] FAT-fs (sdg1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.

---

### Post by CelticWarrior on 2020-12-01
The ISO is here [https://ubuntu.com/#download](https://ubuntu.com/#download) as well as tutorials for burning into a DVD or USB.

---

### Post by pme 72 on 2020-12-01
rbmorse, 
Thanks for your input. That's basically why I ordered it, that, and the need for another $13+ for free Amazon shipping on something I really did need. I hope you'll share your results.

---

### Post by pme 72 on 2020-12-02
CelticWarrior, 

I have searched the BIOS options and so far have not found any "legacy USB support" options. Boot is BIOS based not UEFI. 

The fellow who rebuilt my PC gave me the Motherboard User Guide. I've not found any mention of legacy USB support in those pages.

---

### Post by CelticWarrior on 2020-12-02
> **pme 72 said:**
> CelticWarrior, 

I have searched the BIOS options and so far have not found any "legacy USB support" options. Boot is BIOS based not UEFI. 

The fellow who rebuilt my PC gave me the Motherboard User Guide. I've not found any mention of legacy USB support in those pages.

It's under Advanced > USB configuration and mentioned in Chapter 2, page 16 of your user's manual (added bold for the relevant part):

> Legacy USB Support [Auto]
Allows you to enable or disable support for Legacy USB storage devices, including USB flash
drives and USB hard drives. [B]Setting to Auto allows the system to detect the presence of USB
devices at startup[/B]. If detected, the USB controller legacy mode is enabled. If no USB device
is detected, the legacy USB support is disabled. Configuration options: [Disabled] [Enabled]
[Auto]

The [user's manual]("https://dlcdnets.asus.com/pub/ASUS/mb/SocketAM3+/M5A78L-M_LX/E6524_M5A78L-M_LX.zip") isn't the same as the quick setup guide.

And I hope that by now you understood how to do your own USB installation media instead of ordering an expensive one from Amazon or whatever. Also a preinstalled Ubuntu is NOT the same as installation media. I agree with rbmorse above that what you bought is probably an installation in UEFI mode. If so it obviously won't and can't work in your old BIOS system, it only boots in modern UEFI systems. In summary, a waste of money. For the same price you could have bought a few USB sticks.

---

### Post by pme 72 on 2020-12-03
CelticWarrior, Thank you, I am eternally grateful. 

Just checked, Legacy USB Support was set to [Auto] but sounds like it didn't matter. When the time comes I'll find out how advanced my USB installation skills are. 

Thanks again, I hope someone upstairs grants you and yours a joyous Christmas holiday!

---

