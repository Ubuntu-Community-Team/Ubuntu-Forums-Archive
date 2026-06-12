---
title: "Cannot boot/install. ACPI issues. Also Nvidia graphics card issues."
date: 2014-02-07
forum: Installation &amp; Upgrades
---

### Post by Oddzball on 2014-02-07
Welp, after 2 days of trying to get Ubuntu to even boot form a live cd so i can install it, I am kind of at my wits end.

I have 2 issues really. (Well 3, the third being I have pretty much zero/minimum Linux experience)

First, when I get to the screen as the live cd first boots up, i choose to boot ubuntu. If I don't use nomodeset under f6, I get a "Input not supported" message on my led display.

So setting nomodeset allows me to get past that point, but then I run into another problem. While booting into ubuntu(Or sometimes, right AFTER it finishes booting) my computer will just hard shutdown/reset itself.

I found that using acpi=off allows me to boot, and not have things crash (Though for some reason the graphics look all funny/messed up).

So then I'm FINALLY in the Ubuntu live cd environment.

But here is the issue. Remember, I know pretty much nothing about Linux, the terminal stuff or otherwise. (Hard to learn when I cant get the thing installed)

I want to now choose that Install Ubuntu option. I'm concerned, if I do that, do i still get to set the nomodeset and acpi-off when linux boots? Is there some kind of "Linux start-up window" like windows has that I can set options before booting so that I dont waste my time and then watch it try to boot, get "Input not supported" and then hard crash my computer?


Second. Obviously, something needs to be fixed for the having to use nomodeset. It isn't recognizing my graphics card, or I need to somehow install drivers? Why is it I cant just boot up like normal? Obviously its some kind of weird resolution/hertz issue that ubuntu is trying to display in but how do I fix that? I saw somewhere there is something like nvida(Or noveu).modeset=0 that you can try, but I don't understand that... and again, am i going to have to put a bunch of special commands in EVERY time I want to boot my computer?


The second issue is acpi=off. Just like having to use nomodeset or whatever, this is obviously a work around to get the system to boot, but how do I FIX this? having acpi disabled probably causes a lot of problems. Again, I read somewhere that pci=noacpi will also solve my problem, but what problems does that create? how do i fix it? How do I make it so(assuming i cant fix it) it does this command automatically, along with modeset, so I don't have to type in some special command every time I want to boot linux?

For my computer I have the following hardware;

i5k2500

EVGA 770 GTX

EVGA Z68 SLI Motherboard

OCZ SSD harddrive

Secondary harddrive(Forget brand)

Both harddrives are SATA

ALSO, yes I ran memtest, my Ram is all fine.


Im kind of at my wits end after three solid days(for like 10 hours each day) trying to get this to work. I really, really want to get away from Windows, but Linux sure isn't making it easy for me when it's this difficult to get it to even boot.

So, can someone please help me figure this out?

---

### Post by oldfred on 2014-02-07
Do you have dual video? Since Intel chip also has video mode?

With nVidia you have to use nomodeset and then install nVidia drivers from System Settings.
If using Intel different boot parameters are usually required.

Are you booting in UEFI or BIOS boot mode? If adding nomodeset with f6 then it is BIOS. Is that what you want?

       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

 Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

Even if installing in BIOS mode, I still suggest gpt partitioning. But you have to do that in advance and Windows only boots from gpt with UEFI, so you may want MBR(msdos) if dual booting with Windows.


 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

If you find that you permanently need boot parameters you can add them to grub.


      
 sudo nano /etc/default/grub
# or
gksu gedit /etc/default/grub
# then 
sudo update-grub


 GRUB_CMD_LINUX_DEFAULT="quiet splash"

