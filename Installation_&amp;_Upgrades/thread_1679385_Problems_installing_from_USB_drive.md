---
title: "Problems installing from USB drive"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by mikebot on 2011-01-31
HI, I am having problems installing Ubuntu netbook 10.10 from a USB drive.

I have a Lenovo ideapad S10-3 with Win 7 Starter.
I have tried two different USB drives, one is unidentifiable, the other is a Kingston.
I have used Pendrive and Unetbootin on both.
I have tried formatting the drives to FAT32 from both the Pendrive option and from Win7's default formatting software.
I downloaded the iso from the Ubuntu website torrent, and I did an md5 check to make sure that the file matched up.

When I boot from USB, the purple screen comes up briefly, and after two seconds changes to a black, terminal screen on which a bunch of text scrolls and then it eventually freezes.

When I click a button, the menus pop up, and when I click on either "install" or "run from usb drive," the same terminal thing happens.

Someone recommended that I try installing from that screen after changing the f6 options to nomodeset, noapci (I think), and acpi=off. (I cannot remember the exact lettering, but they were options on that f6 menu.) None of these changed the result.

With the Kingston, the line that it freezes on in the terminal is:
[6.548159] USB Mass Storage support registered.

EDIT: With both drives, when I use the Unetbootin install, the menu comes up, and when I click on either the 'run' or 'boot' options, the cursor in the bottom left of the screen keeps flashing but no progress. (No terminal-like screen with this one.)

It is different with the other drive.



Does anyone have any advice on how to proceed from here?

Thank you!

---

### Post by leeper69 on 2011-01-31
Have you checked out [www.pendrivelinux.com?](www.pendrivelinux.com?) I ran into a different problem after a friend made a multi boot pen drive for me and haven't found a way to fix it in Linux. the drive was formated using the free windowS software on linuxpendrive.com a flag was changed so the usb drive was seen as a floppy drive using there software my drive now reads as a hard drive with one partition.maby this will help to get a boot-able system on your computer.

---

### Post by mikebot on 2011-01-31
> **leeper69 said:**
> Have you checked out [www.pendrivelinux.com?](www.pendrivelinux.com?) I ran into a different problem after a friend made a multi boot pen drive for me and haven't found a way to fix it in Linux. the drive was formated using the free windowS software on linuxpendrive.com a flag was changed so the usb drive was seen as a floppy drive using there software my drive now reads as a hard drive with one partition.maby this will help to get a boot-able system on your computer.

I'm not sure I'm completely understanding... I tried installing it with the pendrive software (formatted with that software and also formatted independently), and both times the software runs when I boot from the drive, but when I select anything from the menu that opens (either to boot from the usb or to install from it), I get the terminal thing.

I can boot from it (when I go to the boot menu my computer sees it as a USB drive that is bootable).

---

### Post by leeper69 on 2011-01-31
Have you checked out [www.linuxpendrive.com?](www.linuxpendrive.com?) I ran into a different problem after a friend made a multi boot pen drive for me and haven't found a way to fix it in Linux. the drive was formated using the free windowS software on linuxpendrive.com a flag was changed so the usb drive was seen as a floppy drive using there software my drive now reads as a hard drive with one partition.I hope this will help to get a boot-able system on your computer.
I used a cd and installed Ubuntu 10.10 to the pen drive. boots fine. just be sure the usb drive is formated to fat 32 with one partition. now I have a boot-able drive with Ubuntu loaded on it. the software on the install disk will change the fat 32 to a ext4 partition and the usb drive is upgradeable to your liking.

---

### Post by mikebot on 2011-02-01
Bump... does anyone know another way I could install Ubuntu? Or does anyone know if these problems mean that the hardware of this computer is incompatible or something?

---

### Post by Carson5696 on 2011-02-01
Hello,
insert your usb into your computer and press ESC while turning it on. move using your arrow keys to USB device (most likely the second one) then you go on with booting up

The reason you have to press the ESC button is that it will load all the scripts because you were holding the ESC if you dont it just loads the boot scripts.

Remember this depends on your computer

---

### Post by mikebot on 2011-02-01
> **Carson5696 said:**
> Hello,
insert your usb into your computer and press ESC while turning it on. move using your arrow keys to USB device (most likely the second one) then you go on with booting up

The reason you have to press the ESC button is that it will load all the scripts because you were holding the ESC if you dont it just loads the boot scripts.

Remember this depends on your computer

So, I have to press f12 to get to the boot menu... are you telling me to press ESC and f12? Or once I am in the boot menu, hold ESC while selecting the USB drive?

---

### Post by Carson5696 on 2011-02-01
How old is your computer?

---

### Post by mikebot on 2011-02-01
> **Carson5696 said:**
> How old is your computer?

