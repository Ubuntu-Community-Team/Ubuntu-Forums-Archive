---
title: "Installing Lubuntu in GPT hard disk"
date: 2015-12-19
forum: Installation &amp; Upgrades
---

### Post by KayeNg on 2015-12-19
Hi guys

I don't have the desktop computer right now but I think it is a Lenovo H530, preinstalled with Windows 8 or 8.1.  The os is corrupted and cannot boot.  I've decided to have a [COLOR=#000000]clean install of everything; I want a dual boot system of windows 8 and lubuntu. 

I boot a lubuntu live usb, used gparted to wipe everything in hard disk, then set it up like so:[/COLOR]

[COLOR=#000000]| Windows OS |                     Mydata                  | Lubuntu OS | swap |

That's 4 (four) primary partitions, initially.  All are primary because the hard disk is GPT; cannot create extended partition.

I don't have the windows disc yet so the above windows partition is currently a blank NTFS partition.  

[/COLOR][COLOR=#000000]I proceed to install lubuntu in the Lubuntu OS partition. "Device for boot loader installation" was set to /dev/sda/[/COLOR]
[COLOR=#000000]
Reboot. I got a black screen saying something which I forgot (the desktop is far away from me now, I'll get to see it couple days from now). It either said it cannot find os or boot loader or something. not sure. sorry.

[/COLOR][COLOR=#000000]Reminder: the hard disk is GPT.

What do I do now?  

By the way, don't worry about me installing lubuntu first then windows.  I know the grub loader will be wiped out but I think it's an easy fix, right?  My concern right now is to get the desktop running again, with or without windows os.

Thank you.


[/COLOR]

---

### Post by oldfred on 2015-12-19
With gpt you do not have the limit on primary partitions. Gpt default is 128 partitions all the same or essentially all primary.

How you boot install media, either UEFI or BIOS/CSM is then how it installs. For both Window & Ubuntu. Generally better to install Windows in UEFI mode first as it requires extra partitions.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Ubuntu will use the same ESP - efi system partition as Windows.

You can install Ubuntu in BIOS/CSM boot mode on gpt drive. But Windows only boots in UEFI boot mode from a gpt partitioned drive and you really need both Ubuntu & Windows in same boot mode either both BIOS or both UEFI. If you really want BIOS boot then you have to convert drive to the 35 year old MBR(msdos) partitioning with the 4 primary partition limit.


 Install Windows 8
[http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html](http://www.eightforums.com/tutorials/2328-uefi-unified-extensible-firmware-interface-install-windows-8-a.html)

       
 Fast Startup off
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html

      [/URL]
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

More details on UEFI installs in link in my signature below.


    [URL="http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html"]
[/URL]

---

### Post by grahammechanical on 2015-12-19
You can wait until you are in a position to give us more accurate information about any problems.

Why should having GPT partitioning table be a problem? It allows us to create any number of "primary" partitions. The old MBR partitioning table only allows us to have 4 primary partitions and so we are forced to use one primary partition as an extended partition and then create logical partitions within the extended partition. Creating, resizing & moving partitions is less complicated with GPT.

It is more important to know the differences between installing computer operating systems on a motherboard BIOS boot system and a UEFI boot system. Have you read this?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

When you wiped everything on that hard disk did you do it by creating a new partition table? Did you install Lubuntu by using the Erase disk and install Lubuntu option? That might have been the better way. If you use the Something Else option and if you were installing Lubuntu in EFI mode, did you assign an EFI boot partition for the EFI boot files to go in? Failure to do that might be the cause of your present problem.

I also think that if we are using GPT and installing Linux in BIOS/Legacy/Compatibility mode then we also need a BIOS boot partition.

Regards.

---

### Post by KayeNg on 2015-12-22
Thanks for your input guys.  I've finally installed Lubuntu in the desktop.  

1.  First off, I created a live USB lubuntu 64-bit, because I think it's about time I use UEFI, and I read somewhere that it's better to install 64-bit operating system if you're booting UEFI, is that correct? 


2.  To be able to install thru a live USB 64-bit Lubuntu, I had to go to BIOS by pressing F1.  Once there, I switch the "boot mode" to "UEFI only".  Then arrange the boot sequence accordingly.

So now the hard disk looks like this in gparted (Five partitions in total) :
|  boot  |       reserved for Windows 8       |                    Data                  |   lubuntu   | swap |

The first one (leftmost) has a mount point of /boot/efi and has a flag of "boot".  The second as you can see above is for Windows 8, which is not installed on the hard disk yet.  The third is an NTFS Data partition where I plan to store all my files like documents, music, pictures, etc.  Fourth and fifth is for lubuntu OS and swap, respectively.

3.  Additionally, during installation, I believe I set /dev/sda1 (the /boot/efi partition) as the "device for bootloader installation".  Is this ok?

I am typing this inside the installed lubuntu system, so everything seems great.  My questions now are:  

Is the configuration above sufficient enough to install the windows 8?  Or do I have to cut down my data partition and create a few new ones?  

Or do I have to erase everything and start from scratch (because I should have installed windows 8 first?) ?   

Did I screw up number 3 (above)?  Was it suppose to be /dev/sda (instead of /dev/sda1) for "device for bootloader installation"?

Thank you for your time!

---

### Post by sudodus on 2015-12-22
> Did I screw up number 3 (above)? Was it suppose to be /dev/sda (instead of /dev/sda1) for "device for bootloader installation"?

The answer used to be yes to that question, but obviously it works :-) The reason is that UEFI looks for the EFI partition, which should have a boot flag (and you have it). Then it is not necessary to install the grub bootloader to the head of the drive, like it is when booting in BIOS mode.

Maybe I am too suspicious against Windows, but I do not rely on it enough to install it after installing linux. Now in your situation, I think you should try. It might stay within the drive space you tell it to use. But I think you might have to repair the booting afterwards. In that case you can try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair).

---

### Post by oldfred on 2015-12-22
You should normally install boot loader to sda not sda1, but with UEFI it does actually install to the ESP, or your sda1, no matter what you say. In BIOS mode you must say sda.

Windows likes a small extra system reserved partition. It is unformatted space, 128KB, often used for security keys or other hidden data.
       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)
    
At least with UEFI Windows does not overwrite the Ubuntu/grub boot loader, but it still will make Windows first in boot order. You can use UEFI or one time boot key to boot into ubuntu entry and use efibootmgr to set boot order. Some systems only want to boot "Windows" entry. And then we have to do work arounds.

       Change boot order with efibootmgr, some require all 4 char others 1 is ok.
[http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr](http://askubuntu.com/questions/485261/change-boot-order-using-efibootmgr)
sudo efibootmgr -o 2,1

            [http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)

---

### Post by yoshii on 2015-12-22
I was going to add that you might need to set the boot flag to on for the bootup partition, but it seems that somehow you managed to do that.  Somebody who needs to do that can use gParted for that.  
Also to anybody else reading this, if you happen to use MBR instead of GPT, Windows requires the first logical partition to be MSDOS/Windows in order to boot.  And there should be about 2 MB of empty nonformatted space before the first partition begins.  People used to say 1 MB, but there's a bug in older versions of gParted so 2 MB is the safe workaround.  And like the others implied, you have to edit your BIOS boot mode to accomodate MBR booting instead of UEFI.  It's typically called the "legacy mode" if it doesn't mention MBR.

---

### Post by KayeNg on 2015-12-30
Thanks guys.  No success yet but I may have found another reason to hate windows.

To reiterate, the desktop is a Lenovo H530s and it is pre-installed with "Windows 8.1 64-bit Operating System" (according to [http://shop.lenovo.com/us/en/desktops/lenovo/h-series/h530s/](http://shop.lenovo.com/us/en/desktops/lenovo/h-series/h530s/))


1.  I wiped entire hard drive; all partitions deleted and formatted.  Made one that looks like this:

|  boot  |       reserved for Windows 8       |                    Data                  | Lubuntu   | swap |

The windows partition is still empty.  The only OS running is Lubuntu, and it's working great!

2. Logging into the working Lubuntu system, I extracted the windows product key thru the terminal with this command:
> **sudo hexdump -s 56 -e '"MSDM key: " /29 "%s\n"' /sys/firmware/acpi/tables/MSDM**

3.  I wasn't able to create the windows recovery or installation disc before I wiped the hard drive, so I had to resort to creating a Windows 8.1 installation media using USB.  
[URL="http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media"]http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media
[/URL]I'm quite certain I chose 8.1 , 64-bit, which is the pre-installed version, according to [http://shop.lenovo.com/us/en/desktops/lenovo/h-series/h530s/](http://shop.lenovo.com/us/en/desktops/lenovo/h-series/h530s/)

4.  I boot the windows 8 usb installation.  It asks for the product key.  I enter it and I get
> The product key entered does not match any of the windows image

What am I doing wrong??

Thanks for your time!

PS I wonder is this could be a solution? I'm thinking of trying the first method -- "**Through Source Files" **
[URL="http://www.optimizemswindows.com/the-product-key-entered-does-not-match-any-of-the-windows-image/"]http://www.optimizemswindows.com/the-product-key-entered-does-not-match-any-of-the-windows-image/
[/URL]
Or is it possible that it was pre-installed with a 32-bit windows 8.1? Or even windows 8 and not 8.1?  I just assumed it was Windows 8.1 64-bit because of the following reasons:

1.  The desktop came with a "Lenovo **Win8.1** Drivers Pack V1.3", hence I downloaded 8.1

2.  The BIOS is UEFI; I read somewhere that one should install 64-bit OS if boot mode is UEFI (I may have got that wrong? Can anyone confirm?) , hence I downloaded 64-bit.

Regarding number 2, if it was indeed 32-bit, would I be able to install it alongside the same desktop which is already running 64-bit Lubuntu?
Also, again regarding number 2, this [URL="http://support.lenovo.com/ph/en/downloads/ds101277"]http://support.lenovo.com/ph/en/downloads/ds101277
[/URL]seems to prove that the desktop in question can be installed with either 32-bit or 64-bit?  Can anyone confirm?

---

### Post by oldfred on 2015-12-30
I thought the new UEFI systems have the product key in the UEFI and you do not manually enter it. But the key in the UEFI is only good for the OEM (vendor) version of Windows.
So best to just restore from the backup.

 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c)

Also are you now trying to install in BIOS mode? The pre-installed Windows would have been 64 bit Windows in UEFI boot mode. Product would not work in BIOS mode.

Windows only boots from gpt partitioned drives with UEFI.
Windows only boots from MBR(msdos) partitioned drives with BIOS.
And for both Windows & Ubuntu how you boot install media is then the install mode, UEFI or BIOS.
If you force install in mode that requires different partitioning, it will totally repartition drive, erasing everything. So make sure you have correct type of partitioning to go with boot mode.

 Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by KayeNg on 2016-01-01
What a frustrating task this is. First of all, I followed the advice of **genet** in this forum:
[URL="http://www.eightforums.com/installation-setup/38486-need-help-formatted-genuine-windows-8-lenovo.html#post330277"]
http://www.eightforums.com/installation-setup/38486-need-help-formatted-genuine-windows-8-lenovo.html#post330277[/URL]
 
Still unsuccessful.

One question, oldfred:
Using another computer to create the install media, does it matter if said computer boots with BIOS or UEFI?

Because you said:> The pre-installed Windows would have been 64 bit Windows** in UEFI boot mode.**

For example, if said computer (running windows 7) was booted with BIOS, and it was used to create the install media by following the advice of** genet **in the link above**,** would I be able to use it to re-install windows 8 to the Lenovo desktop?   

I tried both 64-bit and 32-bit and they wouldn't install; "product key does not match...".  Perhaps it was because they (the install media) was created inside a windows system that was booted with BIOS?  Although I have yet to check whether the windows 7 machine boots with BIOS or UEFI.  

Thanks for your time!

---

### Post by sudodus on 2016-01-01
> Using another computer to create the install media, does it matter if said computer boots with BIOS or UEFI?

Oldfred lives in another time zone, so I'll try to reply: No, I think most (if not all) tools to create install media will create systems that are independent of the host system's boot mode.

I can explain an easy case: If you use [mkusb](https://help.ubuntu.com/community/mkusb) and create ***a live-only install pendrive***, it will clone the iso file, each byte will be copied as it is from the iso file to the pendrive, and that process is completely independent of the host system's boot mode (UEFI or BIOS).

---

### Post by KayeNg on 2016-01-01
In that case, sudodus, I give up.  stupid windows, not worth my time.  I should have told the one who bought the computer to just buy a generic one instead of branded pre-installed windows machine, and if windows is really needed, then just buy a retail dvd.

---

### Post by sudodus on 2016-01-01
*oldfred* will probably give you some new ideas to try, so don't give up yet :-)

---

### Post by KayeNg on 2016-01-01
Looks like I made a mistake. The sticker on the side of the desktop says windows 8.1 SL. Not 8.1 only.
My bad. I'll try again, it's most likely a 64 bit, correct?

---

### Post by sudodus on 2016-01-02
SL seems to mean Single Language.

A Lenovo H530 is most likely delivered with a 64 bit version of Windows, so yes.

---

### Post by oldfred on 2016-01-03
Except some of the mini systems with Atom processors that used 32 bit UEFI on 64 bit system, almost all Windows 8 systems are 64 bit. And they all use UEFI with secure boot turned on, but allow users to turn secure boot off. 
Ubuntu can be installed with secure boot on, but grub will not boot Windows with it on from grub menu, you have to choose from UEFI boot menu or one time boot key like f10 or f12, but varies by brand of system.

Product key does not match sounds like the product stored in the  UEFI is not correct for the version you are installing. You need either to reinstall the vendor's version, or may even have to purchase another license.
This says it is a more generic recovery version, but you should always do a full image backup of Windows, even if you do not think you want it. And I have no idea if this may work with a single language version.

 Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

---

### Post by KayeNg on 2016-01-13
Finally success.  The pre-installed windows was indeed windows 8.1 single language (SL) 64-bit.  So now I have a branded Lenovo desktop computer with a dual boot system, Lubuntu and windows 8.1 SL.  

For people who might read this in the future, I'd like to repeat that I installed lubuntu 64-bit first before the windows os, BECAUSE the pre-installed windows was corrupted, so I decided to wipe the entire drive--as in deleting every partition and created several partitions using gparted.  I then installed lubuntu, then windows.  Then, as expected, I was able to boot windows, but not lubuntu.  

oldfred, fortunately I didn't have to follow the instructions in your links in order to boot both operating systems. All I had to do was boot the lubuntu live usb and typed:

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

...then I was able to boot both operating systems.  I'll mark this thread as solved.  Thanks a lot guys, appreciate it!

---

