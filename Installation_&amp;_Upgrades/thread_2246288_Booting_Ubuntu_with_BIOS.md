---
title: "Booting Ubuntu with BIOS?"
date: 2014-09-29
forum: Installation &amp; Upgrades
---

### Post by aebkea on 2014-09-29
Hello, I am having trouble booting from my CD-Rom or Flash drive.  I can get Ubuntu to boot from my primary HDD but that results in me not being able to install Ubuntu to my primary HDD as I can not modify it in installation.  I have an Awards BIOS V.6 and have done everything that I have found online to get it to work.

When my CPU starts up I hold down F12 to let me select which device to boot from but no matter what option that I pick I can not figure out how to start it.  My CPU always defaults to opening Windows 7.  The USB options when I use the F12 key are USB-HDD, USB-CD-Rom USB-Floppy and USB-ZIP.  Any help would be appreciated.  My friend theorized that maybe my BIOS was overclocked so that it could not have time to read the devices before going to Windows 7 but I am not so sure.  Thank you for your help!  I can supply any more information if necessary.

---

### Post by yancek on 2014-09-29
You should have an option on boot which says "select ?? key to enter setup" which should get you into the BIOS where you should have a boot tab under which you should have a boot priority option and the different drive (if you have multiple drives) will show by name.  I don't know which key you would need on your machine, just watch for it on boot.

---

### Post by aebkea on 2014-09-29
> **yancek said:**
> You should have an option on boot which says "select ?? key to enter setup" which should get you into the BIOS where you should have a boot tab under which you should have a boot priority option and the different drive (if you have multiple drives) will show by name.  I don't know which key you would need on your machine, just watch for it on boot.

I just tried that but it does not appear to work either.  It just skips past everything and loads Windows 7.  I have found that it will appear to search for an OS to boot from on a server if I let it use LAN as a method of boot, but I don't know how to set that up.

---

### Post by Bashing-om on 2014-09-29
aebkea; Hello;

+1 to yancek. Also, I have Award-Phoenix for my bios, and in the bios setup I must first unlock access to the hard drives to change the hard drive boot priority.
Each and every bios is different even to differences between same machines. When in doubt consult the manual. That is not meant to be a short - rude-  response, but just that "reading the manual" in this instance is the better advise. In bios splash screen when 1st booting up is the notification, not only what key to use to access "setup" but -generally- at the op of the screen is a notification of the bios and the manufacturer. Somewhere on the screen is the version of that bios. -> Google is your friend.

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by aebkea on 2014-09-29
> **Bashing-om said:**
> aebkea; Hello;

+1 to yancek. Also, I have Award-Phoenix for my bios, and in the bios setup I must first unlock access to the hard drives to change the hard drive boot priority.
Each and every bios is different even to differences between same machines. When in doubt consult the manual. That is not meant to be a short - rude-  response, but just that "reading the manual" in this instance is the better advise. In bios splash screen when 1st booting up is the notification, not only what key to use to access "setup" but -generally- at the op of the screen is a notification of the bios and the manufacturer. Somewhere on the screen is the version of that bios. -> Google is your friend.
[INDENT][INDENT]my bit to try and help
[/INDENT]
[/INDENT]


Thank you for your response.  I looked up the serial number and found the correct BIOS manual although I find nothing in there about dual-boots, booting from a CD, Flash drive, nor any extensive information about any way to boot a different OS.  I will try to shoot Gigabyte an email and see if they have any tips.  Thanks!

---

### Post by Bashing-om on 2014-09-29
aebkea; Hello;

OK, The procedure to set the boot priority 'may' be somewhat obscure .
The process it's self is basically simple.

One just needs to tell bios what device is to be booted up in what sequence WHEN boot code is not detected.
In the boot priority set up one dictates the "look for" order.
In this use case for you at this time, you want to boot from the CD;
YOU must tell bios to set that CD drive as the 1st boot priority
2nd in the list will be the hard drive.

