---
title: "Lenovo Z50-70: Unable to create an installer USB no matter what I do"
date: 2017-08-23
forum: Installation &amp; Upgrades
---

### Post by yourself2 on 2017-08-23
Hello everyone!

I've tried to make an installer for Ubuntu Gnome, Linux Mint and KDE Neon, but none of these work at all no matter what I do. I thought I'd post here as all of these are Ubuntu based. I have no access to the internet right now (except phone [no tethering])

I've tried these partition schemes -

1. GPT, then dd the ISO
2. MBR then dd
3. Tried copying the files on ext4 and fat32 on Linux (haven't tried Mac)
4. Convert the ISO to IMG then dd
5. Create an EFI partition and put the EFI folder from the ISO in it
6. Unetbootin. 

I tried all of these on Linux currently on my laptop and I tried these on a Mac.

When each process finishes, I try to boot it on the Mac. The flash drive doesn't appear in the boot menu.
I try to boot it on my laptop, it too doesn't appear.

It's not the USB drive as it worked before when I tried the Ubuntu 17.10 beta recently.
Before I boot, I make sure the flash drive is flagged "boot".

I have a MacBook Pro from 2011 (works with Linux, booted from the same ISO of UG I'm trying) and a Lenovo Z50-70 from 2014 (UEFI).

Also, all these ISOs work as I've used them on USBs before.

bump.

---

### Post by QIII on 2017-08-23
Hello!

Moved to Apple Hardware Users for a better fit.

---

### Post by &amp;KyT$0P# on 2017-08-23
What are the exact [FONT=Courier New]dd[/FONT] commands you used?

---

### Post by yourself2 on 2017-08-23
> **QIII said:**
> Hello!

Moved to Apple Hardware Users for a better fit.

Well, I am trying to install to my Lenovo but I guess Apple Hardware Users will do! :P

> **halogen2 said:**
> What are the exact [FONT=Courier New]dd[/FONT] commands you used?

I used -
sudo dd if=/Users/myuser/Downloads/ubuntugnome.iso of=/dev/disk1 bs=1m

---

### Post by QIII on 2017-08-23
Well....

My bad, then!  :)

---

### Post by yourself2 on 2017-08-23
> **QIII said:**
> Well....

My bad, then!  :)

Also, edited my post for halogen2
Edit: just noticed that edit, thanks!

---

### Post by QIII on 2017-08-23
Moved to Installation & Upgrades and re-titled.

---

### Post by yourself2 on 2017-08-23
Yup, thanks.

---

### Post by &amp;KyT$0P# on 2017-08-23
> **yourself2 said:**
> I used -
sudo dd if=/Users/myuser/Downloads/ubuntugnome.iso bs=1m
There's your problem, you didn't specify the [FONT=Courier New]of=/dev/sdX[/FONT] (replacing 'X' with the letter for your USB drive).  Does it work if you do that?

Refer to [FONT=Courier New]man dd[/FONT] for more info.

---

### Post by yourself2 on 2017-08-23
> **halogen2 said:**
> There's your problem, you didn't specify the [FONT=Courier New]of=/dev/sdX[/FONT] (replacing 'X' with the letter for your USB drive).  Does it work if you do that?

Refer to [FONT=Courier New]man dd[/FONT] for more info.



Sorry, I did, I just edited my post because I forgot to put it in there. That's definitely not the problem.
Also, when I tried the dd command on Linux, I did of=/dev/sdb

---

### Post by &amp;KyT$0P# on 2017-08-23
> **yourself2 said:**
> Before I boot, I make sure the flash drive is flagged "boot".
This might be the problem.  Which partition were you flagging?

Does it work if you only use [FONT=Courier New]dd[/FONT], just as you did, and leave it at that?

---

### Post by yourself2 on 2017-08-23
> **halogen2 said:**
> This might be the problem.  Which partition were you flagging?

Does it work if you only use [FONT=Courier New]dd[/FONT], just as you did, and leave it at that?

