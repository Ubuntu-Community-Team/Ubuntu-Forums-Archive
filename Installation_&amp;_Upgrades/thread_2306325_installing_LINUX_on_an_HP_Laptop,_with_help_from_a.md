---
title: "installing LINUX on an HP Laptop, with help from a Mac Desktop"
date: 2015-12-14
forum: Installation &amp; Upgrades
---

### Post by wfriedwaldgmail.c on 2015-12-14
thanks for reading this.

Here's what I'm trying to do: 

I have a very inexpensive 2015 HP stream desktop.  It caught one of those funky windows viruses and since I have never liked windows to begin with (and I vastly prefer linux), I would like to get rid of windows altogether and install some version of linux.

My other computer is a Mac Desktop, running the latest system El Capitan.

the HP does not have a DVD/CD disc drive, but it does have USB3 ports, so I can hopefully use the Mac to prepare a flash drive that will run and install Linux on the HP laptop.

does that make sense? I assume that's doable.

thanks very much for any help you can offer,

Will

PS: the only programs i need on the HP are 1. some kind of browser and 2. VLC media player, which I believe exists in a Linux version.

---

### Post by Dreamer Fithp Apprentice on 2015-12-14
> **wfriedwaldgmail.c said:**
> I would like to get rid of windows altogether and install some version of linux. . . .
the HP does not have a DVD/CD disc drive, but it does have USB3 ports, so I can hopefully use the Mac to prepare a flash drive that will run and install Linux on the HP laptop.

does that make sense? I assume that's doable.Sure. That's a pretty normal way to install really. Just get the appropriate image and make a bootable flash drive from it. Check the download area. There used to be separate images for this purpose, but I think they no longer bother with that. You may have to search for the appropriate software to do that on your Mac, but it is a pretty normal procedure so it shouldn't be hard to find. If you poke around it wouldn't surprise me if there were Mac specific directions linked to from the download page, or at least easy to find.

---

### Post by yancek on 2015-12-15
You can download the unetbootin software for Mac from the link below and use it to create a bootable flash drive of whichever Linux you want to use.  Numerous options at the site below with links to the home page of each distribution so you can choose.