SO it works like so;
Turn on the box, and bios looks to see what is to be booted -- with the CD set as 1st priority .. bios checks for boot code on a Disk in the CD drive, if that GOOD boot code is found, well bios hands of to that boot code;
NOW if there is no disk ( or bad boot code) in the CD, then bios looks at the next device in the boot priority list for boot code, and will hand off booting to that code.

Change in plans; Now you want to boot from the external USB, guess what you MUST do ? As there exist boot code on the hard disk(s), you MUST set the USB drive ahead of the internal hard disk in the boot priority.
In this situation,:
1st boot priority is CD
2nd Boot priority is USB
3rd Boot priority is the internal hard drive.

Turn on the system, bios goes checking -> IF there is a bootable disk in the CD drive bios quits looking and hands off to the booting code in the CD. Bios's job is done. Else ->
There is no disk on the cd: Bios does not find boot code in that 1st boot priority list, goes to the next in the list - here USB. And finds the boot code in the USB, and hands off -> job done; Else ->
There is no disk in the CD, no USB is plugged in so bios -> looks for cd boot code, does not find it, goes to next on the list - USB-, does not find boot code finally goes to hard drive; hands off to the boot code on the hard drive -> job done.

Do you get the picture ?
Now in boot time it takes a lot of time for bios to find some boot code some where, SO to decrease the boot time, one sets as that 1st boot priority what you want to boot from.
Whether it is the CD, you want to boot from
Whether it is the USB, you want to boot from
Whether it is the Hard drive(s), you want to boot from.


It is all in the priority that you set in bios as to the 1st booting device. Every bios has some means to set this priority.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by aebkea on 2014-09-29
> **Bashing-om said:**
> aebkea; Hello;

OK, The procedure to set the boot priority 'may' be somewhat obscure .
The process it's self is basically simple.

One just needs to tell bios what device is to be booted up in what sequence WHEN boot code is not detected.
In the boot priority set up one dictates the "look for" order.
In this use case for you at this time, you want to boot from the CD;
YOU must tell bios to set that CD drive as the 1st boot priority
2nd in the list will be the hard drive.

SO it works like so;
Turn on the box, and bios looks to see what is to be booted -- with the CD set as 1st priority .. bios checks for boot code on a Disk in the CD drive, if that GOOD boot code is found, well bios hands of to that boot code;
NOW if there is no disk ( or bad boot code) in the CD, then bios looks at the next device in the boot priority list for boot code, and will hand off booting to that code.

Change in plans; Now you want to boot from the external USB, guess what you MUST do ? As there exist boot code on the hard disk(s), you MUST set the USB drive ahead of the internal hard disk in the boot priority.
In this situation,:
1st boot priority is CD
2nd Boot priority is USB
3rd Boot priority is the internal hard drive.

Turn on the system, bios goes checking -> IF there is a bootable disk in the CD drive bios quits looking and hands off to the booting code in the CD. Bios's job is done. Else ->
There is no disk on the cd: Bios does not find boot code in that 1st boot priority list, goes to the next in the list - here USB. And finds the boot code in the USB, and hands off -> job done; Else ->
There is no disk in the CD, no USB is plugged in so bios -> looks for cd boot code, does not find it, goes to next on the list - USB-, does not find boot code finally goes to hard drive; hands off to the boot code on the hard drive -> job done.

Do you get the picture ?
Now in boot time it takes a lot of time for bios to find some boot code some where, SO to decrease the boot time, one sets as that 1st boot priority what you want to boot from.
Whether it is the CD, you want to boot from
Whether it is the USB, you want to boot from
Whether it is the Hard drive(s), you want to boot from.


It is all in the priority that you set in bios as to the 1st booting device. Every bios has some means to set this priority.
[INDENT][INDENT]hope this helps
[/INDENT]
[/INDENT]


Okay. I just did exactly as you described with the boot order being:
1.) CDROM
2.) USB-HDD
3.) Hard Drive

