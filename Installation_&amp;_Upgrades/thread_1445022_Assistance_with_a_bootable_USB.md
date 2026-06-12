---
title: "Assistance with a bootable USB"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by akakingess on 2010-04-02
I hope that I don't offend anyone by posting what is probably a non-Ubuntu post, but as the subject states I am trying to get some form of Linux installed onto a bootable 2GB USB flash stick. I have tried Ubuntu/Mint and don't have enough room. I have downloaded and burned a copy of DSL (Damn Small Linux) but when I boot from the CD and attempt it it doesn't seem to work, so my questions are double/triple fold. Can I run the installer from the CD while in Ubuntu and if so how do I go about running the installer/get it started? Also, does anyone have experience with any other Linux OSs (bootable from USB of course, and if you do recommendations are definitely welcome? Those are the main issues at the table right now, and just so you know my 4 GB Flash Stick went out on me, so that is why I want to try to use the @ Gigger, obviously I know it would be much easier with many more choices had I still had the 4GB one working. Thanks in advance for any assistance/guidance/advice, etc. as all input is greatly appreciated. Also, sorry if this turns out to be a double post as I typed this out earlier, swore that I had hit the old "Submit New Thread" button, but couldn't see it within this forum, so I decided to try it again. ;)

---

### Post by garvinrick4 on 2010-04-02
Download a copy of ubuntu and burn it to a CD. 

boot off of CD and use the USB  start up disk creator under System/ Admin

On the bottom of the program page slide it over to the end for 2 gig of persistence,
and make your Usb stick.

I use a 2 gig one and have a nice little Live CD and Ubuntu system. 

can use up to 4 gig of persistence in program but 2 gig will do. 

Once done go to software sources and set it to never upgrade. (you will have no room)

---

### Post by akakingess on 2010-04-02
Sweet, I am going to try it now and let you know how it goes, thanx for the quick response!!!

---

### Post by Megaptera on 2010-04-02
Don't overlook this site dedicated to such projects:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by TChiOBi on 2010-04-02
you might also want to try: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
you can use your already downloaded .iso's or download new ones
also make sure you format the flash drive to fat32(in most cases works better this way) and the flash drive is marked/flaged bootable

under ubuntu: you could try with System > Administration > Disk Utility
or with gparted (sudo apt-get install gparted)

