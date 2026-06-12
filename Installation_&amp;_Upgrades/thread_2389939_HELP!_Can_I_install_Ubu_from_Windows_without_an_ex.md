---
title: "HELP! Can I install Ubu from Windows without an external boot drive?"
date: 2018-04-23
forum: Installation &amp; Upgrades
---

### Post by Mugsy323 on 2018-04-23
**I screwed up really bad.** I need to perform a full install of Ubuntu onto my (Win10) tablet, but it must all be done from the internal drive b/c **I don't have access to my USB ports!** I don't care if I have to reformat and wipe everything. Can it be done?

The long story:

I was trying to figure out how to get my tablet to boot from a USB Flashdrive by making changes to the BIOS (changing the boot order didn't work) and inadvertently disabled my USB ports (including access to my keyboard, so I can't undo my changes or perform a reset.) And "yes", I've tried using the buttons on the tablet. Let's not go down that road. Just trust me.

Everything else works fine. I can boot into Windows and run programs as usual (it's a touch-screen tablet, so I can move the mouse with my finger and type using the on-screen keyboard.)

I did some research and it's supposedly possible to [**reset the BIOS from Linux**]("https://askubuntu.com/questions/538714/reset-bios-using-ubuntu"). I pray that's true b/c it's my last hope at getting my USB ports back. So I'm thinking if I can just install Ubuntu, I can execute the command to reset my BIOS back to its defaults, giving me back my USB ports & keyboard.

So if there's a way to perform a total install of Ubuntu without the need of an external drive (maybe by partitioning the existing C: drive), let me know. I'm desperate.

---

### Post by yancek on 2018-04-23
You might be able to do a 'frugal' install of Ubuntu to your windows drive by following the instructions at the unetbootin site below.  YOu would first obviously have to download the windows version of unetbootin to use.  I'm not sure if it will work with UEFI but then I don't know if you are using UEFI.  Booting an installed Linux system from the windows bootloader is a very convoluted process at best.  I'm not sure if the windows bootloader (BCD) can even boot directly a windows iso file much less Linux.  Good luck!

 [https://sourceforge.net/p/unetbootin/wiki/installmodes/](https://sourceforge.net/p/unetbootin/wiki/installmodes/)

---

### Post by oldfred on 2018-04-23
Only some settings can be reset from any operating system.
With older BIOS, no settings could be changed.
But most of the settings that can be changed are boot order, Secure boot on/off(maybe) and just a few others. 
If you reinstall UEFI from vendor that resets most settings to defaults. Have you tried updating UEFI. That often can be done from Windows.

---

### Post by Mugsy323 on 2018-04-24
> **yancek said:**
> You might be able to do a 'frugal' install of Ubuntu to your windows drive

Thanks for the reply. This looks promising. I do have a couple of concerns though:

1) I forgot to ask if Ubuntu even supports touch-screens? I certainly don't want to go from the frying pan into the fire, going from an OS with only a touch interface to one with no input at all. :o

2) Would such an install still give me low-level access to the bios or would it be running "on top of" Windows (both running simultaneously) like a VM, thus preventing me from making the needed changes?

Thx.

---

### Post by Mugsy323 on 2018-04-24
> **oldfred said:**
> Only some settings can be reset from any operating system.
With older BIOS, no settings could be changed.
But most of the settings that can be changed are boot order, Secure boot on/off(maybe) and just a few others. 
If you reinstall UEFI from vendor that resets most settings to defaults. Have you tried updating UEFI. That often can be done from Windows.

Thx for the reply. I'm about 90% sure it's a UEFI bios. The tablet is only 1 year old and runs Windows 10, and I seem to remember seeing some mention of UEFI somewhere.

But I was under the impression a UEFI bios was GUI based with mouse support. This tablet (an "Insignia" from Best Buy) has the familiar "Text" based bios ("American Megatrends") menus.