Lenovo ideapad S10-3... about 3 months old, but I haven't been using it... probably been used for 40 hours total.

---

### Post by Carson5696 on 2011-02-01
Ok, if you turn on your computer what is the first thing you see

---

### Post by Carson5696 on 2011-02-01
Is this your computer?

---

### Post by mikebot on 2011-02-01
> **Carson5696 said:**
> Is this your computer?

Yes... When I turn it on the first screen is the Lenovo screen (I can press f2 for the setup menu, and f12 for the boot menu). Then it just goes to the Windows loading screen and Windows login screen.

---

### Post by Carson5696 on 2011-02-01
press f2 then tell me what options you have

---

### Post by mikebot on 2011-02-01
> **Carson5696 said:**
> press f2 then tell me what options you have

IT's called "Phoenix SecureCore(tm) Setup Utility."

It has the options: Information, Configuration, Security, Boot, and Exit. (I think it's just normal BIOS.)

Under 'Boot,' you can only change the boot order...

---

### Post by Carson5696 on 2011-02-01
OK make the first one USB

---

### Post by mikebot on 2011-02-01
> **Carson5696 said:**
> OK make the first one USB

Booting from USB is not the problem... I have booted from a USB before and got the Ubuntu menu to appear. It's that when I try to do anything from there, it does not work.

---

### Post by Carson5696 on 2011-02-01
insert the usb and hold the ESC Only and choose USB it will work

---

### Post by mikebot on 2011-02-01
> **Carson5696 said:**
> insert the usb and hold the ESC Only and choose USB it will work

It didn't work... Again, the problem is not booting from the USB. It's that the options on the Ubuntu menu do not work.

---

### Post by Carson5696 on 2011-02-01
Ok

---

### Post by Carson5696 on 2011-02-01
Then re-download the iso

---

### Post by mikebot on 2011-02-01
> **Carson5696 said:**
> Then re-download the iso

I checked the iso (the md5 matches).

---

### Post by 0))) on 2011-02-01
Carson >> sorry but you dont seem to have read the OP's OP.
He has stated he already has MD5 summed the downloaded iso, and the problem is not that he dosent know how to change the boot order of his machine.

mikebot >> just to make double sure **i** haven't misread your OP as well, your attempting to install to your laptop **from** a USB device instead of using a CD/DVD, correct? 

You may want to try the ubuntu live usb tool, which is similar to the usb drive mode of unetbootin in that it creates a bootable usb device that can be used just like an install cd/dvd 

[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

Also this forum exists for unetbootin user problems, have a look and see if its any help

[http://reboot.pro/forum/79/]("http://reboot.pro/forum/79/")

And of course, you can always do it manually either by

[http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/]("http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/")

or the old favourite 

```
dd if=the.ubuntu.iso.your.using of=/dev/sda
```

Obviously change /dev/sda to whatever your usb device is listed as under fdisk -l. Although if you've only got access to a windows machine you'll need the win32 port of dd [http://www.chrysocome.net/dd](http://www.chrysocome.net/dd) 

and the syntax is more like

```
dd if=c:\temp\disc1.iso of=\\.\g:
```

At any rate i myself am trying to solve this as my workstation dosent have a cd drive, so ill post here anything i come across.
Hope this helps.

---

### Post by 0))) on 2011-02-01
Note - the link i gave for manually copying the ubuntu install image onto your usb drive is invalid for ubuntu versions 9.04+, you'll need to follow the instructions here for releases after 9.04

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Scroll down to the header "Create Bootable USB Manually" underneath "Alternative methods".

This works from a windows machine as well using GRUD4DoS, so if i cant find out what my unetbootin problem is i may well attempt this and let you know how i get on.

---

### Post by Carson5696 on 2011-02-01
> **mikebot said:**
> I checked the iso (the md5 matches).

OK Then something might be wrong with your computer

---

### Post by Carson5696 on 2011-02-01
Click in the first boot-up option and click enter then move down to USB if that does not work then I will find out how. :-D

---

### Post by mikebot on 2011-02-01
> **0))) said:**
> Carson >> sorry but you dont seem to have read the OP's OP.
He has stated he already has MD5 summed the downloaded iso, and the problem is not that he dosent know how to change the boot order of his machine.

mikebot >> just to make double sure **i** haven't misread your OP as well, your attempting to install to your laptop **from** a USB device instead of using a CD/DVD, correct? 

You may want to try the ubuntu live usb tool, which is similar to the usb drive mode of unetbootin in that it creates a bootable usb device that can be used just like an install cd/dvd 

[https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

Also this forum exists for unetbootin user problems, have a look and see if its any help

[http://reboot.pro/forum/79/]("http://reboot.pro/forum/79/")

And of course, you can always do it manually either by

[http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/]("http://www.teamteabag.com/2008/05/17/howto-easy-install-ubuntu-804-hardy-heron-or-most-other-distros-from-usb/")

or the old favourite 

```
dd if=the.ubuntu.iso.your.using of=/dev/sda
```

Obviously change /dev/sda to whatever your usb device is listed as under fdisk -l. Although if you've only got access to a windows machine you'll need the win32 port of dd [http://www.chrysocome.net/dd](http://www.chrysocome.net/dd) 

and the syntax is more like

```
dd if=c:\temp\disc1.iso of=\\.\g:
```

At any rate i myself am trying to solve this as my workstation dosent have a cd drive, so ill post here anything i come across.
Hope this helps.

Thank you very, very much... I am not currently home, so I cannot try any of these options yet, but I will report back here. I'm also going to try the same USB drive on my roommate's computer, because I am worried that this is a hardware problem.

> **Carson5696 said:**
> Click in the first boot-up option and click enter then move down to USB if that does not work then I will find out how. :-D

I'm not completely sure you're understanding my problem, but thank you for trying to help!

---

### Post by 0))) on 2011-02-02
My external USB bust last night so sadly iv been unable to test this more (bust as in, little bits of it went flying across the room - dont ask). 

Just for the record though my attempts have been with both fedora, debian and ubuntu iso's, using netbootin, although not pendrive linux, and a homebrew external USB drive made from a laptop drive and a USB caddy. 
I think we can rule out the USB drive being the source of the problem as mikebot attempted with 2 different drives. Same goes for the iso's integrity.
 
I'd like to imagine the problems have been due to using non-live media as the source, but reading unetbootin's wiki it seems like this is unlikely, as the unetbootin process copies the install files and then builds a new syslinux and installs it the MBR of the usb drive, making it bootable. 

Back to the drawing board i guess...

---

### Post by 0))) on 2011-02-02
Mikebot >> just looking over the pendrive linux site and saw some articles that may be useful for you troubleshooting your particular situation.

This url should be self explanatory...

[http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/](http://www.pendrivelinux.com/testing-your-system-for-usb-boot-compatibility/)

and if you machine **cant** boot from usb there is a work around...

[http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/](http://www.pendrivelinux.com/boot-from-usb-without-bios-support-via-plop-cd/)

I remember you saying the boot menu on your laptop at one point spat out "Pheonix securecore" well Phoenix do another BIOS product called award that pendrivelinux.com talk about here

[http://www.pendrivelinux.com/setting-usb-boot-options-phoenix-award-bios/#more-40](http://www.pendrivelinux.com/setting-usb-boot-options-phoenix-award-bios/#more-40)

Im looking at the phoenix securecore technical docs to see if it mentions anything to do with preventing usb boots, will post again if i find anything.

---

### Post by 0))) on 2011-02-02
Okay this may be abit out of date but its all i could find re: the phoenix bios route, it may be worth a try

> PHOENIX/AWARD BIOS
On my Shuttle XPC (SN85G4), the Phoenix/Award BIOS:

Go to "Advanced BIOS Features".
Go to the "1st Boot device" and set it to "USB-ZIP".

Tip from Daniel Butler: I have a Phoenix BIOS, Revision 6. After a lot of frustration, I found that you need to go to the Boot Order screen and select "Harddisk" and hit enter, giving you a list of IDE hard drives - for some reason, this BIOS prefers to call a USB device an IDE harddrive...but whatever. :)
And that's all. Reboot the PC (Exit the BIOS saving the changes) and see if it wants to boot from the thumbdrive.
Of the 5 PC's I tried, 4 where succesfull.

The web page i pulled this from 
( [http://www.weethet.nl/english/hardware_bootfromusbstick.php](http://www.weethet.nl/english/hardware_bootfromusbstick.php) ) talks about windows 2000/XP being current so it may be worthless info, but give it a go anyway.

---

### Post by IWantFroyo on 2011-02-02
I had something like this twice. The first time it stopped at something with the word "family" in it, the second time at "cannot mount devloop0 at blablabla squash.fs".
Can you please tell us what the text ended on? If it's the family thing, your laptop has the dreaded acpi problem, in which you'd edit the command line to include "pci=noacpi" or "acpi=off"
If it's the devloop0 squash.fs mount, you need to try making your usb from a working Ubuntu computer with startup disk, or try plugging in an older external cdrom.

---

### Post by mikebot on 2011-02-04
Yeah, I have not been able to try recently either. I kind of got upset and gave up for the time being. I have tried with 3 USBs now, 3 different computers (one of my own, two at my university), both desktop and UNR versions. I must be doing something wrong, but this is absurd. I've never had a problem doing this before. :(

---