I put my ear up to the CD Drive and found that it did not spin when the BIOS supposedly searched it.  The drive is a LG Blu-Ray reader/writer although it also can read/write CD's and DVD's.  I am wondering if the system is not recognizing the Blu-Ray player as a boot device.  For the USB I am wondering if possibly the BIOS is not reading from the slot that I stuck it into on the back of my computer.  I am wondering if maybe I need to install some third party software like the Wubi.exe in the .iso asks me to if I am having trouble booting.  The trouble is that the software fails to download every time.  Any suggestions would be appreciated, thank you.

---

### Post by Bashing-om on 2014-09-29
aebkea; Welp;

Let me say my experience. Award-Phoenix bios here and I can not boot from the DVDdrive , I must set in bios to boot the CD.
But to be equally honest I have not had the need to put a lot of effort into booting from the DVD drive.
IS "The drive is a LG Blu-Ray reader/writer" the only optical device installed ? If you have the CD drive installed, boot that CD drive rather than the blue-Ray device.

[INDENT][INDENT]bios can be
[INDENT][INDENT][INDENT]funny people
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by aebkea on 2014-09-29
> **Bashing-om said:**
> aebkea; Welp;

Let me say my experience. Award-Phoenix bios here and I can not boot from the DVDdrive , I must set in bios to boot the CD.
But to be equally honest I have not had the need to put a lot of effort into booting from the DVD drive.
IS "The drive is a LG Blu-Ray reader/writer" the only optical device installed ? If you have the CD drive installed, boot that CD drive rather than the blue-Ray device.
[INDENT][INDENT]bios can be[INDENT][INDENT][INDENT]funny people
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


I only have the LG Blu-Ray reader/writer installed.  It is the D: drive for me and Windows calls it a BD-ROM Drive.  I am also wondering if the .ios did not burn to the DVD correctly.  The immideately noticeable files on the disk are as follows:
Files Currently on Disc (14):
    .disk
    boot
    casper
    dists
    EFI
    install
    isolinux
    pics
    pool
    preseed
    autorun.inf
    md5sum.txt
    README.diskdefines
    wubi.exe
Files Ready To Be Written to the Disc (1):
    desktop.ini

---

### Post by Bashing-om on 2014-09-29
aebkea;
It is possible there is a bad burn.

Have you got access to another machine ? See if the disk boots in that alternate box and also:
verify the disk:
boot the liveDVD, soon as the bios screen clears, depress and hold the right -shift- key -> language screen, escape key to accept default -> boot options screen -> "check disk for defects".
For the USB try changing the ports , seems maybe the port and drive speeds not compatible ? 2.0 on the front panel, 3.0 on the back panel ?? And not known what speed the USB drive is. Maybe bios maps to different ports ?
//
Another thought, how old is this troublesome box ? - or stated better, how new ? Is UEFI and/or secure boot at play here ?

> 
I am wondering if maybe I need to install some third party software like the Wubi.exe in the .iso asks me to if I am having trouble booting. The trouble is that the software fails to download every time

please elaborate, "you" are not going to change that .iso. Once the machine tries to boot the liveDVD(USB) and fails, then one "might" resort to adding boot parameters to enable booting the kernel.

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by aebkea on 2014-09-29
> **Bashing-om said:**
> aebkea;
It is possible there is a bad burn.

Have you got access to another machine ? See if the disk boots in that alternate box and also:
verify the disk:
boot the liveDVD, soon as the bios screen clears, depress and hold the right -shift- key -> language screen, escape key to accept default -> boot options screen -> "check disk for defects".
For the USB try changing the ports , seems maybe the port and drive speeds not compatible ? 2.0 on the front panel, 3.0 on the back panel ?? And not known what speed the USB drive is. Maybe bios maps to different ports ?
//
Another thought, how old is this troublesome box ? - or stated better, how new ? Is UEFI and/or secure boot at play here ?


please elaborate, "you" are not going to change that .iso. Once the machine tries to boot the liveDVD(USB) and fails, then one "might" resort to adding boot parameters to enable booting the kernel.
[INDENT][INDENT]sometimes I do wonder
[/INDENT]
[/INDENT]