Best Buy has about as much online support for their computers as a K-Mart. A single driver download (and the manual), nothing as specific as a UEFI update. I looked for such a bios update that could be performed from Windows, but found nothing. :(

Do you know if the bios can be reset back to it's default state via the method described at the link I provided (using "modprobe nvram")?

If so, I'm wondering if the Linux command could be compiled to a DOS exe that could be executed from Windows Safe Mode (with no need to try and install Linux w/o an external boot drive)?

No bios should allow you to do something so dumb w/o a way to undo it. Not even a reset button on the tablet! Even opening it up to try and short the FlashRAM didn't work (and the battery is soldiered directly to the MoBo). What a nightmare.

---

### Post by oldfred on 2018-04-24
What brand/model tablet? (more to know what not to get).

I do not think modprobe modifies UEFI.

> modprobe - Add and remove modules from the Linux Kernel


This can change boot order in UEFI. But not anything else. And does not work on some systems.
> efibootmgr is a userspace application used to modify the Intel Extensi&#8208;
       ble Firmware Interface (EFI) Boot Manager.

You may be able to use an efi shell program. But there are Windows versions also.
A very early link on efi shell.
 [http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/) 

So then search on efi shell and many others.
[https://www.techadvisor.co.uk/forum/helproom-1/helpinstall-windows-internal-efi-shell-4620108/](https://www.techadvisor.co.uk/forum/helproom-1/helpinstall-windows-internal-efi-shell-4620108/)
[https://superuser.com/questions/1246989/getting-out-of-the-efi-shell-on-acer-windows-10-tablet-with-external-keyboard-no?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://superuser.com/questions/1246989/getting-out-of-the-efi-shell-on-acer-windows-10-tablet-with-external-keyboard-no?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)

---

### Post by Mugsy323 on 2018-04-24
> **oldfred said:**
> What brand/model tablet? (more to know what not to get).

I do not think modprobe modifies UEFI.

This can change boot order in UEFI. But not anything else. And does not work on some systems.

You may be able to use an efi shell program. But there are Windows versions also.
A very early link on efi shell.
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

Thx for the reply.

:frown: This tablet actually has an EFI Shell, but to get to it, you must change the boot order in bios.  ](*,) Wouldn't help me anyway since I couldn't type w/o a keyboard. :-/

I don't know where to find a copy I can run from Windows (even Safe Mode) or change the boot order from Windows so I could access it (of course, if it didn't work, I wouldn't be able to get back into Windows, leaving me even more screwed than I am now.)

If I enter BIOS, there is some helpful info on the "Main" menu:

BIOS: American Megatrends 5.011 (Aptio)
UEFI 2.4; PI 1.3 (I don't know what "PI" is.)
Build date: 09/01/2016
Intel GOP Driver: 8.0.1033

I found a utility on the "American Megatrends" website that *looks* like it might be helpful:

["AMI Firmware Update" utility]("https://ami.com/en/products/bios-uefi-tools-and-utilities/bios-uefi-utilities/")

It includes both a CLI version and a GUI version, but I'm not seeing anything in the ReadMe specific to clearing the BIOS (I do see switches for "Program Main BIOS" & "Program NVRAM", but no details on what they do.)

Since it was asked, this is an "Insignia (Best Buy's home brand) Flex 11.6" tablet". 1.44GHz, 2MB, 32bit Win10 (even though it's a 64bit cpu) with a USB 3.0 Type-C port (and two USB 2.0 ports via included detachable keyboard).

Everything you need EXCEPT a way to reset the BIOS. :D

PS: Does the info [**here**]("https://forums.linuxmint.com/viewtopic.php?t=226363#p1194543") help me?

---

### Post by oldfred on 2018-04-24
It looks like the manual only has erase drive as reset?
[https://files.bbystatic.com/xQniaxSNp%2Ff%2Fz2sC%2BT8NAA%3D%3D/NS-P11W7100_16-0363_MAN_V1_Final_lr.pdf](https://files.bbystatic.com/xQniaxSNp%2Ff%2Fz2sC%2BT8NAA%3D%3D/NS-P11W7100_16-0363_MAN_V1_Final_lr.pdf)

Same tablet, works but no details.
[https://ubuntuforums.org/showthread.php?t=2340852](https://ubuntuforums.org/showthread.php?t=2340852)

---

### Post by Mugsy323 on 2018-04-25
I just had a brief scare. #-o

I took a chance trying to install Ubu to a D: partition knowing there was a chance I might not be able to get back into Windows, and sure enough, when I rebooted, the installation failed, but fortunately, when I rebooted again, It went straight to loading Windows.

My steps:

I backed up my C: drive (moving the backup to my desktop PC over the network), uninstalled/deleted as many unnecessary files off the tablet's (32gb) drive to create as much free space as possible,, shrunk the C: partition as much as possible, and created a 7GB D: partition.

I then tried to use "**[WUBI]("https://github.com/hakuna-m/wubiuefi/releases")**" to install Ubuntu to the D: drive (praying for a dual-boot setup after some reassurance I could navigate the boot menu using the buttons on my tablet.)

I ran WUBI and after a few seconds, told me to reboot (fearfully, I did.) On reboot, it displayed "Installing Ubuntu" but then gave me an error seconds later that it could not find the "installation.iso" (it's there, but on the D: partition.)

What other Windows apps exist to perform an auto-install of Ubuntu? Or maybe someone knows anything helpful about Wubi? TIA

*ADDENDUM: Just learned WUBI does not include Grub, so it boots into Windows by default (which saved me). But the only way to get into Linux using it is to hit F2 on boot, so even if WUBI had worked, I would not have been able to access Ubuntu.* :(

---

### Post by oldfred on 2018-04-25
Wubi has not been supported since 12.04. It does not work (or did not) with UEFI & gpt partitioning, only BIOS/MBR. 
Some third party users have made changes so it may work, but not standard version. I thought Ubuntu finally stopped including it in the ISO.

---

### Post by coffeefiend on 2018-04-25
This may be a stupid question for me to ask, but I really don't know  much of anything about tablets as I don't own one and never have, so  please excuse me if it is. But is there a factory reset function on  tablets? Even if there is, I'm not sure it will fix your issue. Just  thinking out loud, really.

---

### Post by Mugsy323 on 2018-04-25
> **oldfred said:**
> Wubi has not been supported since 12.04. It does not work (or did not) with UEFI & gpt partitioning, only BIOS/MBR. 
Some third party users have made changes so it may work, but not standard version. I thought Ubuntu finally stopped including it in the ISO.

Correct. The link to WUBI for Ubuntu 18 states all that.

---

### Post by Mugsy323 on 2018-04-25
> **coffeefiend said:**
> This may be a stupid question for me to ask, but I really don't know  much of anything about tablets as I don't own one and never have, so  please excuse me if it is. But is there a factory reset function on  tablets? Even if there is, I'm not sure it will fix your issue. Just  thinking out loud, really.

<LOL> No. I wouldn't be going through this hell if there was.

I even took my tablet to "FixURGadget" and paid them $53 with instructions on how to *short* the WinBond FlashRAM chip to clear the BIOS, but it didn't work.

I was trying to get my tablet to boot from USB (changing the boot order didn't work) and unwittingly disabled the XHCI controller (which I didn't realize controls the USB ports AND Bluetooth), disabling the detachable keyboard. So even though I can get into the BIOS at startup (hitting Volume Up & Power buttons at the same time), there is no way to get past the first ("Main") menu to reenable the XHCI controller or reset/reload the BIOS defaults (which are on later menus.)

Using the Volume buttons, I can move the highlight/focus Up/Down, but not Left/Right. The Power button acts as "Enter". I've tried every combination of keys, but nothing else works and there are no other buttons on the tablet. The touch-screen does not work in BIOS.

So my only hope is to reset the BIOS using software. I can't find a way to do this from Windows, but supposedly it can be done from Linux.

---

### Post by oldfred on 2018-04-25
Are you able to unplug drive or is it soldered in?
My desktop system totally locked up after trying to boot SSD with UEFI & 18.04 with USB to SATA conversion plug.
I tried all the suggestions I make to others on cold boot (full power down), jumpering pins on motherboard. But unplugging main internal boot drive caused it to reset to defaults and start booting again.

---

### Post by Mugsy323 on 2018-04-26
> **oldfred said:**
> Are you able to unplug drive or is it soldered in? [...] unplugging main internal boot drive caused it to reset to defaults and start booting again.

Interesting information. Unfortunately, they soldiered in every damn thing in this tablet (the "drive" it uses as storage are just chips on the MoBo.)

---

### Post by Mugsy323 on 2018-04-26
Okay, I'm a *little* closer to getting Linux installed.

Following **[these]("https://askubuntu.com/a/642253")** instructions, I used "UNetbootIn v6.57" to add a Boot Menu at startup. The Boot Menu it creates uses the Windows core, creating a menu that looks like the "Windows Troubleshooter" **with touchscreen support** prompting me to choose either "Windows 10" or "UNetbootIn"... the latter of which is *supposed to* load the Ubuntu iso image UNetbootIn extracted when run.

Unfortunately, the last step failed, just like WUBI, telling me it "could not find the disk image".

If I can figure out how to fix that, it *should* load the LiveCD, from which I could conceivably execute the "Modprobe" command w/o doing a full install of Ubuntu (just now.)

---

### Post by humanx on 2018-04-26
Have you tried using your Win10 Repair and Restore disk (or usb)?  You did create one when you bought that Win10 computer, right?

---

### Post by Mugsy323 on 2018-04-26
> **humanx said:**
> Have you tried using your Win10 Repair and Restore disk (or usb)?  You did create one when you bought that Win10 computer, right?

This isn't a Windows issue. Windows is fine.

And how would one use a "Repair Restore Disk (or USB)" with no external drive capability?

---

### Post by Mugsy323 on 2018-04-27
Okay, slight correction on my latest failed attempt...

The error I get after attempting to use "Unetbootin" is "*Windows* Boot Loader not found", not the Ubu iso. A search online shows this to be a known issue running Unetbootin on a device with UEFI bios, and the "fix" is to "go into BIOS and switch it to 'Legacy Mode'."

Well, if I could do that, I wouldn't be in this mess. :lolflag:

So, another "UEFI-friendly" method is needed.

---

### Post by Mugsy323 on 2018-04-27
I spoke to the tech that I hired to try to reset the bios, and he did more than I thought, including desoldering the battery from the MoBo, which *should* have cleared the bios but didn't.

He says "the chip is hard locked from the factory against this kind of 'tampering'."

I'm not sure what "hard locked" means, and now I'm wondering if I'm spinning my wheels trying to do this from Linux. :(

---

### Post by Mugsy323 on 2018-05-05
Final update for anyone who was following this thread.

I had to give up. I tried every trick in the book. Nothing worked. :(

On my last update, I was trying to find a way to install Ubuntu so that I might issue a BIOS reset command from the Linux terminal. But Windows-10 makes installing additional OS's difficult (so does the UEFI Bios), but I eventually found WubiUEFI... a "UEFI compatible" version of "Wubi" (a popular old program that installed other OS and a Boot Menu using Windows that no longer worked on computers with a UEFI Bios).

Long story short, "WubiUEFI" didn't work. On reboot, it reports it "can't find" the linux iso, so there's no OS to install.

But it gets worse. "WubiUEFI" relies on "rEFInd"... a third-party (fourth party?) Boot Loader that doesn't support touch screens (which I did not know at the time). With a missing OS as the first choice and no way to move the cursor right to select/boot Windows, I can't get past that menu. So now I have NO working OS! ](*,)

So, left with no other choice, I opened the tablet up. Based on [some photos]("https://yadi.sk/a/tKMmaLO7vAZ83/57d98500f12ea7555ca83140") I found online, you *should* be able to reset the Bios by shorting a single pin on the Winbond FlashRAM chip, but that too didn't work. I obtained the spec sheet and it mentions a "/Reset" pin, but shorting that didn't work either. I tried shorting the pins before, during and after powering on, but nothing made any difference.

I decided to try again to disconnect the batteries in hopes of clearing the Cmos, this time attempting to turn the tablet On 4-Times in hopes of draining any capacitors or residual charge then letting it sit for an hour before reconnecting the power, but despite all that, the old Bios settings were STILL there.

That made me wonder if it was reading the settings from the built-in SSD, so I disconnected it yet the Bios settings are STILL loading. :confused:

So that's it. I can't think of anything else. I will NEVER buy another tablet without a reset button (or w/o a touch-screen bios.) Anyone need an 11.6" lighted serving tray. :(

---