I flag the the partition that is the size of the ISO - 1.2gb for Neon, 1.4gb for Gnome and 
1.6gb for Mint. I'll try without touching them in Gparted now.

---

### Post by yourself2 on 2017-08-23
> **halogen2 said:**
> This might be the problem.  Which partition were you flagging?

Does it work if you only use [FONT=Courier New]dd[/FONT], just as you did, and leave it at that?

Alright - it doesn't work. It doesn't appear in the Lenovo or the Mac.

---

### Post by oldfred on 2017-08-23
dd erases everything else you do to flash drive.
It images a hybrid ISO to the flash drive & most systems boot that image.

Another alternative if just UEFI boot required.
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by yourself2 on 2017-08-23
> **oldfred said:**
> dd erases everything else you do to flash drive.
It images a hybrid ISO to the flash drive & most systems boot that image.

Another alternative if just UEFI boot required.
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

Hey, thanks.

I tried that, to no avail. Sorry!

---

### Post by oldfred on 2017-08-23
Are you getting error messages?
If UEFI secure boot is on, you almost always have to change a setting to allow or turn on boot from USB ports. Many require that even with UEFI secure boot off.

Some models also have additional settings in UEFI that must be changed.

 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)

---

### Post by yourself2 on 2017-08-23
> **oldfred said:**
> Are you getting error messages?
If UEFI secure boot is on, you almost always have to change a setting to allow or turn on boot from USB ports. Many require that even with UEFI secure boot off.

Some models also have additional settings in UEFI that must be changed.

 Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
 
It likely isn't that, but I'll check.

Edit: yeah, it's off. Even if it was on, at least the Mac would show it... it booted off the same USB and ISO combo. Unetbootin worked before, why wouldn't it now?

---

### Post by BenginM on 2017-08-23
ddin' the iso to usb never fails me , what i do is delete the usb partition in disk utility , create a new table with msdos format as FAT32 and create new partition ..  you may want to follow :


[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0)

---

### Post by yourself2 on 2017-08-24
> **BenginM said:**
> ddin' the iso to usb never fails me , what i do is delete the usb partition in disk utility , create a new table with msdos format as FAT32 and create new partition ..  you may want to follow :


