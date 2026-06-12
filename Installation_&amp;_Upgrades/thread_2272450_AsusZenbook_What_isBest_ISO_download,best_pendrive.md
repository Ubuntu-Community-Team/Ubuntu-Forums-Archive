---
title: "AsusZenbook What is:Best ISO download,best pendrive setup WIN8.1UEFI"
date: 2015-04-06
forum: Installation &amp; Upgrades
---

### Post by gregory10 on 2015-04-06
I have dowloaded an ISO: Ubuntu Trusty 14.04.2 (LTS) wanting to install it on my newly purchased Asus Zenbook for dual boot with Windows 8.1
[FONT=Segoe UI][COLOR=#333333]The tutorials that I can find for dual boot Ubuntu only ever have reference to sda when referring to partition tables and the like which is referring to legacy drives.[/COLOR][/FONT]
[FONT=Segoe UI][COLOR=#333333]UEFI from what I read of is solely GPT it all refers to LBA partitions and LBA partition tables not SDA partitions and partition tables.
[/COLOR][/FONT]I looked but found nothing really as far as documentation on installing with UEFI using Ubuntu.


Spent the weekend researching, reading, finding as much info as possible wading through tutorials all that.
I have the newest version of Universal-USB-installer 1.9.7.4,exe with the ISO ready to make an new pendrive for the instal it's on the WIN8.1 Asus Zenbook
Also can make one on my Kubuntu machine but the one I made didn't seem to be up to date - I used an app called startup disk creator to make it (it might be making an MBR bios set by default).
and in the documents folder. I turned off 'secure boot' and turned on CSM which apparently makes both the legacy MBR and the new UEFI bios available for use. 

Heres the thing:
1. I checked it (the image and pendrive setup), its got the wubi.exe which is supposed to be the wrong thing according to another thread I read here on this forum.
2. It doesn't seem to have a file called: [FONT=Segoe UI][COLOR=#333333]BOOTx64.EFI (which apparently is necessary for this to be the secure new style UEFI anti malware setup it needs to be)[/COLOR][/FONT]
[FONT=Segoe UI][COLOR=#333333]3. the GRUB: in that file loopback.cfg there is nothing that points to anything to do with EFI in any of those variables in that one small file in /install/grub/loopback.cfg
[/COLOR][/FONT]    how can I be confident I am using the right setup???
[FONT=Segoe UI][COLOR=#333333].[/COLOR][/FONT]

[FONT=Segoe UI][COLOR=#333333]THESE ARE MY QUESTIONS:[/COLOR][/FONT]
[FONT=Segoe UI][COLOR=#333333]1.How do I know I have the right ISO (it is the latest one as far as I know) but is it set-up for dual boot installations with UEFI bios?
[/COLOR][/FONT]     1.a. For that matter how do I know for sure it has the Unity-gui on the Ubuntu OS version stored in that ISO image?

[FONT=Segoe UI][COLOR=#333333]2. How do I know or recognise the right grub or equivalent for UEFI instals for dual boot with windows 8.1 on a UEFI GTP SSD hardrive

I have a backup image for the machine and can easily reinstall the windows setup to what it was (I tested it and it works)
I don't want to wreck that drive partitioning because that would likely mean a lot of extra work or taking it back for service to Asus tech's in the city (I would lose at least a week).
That would put me back a week in my setup for the development work. Been working on an old Toshiba laptop running Kubuntu 
but I need a touch screen for testing the app as I work. As much as I hate windows I need to test it on the widows setup also.

Thanks for any help and advice anybody can give me. I really would like to have this all set and ready to use by the end of the week[/COLOR][/FONT]

---

### Post by ubfan1 on 2015-04-06
All Ubuntu ISOes have been set up for UEFI for years.  The startup disks (live media) are set up to boot either UEFI or BIOS.  If they don't work when properly burned to a CD or USB, then the machine's UEFI implementation is faulty (or broken on purpose).  Read
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
and
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
Avoid WUBI, it's not supported, and there are many other alternatives.
Avoid turning on CSM if you can boot the live media. Windows is in UEFI mode, and you need to install Ubuntu in UEFI mode too.
Do turn off fast boot in the Windows power options.  Secure boot should not matter, but I have an Asus which won't boot USB with secure boot enabled.  Ubuntu uses unity, kbuntu, xbuntu, etc. use other interfaces.
Avoid using LBA, it has nothing to do with GPT, and is just another layer of unnecessary complication in your case.
If you are booting from the SSD, it will have an EFI system partition (FAT, boot flag) for the bootloaders.  The machine's firmware will have pointers to select/start one of these bootloaders, which are kept in different directories so they don't interfere with each other.  The device also has a default bootloader, which I like to set up, since it may be invoked in some error situations.  This default bootloader is in /EFI/Boot/bootx64.efi, just like the live media has (note the live media is FAT, bootflag, has /EFI/Boot/bootx64.efi and grubx64.efi, so it meets all the default UEFI bootloader criteria.  All the Ubuntu bootloaders are usually just put into /EFI/ubuntu, and the grub.cfg file there just pulls in your mainteined grub.cfg from the /boot/grub directory on your root.

---

### Post by oldfred on 2015-04-07
The two standard partitioning type are MBR(msdos) and gpt(GUID). MBR is over 35 years old and still used with BIOS boot systems.
Gpt is the newer partitioning. Windows only boots from gpt drives with UEFI, but has been able to read gpt data drives for years even with BIOS/MBR on another boot drive.

Linux numbers drives like sda, sdb, sdc etc. And then the partitions are a number have the drive or sda1, sda2 etc. That make it clear where Windows may have a "d: drive" that could be on same disk and be sda2 or be on another disk and be sdb1. 

Then each partition can have format like NTFS for Windows or ext4 for Linux. Many others available.

How new is Zenbook? Or what processor?
The newer the system, the newer the version of Ubuntu you will need.

 ASUS Zenbook UX301LAA ultrabook under Linux  - reboot, power issues
[http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTQ)

 Asus Zenbook Prime UX31A (UEFI)  Blank screen resolved by turning secure boot off, many tests of Boot parameters
[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)
 install 13.04 on asus ux32a, problems with usb boot - several reports working well no details
[http://ubuntuforums.org/showthread.php?t=2146440](http://ubuntuforums.org/showthread.php?t=2146440)

---

### Post by gregory10 on 2015-04-07
@oldfred
the Zenbook is a UX303LA 
I got the latest image just now 'unbuntu 14.04.2-Desktop-AMD64.iso' is this the right image file?
I need confirmation to be confident to go ahead. Looks like it's one image fits all but thought 'AMD' was different from 'Intel' so would maybe be different ISO.
I seem to have seen a list of downloads somewhere and one was for intel and another for amd.

---

### Post by gregory10 on 2015-04-07
@ubfan1
thanks for the info and reply I read through the links
downloaded another image and it has the files you mentioned but still need confirmation I have the right one for the Asus Zenbook
the image says AMD64 as well as desktop so am thinking it is one image suites all. the \EFI\BOOT\ directory is there with those 2 files
so I definitely had the wrong one so glad I asked first. Still need confirmation I got the right image though for the 'intel' its not an AMD motherboard.
the image is titled: [COLOR=#000000]unbuntu 14.04.2-Desktop-AMD64.iso
is that the right one. the Ubuntu download page said it was for laptop and desktop didn't mention 'AMD' which I figure differs in the kind of CPU and chip set.

Can anybody confirm that it is the right ISO image? I just need confidence to go ahead and make the USB installer/live boot device.

With thanks
G[/COLOR]

---

### Post by oldfred on 2015-04-07
On the software side, AMD & Intel 64 bit are the same. The naming convention for the 64 bit uses AMD as their 64 bit with 32 bit backwards compatibility became the standard.
       [http://en.wikipedia.org/wiki/X86-64](http://en.wikipedia.org/wiki/X86-64)

Your ISO is correct. And that is a LTS or long term support version.
But some with very new systems like yours may be better with newer 14.10 or even the beta till end of April 15.04. Intel updates kernel, support software & video drivers, but updates take a while to be released, then those releases have to be incorporated into a distribution like Ubuntu. But those versions are not LTS and require updates every 9 months. 16.04 will be the next LTS, so it is a year away.

You also have nVidia and Intel video. That may cause issues. Does system boot with one or the other? Can you set that in UEFI or is it only software switchable? Newest nVidia driver supports nVidia Optimus.

 Dual graphics nVidia GT840M
[http://ubuntuforums.org/showthread.php?t=2262882](http://ubuntuforums.org/showthread.php?t=2262882)
Dual graphics install nVidia prime and newer nVidia driver
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)
[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

---

### Post by gregory10 on 2015-04-07
@oldfred
it's good to have that confirmation it really helps me knowing I got the right ISO seeing as I got it wrong once.
thanks again this is what I needed to know to be confident to go ahead. I'll put it up as resolved after I do the install which should be tomorrow by end of day.
I got most of the other info now. The partitioning scheme is what I have to plan next and that is mostly done now.
So thanks for the replies.

---

### Post by oldfred on 2015-04-07
Boot installer in live mode and see what works or more importantly what does not work. And then see if others have solved the issues of something not working.

We have lots of opinions on partitioning. :)
But I find even my most optimal partition plan is not so good several years later. I have Desktop and then get a new drive anyway as I do not trust older drives as main working drive. Every user has different needs or uses of system, so partitioning will vary.

---

### Post by gregory10 on 2015-04-08
I said it in the other thread just now

I don't think this will be properly sorted until I get rid of microsoft windows 8.1 from my new machine forever.
I made a backup of my own using using Macrium Reflect. Bought a 16GB pendrive to be able to delete the microsoft recovery partition by copying it according to their instructions.
they said in the tutorial that at the end of the process the software would give me the option of deleting that partition but it didn't. I'm stuck with what is called a 'healthy partition'
which isn't easy to delete. So far I found not on board windows tool that will do it. 

My next step is to do a full install of Ubuntu and in the process delete all of of the windows partitioning along with that mess of an operating system which has given me nothing 
but trouble for the last week including the trojan viruses that came with it. Yes not sure they came through win 8.1 itself exactly but their system had McAfee pre-installed and that
was the source. 

Now I need to find out how to install Ubuntu while deleting Microsoft Windows 8.1 at the same time.
It's a userpic mess on my system. I own the machine and intend to get that mess of my machine.

---

### Post by gregory10 on 2015-04-08
Oleased to be able to say that the instal all went well because I got rid of windows so no problems all done and am wiriting this from the new machine with the fresh instal of Ubuntu
I am so glad I made the decision to ditch Microsoft windows and do some serious computing.

thanks for all the input
all the best
G

---

