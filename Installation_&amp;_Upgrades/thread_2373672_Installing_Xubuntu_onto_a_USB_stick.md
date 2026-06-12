---
title: "Installing Xubuntu onto a USB stick"
date: 2017-10-08
forum: Installation &amp; Upgrades
---

### Post by mantas4682 on 2017-10-08
Hello, I'm sorry if this is a stupid question and the answer is probably already out there, but I'm new to this and I just can't wrap my mind around it.

I'm trying to get Xubuntu onto a USB stick, which I think I did? What I assume I've entered is a Live Session to try out Xubuntu and that would be enough for me, I know there is persistent data that saves between sessions but after my initial try any other boots fail to load, the splash screen just goes on forever, nothing seems to be happening. The other option on boot is to Install Xubuntu which I assume would attempt to install it onto my hard drive and not the mounted USB which I want it on. My hard drive is damaged, so Windows are hardly working and I cannot afford a new computer nor do I want to spend anything extra on this old, crummy laptop. I really liked what I got when I was trying out Xubuntu and it would definitely do until I can justify a replacement. Can I get it to act like a persistent OS as if it were installed onto my hard drive?

---

### Post by ian-weisser on 2017-10-08
Welcome to the forums.

In order to make your current Live environment persistent, you must reformat your USB stick to create a persistence partition. This will destroy you current Live .iso image, so you must re-create your Xubuntu Live on the properly-prepared USB stick.

Alternately, you can install a full Xubuntu system onto a *second* USB stick. A Live USB cannot overwrite itself. You must change a couple settings in the installer to install to USB instead of HDD.

Neither option is particularly difficult, and many tools and tutorials are available.
However, you must pay close attention to the feedback from those tools. Sometimes things go wrong.

Warning: Any time you install an Operating System, you risk TOTAL LOSS of everything on that hardware, including other Operating Systems and all your personal data. Before mucking about with partitons or installing anything, make sure you have all your data (and your Windows Product Key) properly backed up.

---

### Post by efflandt on 2017-10-08
It used to be easy to add persistent data to a live/install system with Startup Disk Creator, but that is more difficult now that it is a combo BIOS/UEFI boot and the image for that is written directly to USB instead of installing files on a FAT32 partition with easy addition of filesystem in a file for persistent data. To actually install on USB you would need the live/install system on one USB (or DVD) in order to do a regular install to another USB device (minimum 8 GB, more would be better). When you get to the partitioning part of install, you should select "Other" and make sure that you install Ubuntu and grub (drop down list) to the USB drive that you intend to, because I am not sure what "Use entire drive" (which drive?) or "Use unallocated space" might do for installing system and grub.