> 
[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
[/LIST]
        o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 

---

### Post by sudodus on 2014-02-07
> **Oddzball said:**
> 
First, when I get to the screen as the live cd first boots up, i choose to boot ubuntu. If I don't use nomodeset under f6, I get a "Input not supported" message on my led display.

After installation, you can also use boot options, but then you add them, first for trial and error into the grub menu (near quiet splash), then when you know what you need, you add them into the file **/etc/default/grub** according to

[URL="https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2"]https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2
[/URL]
and then make it active by running the command

```
sudo update-grub
```
> 
So setting nomodeset allows me to get past that point, but then I run into another problem. While booting into ubuntu(Or sometimes, right AFTER it finishes booting) my computer will just hard shutdown/reset itself.

I found that using acpi=off allows me to boot, and not have things crash (Though for some reason the graphics look all funny/messed up).

So then I'm FINALLY in the Ubuntu live cd environment.

But here is the issue. Remember, I know pretty much nothing about Linux, the terminal stuff or otherwise. (Hard to learn when I cant get the thing installed)

I want to now choose that Install Ubuntu option. I'm concerned, if I do that, do i still get to set the nomodeset and acpi-off when linux boots? Is there some kind of "Linux start-up window" like windows has that I can set options before booting so that I dont waste my time and then watch it try to boot, get "Input not supported" and then hard crash my computer?

Yes, you need the boot options, at least until you have install a proprietary nvidia graphics driver. Are you sure that you have an nvidia graphics chip/card?
> 
Second. Obviously, something needs to be fixed for the having to use nomodeset. It isn't recognizing my graphics card, or I need to somehow install drivers? Why is it I cant just boot up like normal? Obviously its some kind of weird resolution/hertz issue that ubuntu is trying to display in but how do I fix that? I saw somewhere there is something like nvida(Or noveu).modeset=0 that you can try, but I don't understand that... and again, am i going to have to put a bunch of special commands in EVERY time I want to boot my computer?

Some graphics chips/cards do not work with the free software. But only you have found something that works it can be installed and stay so that it will be used (forever or until you uninstall it).
> 
The second issue is acpi=off. Just like having to use nomodeset or whatever, this is obviously a work around to get the system to boot, but how do I FIX this? having acpi disabled probably causes a lot of problems. Again, I read somewhere that pci=noacpi will also solve my problem, but what problems does that create? how do i fix it? How do I make it so(assuming i cant fix it) it does this command automatically, along with modeset, so I don't have to type in some special command every time I want to boot linux?

I don't know any details about acpi=off. I hope someone else will chip in an explain it for us.
> 
For my computer I have the following hardware;

i5k2500

EVGA 770 GTX

EVGA Z68 SLI Motherboard

OCZ SSD harddrive

Secondary harddrive(Forget brand)

Both harddrives are SATA

ALSO, yes I ran memtest, my Ram is all fine.


Im kind of at my wits end after three solid days(for like 10 hours each day) trying to get this to work. I really, really want to get away from Windows, but Linux sure isn't making it easy for me when it's this difficult to get it to even boot.

So, can someone please help me figure this out?

You can try installing a proprietary driver like this (in text mode or in a terminal window)
```

sudo apt-get install nvidia-current
```

There are also other nvidia drivers that you can try if this one won't work. Reboot for the computer to start using the new driver.

Another route you can try is another version of Ubuntu. Which version are you testing now? 12.04 LTS, 13.10?

---

### Post by Oddzball on 2014-02-07
[COLOR=#ff0000]**Do you have dual video? Since Intel chip also has video mode?**[/COLOR]

No, there is no integrated video on my MB.(I assume this is what you mean by Dual video)

[COLOR=#ff0000][B]With nVidia you have to use nomodeset and then install nVidia drivers from System Settings.
If using Intel different boot parameters are usually required.[/B][/COLOR]

Is there a good guide for how to install the drivers. My only experience, is (On windows) going to nvidia site, downloading the drivers, and running the installer with a clean install.

**[COLOR=#ff0000]Are you booting in UEFI or BIOS boot mode? If adding nomodeset with f6 then it is BIOS. Is that what you want?[/COLOR]**

I guess I dont understand this. I KNOW my motherboard is a UEFI bios. How do I make Ubuntu, when i first put in the install cd, boot into UEFI mode?




[COLOR=#ff0000][B]
If you find that you permanently need boot parameters you can add them to grub.


      
 sudo nano /etc/default/grub
# or
gksu gedit /etc/default/grub
# then 
sudo update-grub


 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[/B][/COLOR]This is exactly how to type this in the terminal?[COLOR=#ff0000][/COLOR][COLOR=#000000]
Thanks for the info, I will start reading that atm...[/COLOR][COLOR=#ff0000][/COLOR]**[COLOR=#000000][/COLOR]**

---

### Post by sudodus on 2014-02-07
```
GRUB_CMD_LINUX_DEFAULT="quiet splash nomodeset acpi=off"
```
or
```
GRUB_CMD_LINUX_DEFAULT="nomodeset acpi=off"
```
to get more information during booting, 

and then
```

sudo update-grub
``` and reboot

---

### Post by sudodus on 2014-02-07
Do you intend to dual boot with Windows, or do you intend to overwrite Windows and have only Ubuntu?

Anyway, before installing anything, ***backup*** at least your personal files. It is also a good idea to make a recovery disk or an complete image of the Windows system (for example with Clonezilla). Editing partitions is risky. You may change your mind (if overwriting Windows), so a complete image might be a good option.

---

### Post by Oddzball on 2014-02-07
> **sudodus said:**
> Do you intend to dual boot with Windows, or do you intend to overwrite Windows and have only Ubuntu?

Anyway, before installing anything, ***backup*** at least your personal files. It is also a good idea to make a recovery disk or an complete image of the Windows system (for example with Clonezilla). Editing partitions is risky. You may change your mind (if overwriting Windows), so a complete image might be a good option.

Thanks for all the help guys. Ill go through all this over the weekend.

I plan to use a livecd of clonezilla to backup everything, then dual boot with Windows and Linux. Mostly I want to keep Windows around for gaming purposes.

Also, I still dont understand this;


**[COLOR=#ff0000]Are you booting in UEFI or BIOS boot mode? If adding nomodeset with f6 then it is BIOS. Is that what you want?[/COLOR]**

I guess I dont understand this. I KNOW my motherboard is a UEFI bios.  How do I make Ubuntu, when i first put in the install cd, boot into UEFI  mode?

How do I choose to boot in UEFI or Bios mode with linux?

---

### Post by oldfred on 2014-02-07
Both Windows and Ubuntu install in the same mode as you boot installer in from UEFI menu. 

So from UEFI menu you should have two entries for flash drive, one UEFI and one BIOS, but ofthen they are not clear descriptions.

Best not to use drivers directly from nVidia or a ppa which may only be required if you have a very new video card and need the very newest drivers. Ubuntu is now better and offers pretty current nVidia drivers thru repository. And do not attempt to install from nVidia, ppa and System settings without first purging as they conflict.

You can install from command line several different versions or from System settings. Older versions of Ubuntu had Other drivers icon, and newer versions have Drivers as a tab in Other Software or (something). If it offers legacy nVidia drivers just do not install those. 

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

 Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot. required for UEFI & grub bug fixes
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