Ok, so I got the DVD to work on another computer and I checked for  faults and there are none there.  Once I moved the USB to a USB 2.0 then  it tried to boot from there but it said Boot Error.  I am wondering if  maybe I should try something other than USB-HDD and maybe the FDD, ZIP,  or CDROM varients might work.  Which do you think I should try?

---

### Post by aebkea on 2014-09-29
> **Bashing-om said:**
> aebkea;

Another thought, how old is this troublesome box ? - or stated better, how new ? Is UEFI and/or secure boot at play here ?



My computer is about 2 years old.  I don't think that UEFI or Secure Boot are in play.

---

### Post by Bashing-om on 2014-09-29
aebkea; OK,

In that case, take the disk and USB to another box. There see if they boot.

Fault isolation; is it the media, or the hardware ? IF bootable in another box, then the fault is hardware related. No boot in a known good machine, you can bet it is the media at fault.

[INDENT][INDENT]just my thought
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-09-30
Some newer systems require you to turn on the boot capability of external devices. And that may even be hidden under another menu or require you to set a password (never lose that one) to open windows to let you change those types of settings.

Only bootable flash drives will be shown.

On my older Gigabyte motherboard I had all the USB- type boot options and none worked. I was originally lost. Proved that flash drive was bootable by using it on laptop. I had left it plugged in and had two drives, so experimenting with booting second drive, there was my flash drive! Even though a USB device BIOS sees it as another hard drive.

---

### Post by aebkea on 2014-09-30
> **oldfred said:**
> Some newer systems require you to turn on the boot capability of external devices. And that may even be hidden under another menu or require you to set a password (never lose that one) to open windows to let you change those types of settings.

Only bootable flash drives will be shown.

On my older Gigabyte motherboard I had all the USB- type boot options and none worked. I was originally lost. Proved that flash drive was bootable by using it on laptop. I had left it plugged in and had two drives, so experimenting with booting second drive, there was my flash drive! Even though a USB device BIOS sees it as another hard drive.

Hello,
I still can't figure out how to boot with USB on my CPU although I figured out that my disk player was not called CD-ROM but was instead named with a seemingly random name like a serial number.  Once I punched that in Ubuntu booted right up.  I have another quick question though.  How much space should I allocate to the Ubuntu installation?  I have heard that 10 Gigabytes is the minimum but I want to know how much space I would need if I installed a lot of games with many assets onto Ubuntu.  Also, can I edit the partitioning post-installation?  Thank you.

---

### Post by Bashing-om on 2014-09-30
aebkea; Hey;

In for a penny, in for a pound, but
I can not give any additional advise on manipulating your bios settings for the usb drive .
As to space allocation for ubuntu, I would say 50 Gigs as a minimum, given what you want to do.
Better advise can be given if we know what there is to work with.
Boot the liveDVD to a terminal ( desk top, key combo ctl+alt+t will yield a terminal ) and post back the outputs of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
Which will relate your disk(s) specifications and partitioning.

[INDENT][INDENT]getting ready
[INDENT][INDENT][INDENT]getting set
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Vladlenin5000 on 2014-09-30
> **aebkea said:**
> Hello,
I still can't figure out how to boot with USB on my CPU although I figured out that my disk player was not called CD-ROM but was instead named with a seemingly random name like a serial number.  Once I punched that in Ubuntu booted right up.  I have another quick question though.  How much space should I allocate to the Ubuntu installation?  I have heard that 10 Gigabytes is the minimum but I want to know how much space I would need if I installed a lot of games with many assets onto Ubuntu.  Also, can I edit the partitioning post-installation?  Thank you.

So, in a nutshell the option was always there and you found out you've missed all the time after 2 pages and 15 posts... Well, I guess it could have been worse...
Note: Most BIOS/UEFI identify internal drives by their make/model: HT-DT-ST something is Hitachi-LG partnership (brandname: LG); TS-something is Toshiba-Samsung partnership (brandname: Samsung), etc.; some also identify external drives in the same fashion. Many old BIOS used only generic labels for external drives like  USB-FDD, USB-CDROM or USB-HDD.

Lots of games = lots of space => Allocate as much you as can afford.

---