Depending upon the amount of RAM you have, if the USB you are installing to is a mechanical drive you can add swap about equal to or a little larger than RAM because some stats use decimal units of 1000 vs. binary units of 1024. If the USB you are installing to is flash memory you may want to think about whether you want any swap at all. I never used swap on my desktop PC with 8 GB RAM or even on a tablet PC with only 2 GB RAM that boots from SD card. But I do not use that tablet PC for much because it is only 2-core 1 GHz (slow). Swap is used if you run out of memory or you want to hibernate. Another option is to add swap, but adjust swappiness to minimize its use [https://askubuntu.com/questions/103915/how-do-i-configure-swappiness](https://askubuntu.com/questions/103915/how-do-i-configure-swappiness)

---

### Post by ajgreeny on 2017-10-08
Take care if your computer boots using UEFI as no matter what you ask it to do with grub at installation of the full OS (not a live with persistence), the installer will put grub onto the EFI partition of the first drive, ie, most likely the internal hard drive, not the USB.  I am not sure how you overcome this when installing other than perhaps booting the live system in legacy mode, meaning the installation will also be in legacy mode, but that could mean that it will boot only on machines with legacy BIOS, though that may not be correct, I am unsure whether that is the case.

---

### Post by mantas4682 on 2017-10-09
This makes a lot more sense, I think I got it installed now properly. Though the OS runs much slower and clunkier than the live version I was on, though it's the same USB, same port. What is that about? Even the live version I was running from a DVD whilst installing it onto this USB ran smoother than this. Am I missing something again? Should I try a different distro?

---

### Post by ajgreeny on 2017-10-09
Running a full install via a USB will always be slower than a HDD as it is limited by the i/o speeds of the USB connection. USB-3 will be faster than USB-2, of course but still slower than a normal hard disk installation as I understand things.

If you have sufficient ram I think you can set the system to boot into the OS in your RAM  but I will have to search for that and come back when I have time.

Here you are:-
[https://askubuntu.com/questions/829917/can-i-boot-a-live-usb-fully-to-ram-allowing-me-to-remove-the-disk](https://askubuntu.com/questions/829917/can-i-boot-a-live-usb-fully-to-ram-allowing-me-to-remove-the-disk)
[https://ubuntuforums.org/showthread.php?t=1499338](https://ubuntuforums.org/showthread.php?t=1499338)

I have not tried either of these so can not speak from personal experience, but if you do this on the fly using a temporary edit of the boot stanza in the grub menu it will only work for that one boot.  If successful you can later edit /etc/default/grub to always boot in that manner but don't do that until you know it works for your hardware.

---

### Post by sudodus on 2017-10-09
**An alternative to an installed system is a persistent live system.** It will be faster on a slow USB 2 pendrive or connection because it runs in RAM like other live systems. You can create such a system with mkusb according to these links,

[help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[help.ubuntu.com/community/mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

**It might be a good idea to get a fast USB 3 pendrive.** Often the flash memory hardware is the bottleneck, even via a USB 2 port in the computer. See this link,

[help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed](https://help.ubuntu.com/community/Installation/FromUSBStick#Notes_about_speed)

**With a fast USB 3 pendrive, you might find an installed system in USB good enough** (concerning speed and responsiveness). And it is possible to keep up to date like any installed system, while a persistent live system cannot be and should not be fully updated and upgraded.

These are several tips via the following link,

[Boot Ubuntu from external drive](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)

**You should consider some tweaks to reduce wear**, while might otherwise brick the pendrive,

[help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#Final_system_tweaks)

---

### Post by rochuang on 2017-12-18
the Live USB I created either won't boot or it boot to a command line environment and I don't know how to approach next. I tried using tools like unetbootin, Universital USB -installer, and YUMI, but none of them would create a bootable USB that can takes me to a User Interface. I know successed USB live CD should takes me to a UI window and guide me to install the Ubuntu Linux. 
 I am pretty sure I have configured BIOS correct to allow boot. still stocked at the issue and still searching for solution. 

See the USB live CD I created. isolinux, EFI , or install folders are all empty, not sure if that's normal. I assume it is, because I never install the OS using live USB yet.
 

[ATTACH=CONFIG]277872[/ATTACH][ATTACH=CONFIG]277873[/ATTACH]

---

### Post by yancek on 2017-12-18
Can you post the name of the Xubuntu iso file you downloaded?  Is it a desktop iso?  A server iso would not have a GUI.  The images you posted are from windows, is this the computer you are trying to install Xubuntu to?  Which windows version are you using?  Is it EFI?  If so, are you booting Xubuntu EFI with the settings in the BIOS?

---

### Post by rochuang on 2017-12-19
Hi Yancek, the iso file I download is a desktop version ubuntu-14.04.5-desktop-amd64. My PC an Acer aspire v13 laptop running windows 10 and I discovered it is running UEFI mode. I have tried to disable the UEFI mode but then it will boot into command mode waiting for my command, but I don't know what I need to type in there.

---

### Post by rochuang on 2017-12-19
update. a very weird thing. I've create the live USB dozen times already, and I realize when I first created it it does have files within isolinux , EFI, and install folders. But after I restart my computer everything gone (empty)..! Now my live USB looks like this [ATTACH=CONFIG]277875[/ATTACH] with a file called "wubi" on it. never seem it before from my previous installation. why is it so hard to create a live USB I don't get it.....

---

### Post by sudodus on 2017-12-19
Try a cloning tool,

[mkusb](https://help.ubuntu.com/community/mkusb) in Ubuntu.

[Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) in Windows.

Cloning is a very reliable method to create a USB boot drive with Ubuntu.

It will create a live-only system to 'Try Ubuntu' and to install Ubuntu.

---

### Post by mastablasta on 2017-12-19
also what kind of command line system you are booting into?

is the hardware linux compatible?

---

### Post by C.S.Cameron on 2017-12-19
You can install Ubuntu to the USB it was booted from if it is a Live system and booted with the toram option.

If your computer has sufficient RAM, Ubuntu should run mainly in RAM and for most stuff be nearly as fast as an install to internal disk even with USB2.

Have you checked your downloaded ISO with MD5SUM?

Edit:

When booted from the USB you can find the files that are actually on the drive located in filesystem/cdrom.

---

### Post by rochuang on 2017-12-20
Hi, I have use Win32 Disk Imager in Windows. to create USB disk, but after writing to USB my USB became unreadable...... which happen with one of other tool that does the same too. I tried twice and both same result. [ATTACH=CONFIG]277891[/ATTACH] not happen to yours? just me? haha

Thanks anyway.

---

### Post by rochuang on 2017-12-20
Its a linux command line start with grub> here with screen shoot
[ATTACH=CONFIG]277894[/ATTACH]

 I done so many time on making live USB disk and half of the Live USB I make  would bring me to this command prompt. 

For hardware I am not sure if it's linux compatible, my is a Acer Aspire V13 laptop. I can't even boot into the installation page I don't think hardware matter now isn't it?

---

### Post by rochuang on 2017-12-20
updates.

I finally able to boot into a "looks" correct place... but just that no matter what selection I choose it always return an error message saying "invalid magic number"!??! what magic number...  (see attached pic)
er~~ what's wrong with all this. by the way, tool I use this time is called "unetbootin-windows-657". I think I will continue re-trying other tools and see if they would make a success live USB or not... I've tried 5 tools already and they are all popular tools recommended from other discussion forums. 
[ATTACH=CONFIG]277892[/ATTACH][ATTACH=CONFIG]277893[/ATTACH]

---

### Post by mastablasta on 2017-12-20
that is not linux command line. that is GRUB (th eboot manager). you shouldn't see that.

check the downloaded image and make sure it matches the one on the server: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

make sure USB is not bad. change it with another one or burn the image to DVD.

---

### Post by rochuang on 2017-12-20
Hi actually I do have check my ISO using md5sum and it was correct! but I should of download other version of ISO just to see which version would work to me. 
You suggest USB might be bad? but how can a bad USB still allow me write and read correctly under normal use for other purpose like copying a file to it and open a file within the USB but only wrong when I am trying to boot into the image I made?! that is just odd..... but I will try with other USB stick and see what happen. THank!

> **mastablasta said:**
> that is not linux command line. that is GRUB (th eboot manager). you shouldn't see that.

check the downloaded image and make sure it matches the one on the server: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

make sure USB is not bad. change it with another one or burn the image to DVD.

---

### Post by sudodus on 2017-12-21
USB drives are somewhat different, and some of them work well as data storage drives, but not as boot drives.

Some USB pendrives can boot some computers, but not all of them.

You can also test your USB drive in another computer (of a friend, colleague, relative ...).

The problem can be in the USB drive (hardware or software).

The problem can also be in the computer (the settings in the UEFI/BIOS system, that can be set with the UEFI/BIOS menus).

---

### Post by Neville Hillyer on 2017-12-22
I recently experienced more difficulties than normal trying to get an iso put on a stick via a Mac to boot on a PC. I have done this previously without difficulty but nothing would work this time.

What eventually worked for me was reformatting the USB stick on Windows and using Universal-USB-Installer-1.9.7.9.exe

---

### Post by rochuang on 2017-12-26
Hi Sudodus, 

It turn out it was my USB pen drive that's not working properly. I made my live USB on the other pen drive and it works fine! weird and I still don't know the reason behind it... the original pen drive can read/write just fine, why can't it be boot.... 

Thanks for your help!


> **sudodus said:**
> USB drives are somewhat different, and some of them work well as data storage drives, but not as boot drives.

Some USB pendrives can boot some computers, but not all of them.

You can also test your USB drive in another computer (of a friend, colleague, relative ...).

The problem can be in the USB drive (hardware or software).

The problem can also be in the computer (the settings in the UEFI/BIOS system, that can be set with the UEFI/BIOS menus).

---

### Post by sudodus on 2017-12-26
> **rochuang said:**
> Hi Sudodus, 

It turn out it was my USB pen drive that's not working properly. I made my live USB on the other pen drive and it works fine! weird and I still don't know the reason behind it... the original pen drive can read/write just fine, why can't it be boot.... 

Thanks for your help!

I'm glad you found a solution :-)

---

### Post by Neville Hillyer on 2017-12-29
If you want to experiment you could try reformatting the problem pen drive on a PC - see me earlier post.

---