under windows, it's not enough to just format, need's to be bootable, try google~ing for an "HP tool fromat usb" (without quotes & and don't know if allowed links to other sites like those, but anyways), it will make it empty, formated, and flaged bootable, after wich you can use unetbootin for windows

hope this helps

---

### Post by akakingess on 2010-04-02
> **Megaptera said:**
> Don't overlook this site dedicated to such projects:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)


I have checked out that site, only to get pretty lost (that site is a little too busy for my tastes), but may have to visit it again as I am not having luck with going Ubuntu from USB. Even Mint claims there is not enough space, and DSL had even other issues. I am just going to have to invest in a larger USB Stick (which is what I was trying to avoid). Thanks for all of the input and please keep it coming, but I may have to wait til tomorrow for any more attempts, as it is getting late/early 4 AM, and I don't want to get so frustrated that I give up on the matter. It is not a matter of necessity rather than my thirst for knowledge and trying everything out (Ubuntu or not). Thanks again.

---

### Post by akakingess on 2010-04-02
> **TChiOBi said:**
> you might also want to try: [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
you can use your already downloaded .iso's or download new ones
also make sure you format the flash drive to fat32(in most cases works better this way) and the flash drive is marked/flaged bootable

under ubuntu: you could try with System > Administration > Disk Utility
or with gparted (sudo apt-get install gparted)

under windows, it's not enough to just format, need's to be bootable, try google~ing for an "HP tool fromat usb" (without quotes & and don't know if allowed links to other sites like those, but anyways), it will make it empty, formated, and flaged bootable, after wich you can use unetbootin for windows

hope this helps

Thank you for that tip, I am trying it as we speak, chose to try Linux Mint first, if that fails, then will move on to Damn Small Linux (since I am working with only a 2GB USB) and see where we go from there. I will let y'all know of any successes/failures and again, thanks for all the prompt responses and helpful advice, and I do mean all of you!!!

---

### Post by akakingess on 2010-04-02
Quick update before I crashed, using unetbootin, I thought everything went smoothly, but tried to boot off of the USB (which is an option and set up within the BIOS) it came up with a menu that would allow me to install, check memory, etc. I used a mint.iso image that I had downloaded as my source and it completed successfully, but can't seem to get it to boot into Linux, any more suggestions would be welcome and I will check out pendrivelinux again, but as of now, I think it's time to give what I have left of my brain some rest, hell, it's probably user error at this point, right :)  Thanks again to all of you that were quick to offer assistance, that is why I visit this forum everyday (it's actually one of my 3 home pages when I launch FireFox) so I love to see the family-like atmosphere, now it's time to get some sleep (that will now be my birthday present instead of the bootable USB OS, which is what I wanted to give myself. I know, but being married with 3 kids makes this pretty much my "life" so to speak. Thanks again, and I will see y'all on the flip side.

---

### Post by TChiOBi on 2010-04-03
> **akakingess said:**
> Quick update before I crashed, using unetbootin, I thought everything went smoothly, but tried to boot off of the USB (which is an option and set up within the BIOS) it came up with a menu that would allow me to install, check memory, etc. I used a mint.iso image that I had downloaded as my source and it completed successfully, but can't seem to get it to boot into Linux, any more suggestions would be welcome and I will check out pendrivelinux again, but as of now, I think it's time to give what I have left of my brain some rest, hell, it's probably user error at this point, right :)  Thanks again to all of you that were quick to offer assistance, that is why I visit this forum everyday (it's actually one of my 3 home pages when I launch FireFox) so I love to see the family-like atmosphere, now it's time to get some sleep (that will now be my birthday present instead of the bootable USB OS, which is what I wanted to give myself. I know, but being married with 3 kids makes this pretty much my "life" so to speak. Thanks again, and I will see y'all on the flip side.

since i have an usb flash drive of 4gb and before used a 1gb, both worked with unetbootin to set up my ubuntu's, i see no need to burn iso's to cd/dvd

i might have missunderstood all the above so i wil try explain what i did or how it works for me(my english is bad)

after puting iso with unetbootin on usb flash rebooted and started like this:
~while bios loading i press F9 to give me the options to boot from flash/floppy/cdrom/hdd
~choosing flash it will start loading boot saying: SYSLINUX[something i don't recall]boot:
~waiting few seconds: 2~5 so it loads up the unetbootin menu:
+Default (wich will use the iso's default boot, in Ubuntu 9.10, 10.04, Mint 8 will use the live cd option to load without changes on your pc)
+Help(loads up a console linux to help with...(this part i have no clue)
+OEM(this is for manufactures, if right word, but no clue what it actually does)
~i choose Default or let the 10seconds pass and it will load th live cd(in mint there's another 10s wait to automaticaly boot into live cd)
~after live cd loaded i choose install icon from desktop, follow the instructions that suits my pc needs and done

i'm new to all this asweel, but hope this helps

LE:
~mint did have slight more options but default did get me into live cd
~woked on usb flash 1GB too all 3 linux mention above

---

### Post by akakingess on 2010-04-03
> **TChiOBi said:**
> since i have an usb flash drive of 4gb and before used a 1gb, both worked with unetbootin to set up my ubuntu's, i see no need to burn iso's to cd/dvd

i might have missunderstood all the above so i wil try explain what i did or how it works for me(my english is bad)

after puting iso with unetbootin on usb flash rebooted and started like this:
~while bios loading i press F9 to give me the options to boot from flash/floppy/cdrom/hdd
~choosing flash it will start loading boot saying: SYSLINUX[something i don't recall]boot:
~waiting few seconds: 2~5 so it loads up the unetbootin menu:
+Default (wich will use the iso's default boot, in Ubuntu 9.10, 10.04, Mint 8 will use the live cd option to load without changes on your pc)
+Help(loads up a console linux to help with...(this part i have no clue)
+OEM(this is for manufactures, if right word, but no clue what it actually does)
~i choose Default or let the 10seconds pass and it will load th live cd(in mint there's another 10s wait to automaticaly boot into live cd)
~after live cd loaded i choose install icon from desktop, follow the instructions that suits my pc needs and done

i'm new to all this asweel, but hope this helps

LE:
~mint did have slight more options but default did get me into live cd
~woked on usb flash 1GB too all 3 linux mention above

OK, I just got back in from a long trip so I may be misunderstanding, I used unetbootin from within my normal Ubuntu and just chose the mint .iso that I had downloaded as the source, not actually from CD. Also, are you talking about using the USB to install Linux, or actually run it from there (which is what I am trying to do). Either way, I will try what you have stated and see if that works, but it will probably have to wait 'til tomorrow (Easter, yeah). Thanks again for all of your input.

---

### Post by techunit on 2010-04-04
> **Megaptera said:**
> Don't overlook this site dedicated to such projects:

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

Thank you for bringing this site up it is wonderful. I have been using it since 2008 never had a problem.

---

### Post by Megaptera on 2010-04-04
> **techunit said:**
> Thank you for bringing this site up it is wonderful. I have been using it since 2008 never had a problem.

You're welcome! I too have used it and find it works out of the box!!

---