[https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-macos#0)

Followed that. I don't have access to the internet until tonight so so can't download Etcher.

---

### Post by sudodus on 2017-08-24
I think something else is wrong. **dd** is powerful but dangerous. If I understand correctly, you are using dd in a correct way, and then it is a very reliable way to create a (live-only) usb boot drive.

I usually recommend [mkusb](https://help.ubuntu.com/community/mkusb), which wraps a safety belt around **dd**. You can try it, but I suspect that there is another problem in this case.

**Maybe the iso file is bad or not suitable for these computers.**

What is the file name? I think you need a 64-bit version. Look for 'amd64' in the file name. 'i386' indicates that it is a 32-bit version, which might be difficult to boot in UEFI mode.

Some releases (versions) might work better depending on the [age of the] hardware in the computers. The current versions of standard Ubuntu are

- 14.04.1 LTS
- 14.04.5 LTS
- 16.04.1 LTS (with the longest remaining support time until end of life)
- 16.04.2 LTS
- 16.04.3 LTS
- 17.04 LTS

See this link, [How to select the version and flavour of Ubuntu](https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865).

Some LTS versions (for example 16.04.**1** LTS but not 16.04.2 and 16.04.3) of standard Ubuntu have 5 years of support, but the corresponding community flavours (for example Ubuntu Gnome, that you are testing) have only 3 years support so Ubuntu Gnome 14.04.x are no longer supported. The other versions (like 17.04) have only 9 months of support.

Anyway it is a good idea to try another version and maybe another flavour of Ubuntu.

You should also ***check with md5sum that the download was good***. See this link, [help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

**It is possible that the USB pendrive is failing.**

Sometimes you get strange symptoms, that are difficult to interpret. It seems you can write to it for example with **dd**. But the pendrive is actually read-only, and not changed. See the following link and links from it,

[Can't format my usb drive. I have already tried with mkdosfs and gparted - Analysis of the problem](https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035)

**It is also possible that the computer settings must the changed to make them boot into a USB drive.**

This can often be done via a temporary hotkey or hotkey combination, different for different computers.

It should be possible to select a suitable setting via the UEFI/BIOS menus, that you can enter very early at boot (via a hotkey or hotkey combination).

You might find tips via the following links and links from them,

[help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[.../Installation/UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)
[.../Installation/Booting the Computer from USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

---

### Post by yourself2 on 2017-08-24
> **sudodus said:**
> I think something else is wrong. **dd** is powerful but dangerous. If I understand correctly, you are using dd in a correct way, and then it is a very reliable way to create a (live-only) usb boot drive.

I usually recommend [mkusb]("https://help.ubuntu.com/community/mkusb"), which wraps a safety belt around **dd**. You can try it, but I suspect that there is another problem in this case.

**Maybe the iso file is bad or not suitable for these computers.**

What is the file name? I think you need a 64-bit version. Look for 'amd64' in the file name. 'i386' indicates that it is a 32-bit version, which might be difficult to boot in UEFI mode.

Some releases (versions) might work better depending on the [age of the] hardware in the computers. The current versions of standard Ubuntu are

- 14.04.1 LTS
- 14.04.5 LTS
- 16.04.1 LTS (with the longest remaining support time until end of life)
- 16.04.2 LTS
- 16.04.3 LTS
- 17.04 LTS

See this link, [How to select the version and flavour of Ubuntu]("https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865").

Some LTS versions (for example 16.04.**1** LTS but not 16.04.2 and 16.04.3) of standard Ubuntu have 5 years of support, but the corresponding community flavours (for example Ubuntu Gnome, that you are testing) have only 3 years support so Ubuntu Gnome 14.04.x are no longer supported. The other versions (like 17.04) have only 9 months of support.

Anyway it is a good idea to try another version and maybe another flavour of Ubuntu.

You should also ***check with md5sum that the download was good***. See this link, [help.ubuntu.com/community/UbuntuHashes]("https://help.ubuntu.com/community/UbuntuHashes")

**It is possible that the USB pendrive is failing.**

Sometimes you get strange symptoms, that are difficult to interpret. It seems you can write to it for example with **dd**. But the pendrive is actually read-only, and not changed. See the following link and links from it,

[Can't format my usb drive. I have already tried with mkdosfs and gparted - Analysis of the problem]("https://askubuntu.com/questions/144852/cant-format-my-usb-drive-i-have-already-tried-with-mkdosfs-and-gparted/933035#933035")

**It is also possible that the computer settings must the changed to make them boot into a USB drive.**

This can often be done via a temporary hotkey or hotkey combination, different for different computers.

It should be possible to select a suitable setting via the UEFI/BIOS menus, that you can enter very early at boot (via a hotkey or hotkey combination).

You might find tips via the following links and links from them,

[help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")
[.../Installation/UEFI]("https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI")
[.../Installation/Booting the Computer from USB]("https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB")

Hey, sudodus!

1. Bad ISO.

They aren't bad, and I'm sure (though I've never done an md5 check) because I used these exact ones before on the same computers.

2. Bad USB

I have written to the USB, and have actually gotten "read only" errors twice when trying to edit them after writing at the beginning. After writing though, I checked in the other computer that the files were there, so this could be a problem. I can try with a new one tonight after my flight though.

3. UEFI settings

My settings are what they need to be - SB off, USB boot on. I have booted from USBs before and have never changed themz

---

### Post by oldfred on 2017-08-24
Have you updated UEFI to newest version from Lenovo? Many vendors have to make fixes for UEFI boot issues.
And if you update UEFI, it reverts to defaults, so you have to redo the changes you made to UEFI settings.

---

### Post by yourself2 on 2017-08-24
> **oldfred said:**
> Have you updated UEFI to newest version from Lenovo? Many vendors have to make fixes for UEFI boot issues.
And if you update UEFI, it reverts to defaults, so you have to redo the changes you made to UEFI settings.

Fully up to date and made sure settings were the same as before. I updated a year ago and the last update was in 2014..
Also, while on the flight, I attempted to erase the USB with the 'Overwrite with zeroes' option, then DDing the image. Didn't help.

---

### Post by yourself2 on 2017-08-25
Hello again.

I tried with a different USB (SanDisk Ultra 64gb USB3) and that didn't work with a SUSE Studio iso that I made yesterday (it works in VirtualBox though). I'm going to try the KDE image now.

I checked my BIOS settings, and these are the settings.

Secure Boot: Off
USB Boot: On
VT-d: On
Fast Boot: Off


Also, though I'm not sure if it matters, but my Nvidia graphics card is on (GeForce 840M). I have an Intel system (i7-4510U) if it matters, and it's currently running Mint 18.2. The Mac is an Early 2011 MacBook Pro running 10.9.5 Mavericks.

Edit: I'm going to reset the BIOS on my Lenovo and see what happens. The USB is definitely good, as I put KDE neon on it (unetbootin on the Mac) and attempted to boot from the Mac, and it works. I tried to boot on the Lenovo, and no dice (yet).

Edit 2: BIOS reset didn’t help. The flash drive still doesn’t appear in the boot menu of the Lenovo, but it does on the Mac. It’s running now, and I edited this post from it.

---

### Post by sudodus on 2017-08-25
If the Mac boot from the USB drive, it works, at least in that mode. Is the Mac booting in UEFI mode? You can check with the following command line

```
test -d /sys/firmware/efi && echo efi || echo bios
```

and there are more tips at the following link and links from it,

[help.ubuntu.com/community/Installation/FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

When you know which in which mode the Mac is booting, you can set the Lenovo to boot in the same mode (or in both modes) and keep trying with different settings (in the UEFI/BIOS menu system) but also try to boot via a temporary boot menu. I have a very old IBM Thinkpad and an old Lenovo laptop with Intel i3 CPU. Both are easy to boot via a temporary boot menu via **<F12>**.

When booting my Lenovo I get the following:

1. **"Press <F1> to BIOS setup"**

and at the **Startup menu** I can set

'UEFI/Legacy Boot'

and when set to 'Both' there is on the next line
'UEFI/Legacy Boot Priority' (which one to boot first, if both seem to work)

2. **"To interrupt normal startup, press the Enter button"**

Look for the corresponding hotkeys and menu items(maybe the same, maybe different.)

---

### Post by yourself2 on 2017-08-25
The command echoes back to me, 'efi'. Even in the boot menu, it shows the USB drive (on the Mac) as 'EFI Boot'. 

My Lenovo isn't an older laptop, it's from 2014, and came with Windows 8.1 Update. It doesn't have these messages at post. I press the 'Novo' button (next to the charging port) that is flush to the surface.
Pressing it while in the OS does nothing, but pressing it while the computer is off turns it on and shows a menu, with the following options -

Normal Startup
BIOS Setup
Boot Menu
OneClick Recovery

I go to the BIOS and I put these options (brackets will be if the boot mode is Legacy Support)

Boot Mode: UEFI (Legacy Support)
Boot Order (only with LS): UEFI First, Legacy Second

Boot Order:

EFI USB Device
ubuntu (SSHD-this-is-the-hard-drive-has-mint)
EFI Network
EFI CD/DVD

When I go the boot menu, I get three options, when the USB is plugged in.

ubuntu (SSHD-with-mint-on-it)
EFI Network IPv4
EFI Network IPv6

I have got some CDs I can try, which have 4GB storage on them...

---

### Post by sudodus on 2017-08-25
It looks like it should work to boot your Lenovo both via USB (EFI USB Device) and via EFI (CD/DVD).

It is worthwhile to burn a boot DVD with Ubuntu or an Ubuntu flavour, 4 GB is enough (the size of the Ubuntu iso files is between 1 and 2 GB ).

Maybe there is a problem with a hardware driver or some other thing, that causes problems between the Ubuntu based system and the computer. In order to test this, you can try other versions of Ubuntu and also other linux distros.

---

### Post by yourself2 on 2017-08-25
I'll burn a CD now, and I'll come back afterwards to see if it worked.

---

### Post by yourself2 on 2017-08-25
Okay, made the CD. It didn't appear at all.

Whelp dunno what's gonna happen.

Edit: Alright, update.

I made an openSUSE Tumbleweed UEFI installer (the official one) and tried to boot it on my Lenovo, and ofc it didn't appear. Tried booting it on the Mac, and it appeared as EFI Boot. Selected it, and it showed the SUSE boot menu. I didn't boot further because I don't want to install it. I'm pretty sure something's wrong with the computer. I hope I don't need to take it to repair because of some sort of corruption because I lost the reciept.. lol

---

### Post by sudodus on 2017-08-25
How did you make it? Which tool?

What happens when you insert the CD disk (I hope you mean DVD disk) *into the booted computer*? Do you see one big file, the iso file, or do you see a number of directories and files?

---

### Post by yourself2 on 2017-08-26
I made the DVD disk with Brasero. It booted on the Mac and appeared as 'EFI Boot'. It didn't appear on the laptop.

---

### Post by westie457 on 2017-08-26
Possibly a silly question. Are you trying to boot the usb stick using only the 'novo' button?

I have two Lenovo laptops here and found that booting a usb stick via the novo button would only work for a Lenovo Recovery USB (purchased Factory Restore and/or home made system restore stick).
All others have to be booted using the F12 button.

---

### Post by yourself2 on 2017-08-26
> **westie457 said:**
> Possibly a silly question. Are you trying to boot the usb stick using only the 'novo' button?

I have two Lenovo laptops here and found that booting a usb stick via the novo button would only work for a Lenovo Recovery USB (purchased Factory Restore and/or home made system restore stick).
All others have to be booted using the F12 button.

When I press the Novo button, there's an option for the boot menu, which I have always used when I reinstall my OS (around 100 times lol). There's no obvious reason for it not to work now... I havent ever changed my BIOS settings, and I put them back to the old settings I had after a BIOS update (still the most up to date) reset them a year ago. Since then I've reinstalled so many times.

---

### Post by sudodus on 2017-08-26
Maybe some hardware component has failed in the Lenovo. It seems to me that you have tried what has been working (and what **should** work now).

But let us hope that someone will chip in an suggest a method, that works for you to boot via either USB or DVD.

- Please try to get directly to the temporary boot menu via the hotkey <F12>

You could start by looking at the following alternatives.

- Some computers (but far from all of them) can boot via the built-in slot for memory cards (typically SD cards). You can use for example mkusb-dus to make a memory card bootable in the same way as you make a USB pendrive bootable.

- An installed system with Ubuntu is portable between computers, if you avoid proprietary drivers. So you can unplug the internal drive from your Lenovo laptop and connect it to another computer (externally or internally), and install Ubuntu into it. After that you can plug it back into the Lenovo. Chances are high, that it will work.

Yes, I know that this is a cumbersome workaround, but I have done it, and the installed systems have worked for me in computers, that are quite different (but of course PC computers with Intel or AMD processors). I have even made and uploaded compressed image files with such systems. (Today the main link is broken, but I think you can get a compressed image via the alternate link 'Download source 2'.)

See this link: [help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by yourself2 on 2017-08-26
Thanks, everyone for the help. There's probably some hardware problem, so wish me luck on finding that receipt.

The F12 (+ fn because of media keys) button takes me to the boot menu, but the options still don't show my USB or CD of openSUSE, KDE neon, Linux Mint or Ubuntu 17.10 beta.

My computer does have an SD card slot, and I could try that, though I don't think it would work.

I'll probably take out the hard drive from the Mac, install Ubuntu and then move that to my Lenovo PC.

I wish there was an upvote, or kudos button avaliable.

I'll also try asking on reddit (r/techsupport and r/lenovo) and on Lenovo's support forums.

---

### Post by sudodus on 2017-08-26
Good luck with the receipt and with your continued efforts to find a method that works :-)

---