[http://unetbootin.github.io/](http://unetbootin.github.io/)

[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by Bucky Ball on 2015-12-15
Welcome. I have a HP Stream 11. If you have the same hardware 'under the hood' as mine, follow yancek's instructions and install via USB. Everything worked 'out of the box' for me.

I have a slimmed down version of Xubuntu 14.04 LTS and it runs faultlessly and fast. Better than I expected the machine to perform, in fact. You will get a better response with a lighter spin/flavour than Ubuntu on that machine I'd say. :) Does it have an eMMC card - no 'drive' - and Celeron processor? If so try Xubuntu or Lubuntu. Also, only the official flavours are supported in the main areas here and by Canonical so best for support if you try and 'keep it in the family'. 

Up to you if you go for something more exotic, and experimenting's what it's all about of course, but you can always set up a stable, well-supported flavour and do that later. :)

---

### Post by wfriedwaldgmail.c on 2015-12-15
thank you all very much for your response and input! 

Very helpful!

yes, I'm going to stick with the most basic "flavor" of linux, something that we can be as sure as possible will work.

will enthusiastically try what Mr. Yancek suggests, and let you know the results.

yes! thanks!

w

Okay, i hit a snag:

I seem to have constructed the USB flash drive okay (using a FAT-formatted drive)  - using Xubuntu LTS (I think that was the version...)

but when I start the laptop, it defaults to the hard drive - it doesn't seem to look for the USB drive.

is there a way to tell the machine to boot from the USB drive rather than the hard drive?

thanks very much again!

---

### Post by Bucky Ball on 2015-12-15
Quirky, but try hitting F12 at boot (I think it's F12 on the stream) and get to the boot device list, not the BIOS. Try choosing it from there. On my Toshiba this is the only way I can boot from anything but the hard drive for some reason. 

What software did you use to create the USB installer? If you need to try again, make sure you reformat the USB to FAT32 again before burning the image again. Safer. :)

---

### Post by wfriedwaldgmail.c on 2015-12-15
1. okay, this seems to be the way to do it - 
combination of F10 & ESC at startup!

<http://h30434.www3.hp.com/t5/Notebook-Operating-System-and-Recovery/How-do-I-access-the-BIOS-on-the-HP-Stream-13/td-p/4825182>

2. the flash drive was formatted in DOS, and the system did NOT see it.
wanted to try reformatting in FAT32, but that doesn't seem to be an option.
however, there IS an option for exFAT - should I try exFAT?
(little I know about windows, I see somewhere that exFAT is the "successor" to FAT32.)

will try it and let you know ...

thanks again!

w

---

### Post by oldfred on 2015-12-15
It should be FAT32 with boot flag.
That then can be used for UEFI or BIOS installs with Ubuntu.
Your Mac should also use gpt partitioning, but that is not required.

But installer software automatically erases flash drive, formats flash drive, extracts ISO and installs a BIOS boot loader. If UEFI only boot desired for Ubuntu installer you can manually format flash drive FAT32 with boot flag. Then extract ISO. UEFI boots from /EFI/Boot/bootx64.efi which exists in Ubuntu folders on install media. Only 64 bit works with UEFI, although there is now a 32 bit UEFI method for some of those crippled 32 bit UEFI systems.

 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by wfriedwaldgmail.c on 2015-12-15
the (non-Mac) options I get seem to be:

MS-DOS
exFAT

and via a special add-on program
NTFS

but there's no FAT32 option.

if this install requires a FAT32 drive and nothing else will do (even exFAT), then, alas, I fear that I am dead in the water!

thanks again!

w

---

### Post by oldfred on 2015-12-15
Maybe this will help. I do not have a Mac to know for sure.
 [http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187](http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187)

      
 Fix for making bootable Ubuntu Live USB with persistence using Unetbootin on a Mac - Quackers
[http://ubuntuforums.org/showthread.php?t=2174630](http://ubuntuforums.org/showthread.php?t=2174630)

---

### Post by wfriedwaldgmail.c on 2015-12-15
More info 

I just noticed that the program UNETBOOTIN ONLY seems to recognize a flash drive in NTFS, not exFAT or DOS

the exFAT drives do not turn up as options in UNETBOOTIN, only NFTS.

however, I haven't been able to try FAT32 since I don't have any way to format a flash drive in FAT32, unless there's some little mac utility out there that can do it.

help again!

thanks!

W

PS: so far, I think I have tried all three available DOS formats in the HP stream

MS-DOS (FAT)
exFAT
NTFS

and the HP stream does NOT apparently recognize any of them!  nuts! rats! what to do

---

### Post by oldfred on 2015-12-15
When it says ms-dos(FAT) what version of FAT, is that not FAT32?

---

### Post by wfriedwaldgmail.c on 2015-12-15
I don't know! All i can say is the program [COLOR=#000000]UNETBOOTIN worked fine with that format, but that the HP did NOT recognize that drive, or find it when I tried to boot from it.

so I don't know!

thanks!

w[/COLOR]

Oh - somehow I missed these two earlier!

[COLOR=#000000][INDENT]Maybe this will help. I do not have a Mac to know for sure.
[http://computers.tutsplus.com/tutori...mac--cms-21187]("http://computers.tutsplus.com/tutorials/how-to-create-a-bootable-ubuntu-usb-drive-for-pc-on-a-mac--cms-21187")

WF: wow! this is a lot of steps!  But of course I'll try it ... will see what happens. probably won't get to this for a few days ...

Fix for making bootable Ubuntu Live USB with persistence using Unetbootin on a Mac - Quackers
[http://ubuntuforums.org/showthread.php?t=2174630](http://ubuntuforums.org/showthread.php?t=2174630)

WF: am I reading this correctly? It seems like these are instructions for installing Ubuntu on a Mac machine - what I'm trying to do is use a Mac to create a USB drive that will install Ubuntu on a windows laptop.  or am I confused? anyhow, thanks for the input!  yes![/INDENT]
[/COLOR]

W

---

### Post by oldfred on 2015-12-15
I gather Mac uses .dmg files not .iso as the image file for a flash drive.
But do not know as I have only used a PC.

I do know on a PC, you can format the flash drive as FAT32 with a boot flag, and just extract the ISO and copy to flash drive. That is UEFI boot only, and will not work in BIOS mode.
The install of syslinux is to create a BIOS boot.

 UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by Bucky Ball on 2015-12-15
UNetbootin may create a Live USB on an NTFS partition, but it won't work. It needs to be FAT32, as stated previously.

---

### Post by wfriedwaldgmail.c on 2015-12-15
so I'm left with two inter-related questions:

A. how is FAT32 different from MS-DOS and / or exFAT?

B. since the DISK UTILITY program on the current MAC OS EL CAPITAN does not offer a "FAT32" option (although it does offer a choice of MS-DOS, exFAT and with an add-on, NTFS), then how can I create a FAT32 USB drive?

and oh yes: MAC can use "DMG" and "iso" files, no problem. However, one thing we can't use is an "exe" file!

thanks again!

w

---

### Post by oldfred on 2015-12-15
MS-DOS goes all the way back to original FAT, FAT16 & FAT32. I would think your Mac would be using FAT32. Part of issue is Microsoft patents, which for FAT they say they will not enforce, others say they could not really enforce them anyway.
But ex-FAT is a newer Microsoft and may have legal issues. Most Linux do not have full support, driver is relatively new. 

UEFI uses FAT32 for the ESP - efi system partition. And Mac with Intel was the first major use of UEFI. 

But all the installers use FAT32. And that should not be an issue.

---

### Post by sudodus on 2015-12-16
I think you can run ***dd*** (from the under-lying unix operating system) in MacOS. dd is nick-named 'disk destroyer' because it does what you tell it to do without questions, so if you tell it to wipe your family pictures ... but if you use it correctly, dd is a very powerful tool.

If you can and dare use dd, you can use it to clone the iso file to a USB pendrive. And that pendrive can be used to boot a PC. This method does not depend on previous formatting. (I made mkusb for linux in PC to wrap security around dd, but it does not work in MacOS.) Maybe there is some corresponding tool, but dd can certainly do the job, just ***make really sure that you are cloning to the pendrive*** and not to the internal drive or some other drive with valuable data).

Use the unix tools available to identify the drive letter. Maybe blkid, fdisk, gdisk, parted (I don't know which tools are available in the underlying unix of MacOS.) I would not rely on the identification in the MacOS, it might not match what is used by the underlying unix system (and dd).

All partitions on the pendrive should be unmounted. You probably need root (superuser) privileges, here symbolized by the # prompt,

```
# dd if=file.iso of=/dev/sdx
```

where x is the drive letter identifying the pendrive. It is probably not a, but can be b, c, ... , depending on the number of connected drives and the order that they are recognized.

***Edit:*** An alternative is to borrow a computer with Windows in order to make the USB boot drive to format the pendrive and after that use Unetbootin, or to use [Win32DiskImager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) (which is cloning like dd in Windows).

---

### Post by wfriedwaldgmail.c on 2015-12-16
Now I am really at a loss - I checked at the MAC forum, and the consensus is that "MS-DOS" is what the MAC system calls "FAT32" - so they are the same thing. OLD FRED was indeed correct!

So i have been trying a combination of USB flash drives

* that have not been reformatted since purchase, they're in the original factory format (MS-DOS / FAT32)
or
* that I have used MAC DISK UTILITY to format into MS-DOS / FAT32 -

after trying at least half a dozen flash drives, nothing worked in the HP Steam.

so I don't know what to do next ... apparently I can NOT boot from a USB flash drive.

any additional ideas?  should I start a new thread here?

thanks!

w

PS: I just saw the post from SUDODUS - it seems like the problem may not be the format of the USB drive but that the HP just can't read anything, if I tried MS-DOS (FAT32), exFAT and also NTFS, it seems like that's every option that there is ... right? no program or solution seems to be able to come up with a format that the HP Stream can actually read.  It failed on three for three.  what do we think? thanks again...

so it seems like I need another method, but don't know what ... the HP keeps wanting to boot into the old crappy crippled version of windows/dos ...

thanks!

w

---

### Post by sudodus on 2015-12-16
A cloned USB drive has the ISO 9660 file system (made with dd). It is different from what you have tried. And there are also other things to change.

Start from post #4 by Bucky Ball.

---

### Post by oldfred on 2015-12-16
Another user, says Lubuntu & Mint work and many others do not:
[http://ubuntuforums.org/showthread.php?t=2306323&highlight=hp+stream](http://ubuntuforums.org/showthread.php?t=2306323&highlight=hp+stream)

Looks like his settings are Legacy/BIOS mode. You may with the Mac have only a UEFI boot?
A HPs have issues with UEFI boot of anything other than Windows and require one of several work arounds depending on whether dual booting or just Ubuntu.

---

### Post by wfriedwaldgmail.c on 2015-12-17
thank you SUDODOS & OLDFRED ...

I will try!

I have been trying the mac UNETBOOTIN app to install the XUBUNTU option, but I can certainly try with LUBUNTU - that seems to be what Pchokola recommends.

will also try the "dd ISO" method and see what results that yields.

yes! thanks!

w

---

