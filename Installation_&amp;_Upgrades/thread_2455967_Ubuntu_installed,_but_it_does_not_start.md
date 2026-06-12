---
title: "Ubuntu installed, but it does not start"
date: 2020-12-31
forum: Installation &amp; Upgrades
---

### Post by ioriaperlinux on 2020-12-31
I have a Fijitsu Lifebook A531. Removed windows and tried to install ubuntu by live usb, 20.10 ver.

I have tried 2 usb keys, different distributions (ubuntu and xubuntu), key made by different apps (rufus and others). I tried to do manual partition for disk, using different partition tables (msdos and gpt), but also tried with automatic partition. No matter, result is always the same. Installation goes straightforward, no issue: ask me to restart, remove usb media... and at the restart, appears this

[https://drive.google.com/file/d/1idpoSAtEaclxVVxSKqkDvodqpI7rXvm5/view?usp=drivesdk](https://drive.google.com/file/d/1idpoSAtEaclxVVxSKqkDvodqpI7rXvm5/view?usp=drivesdk)

And then bios boot. Ubuntu does not start.

I tried to restart using usbkey, checking if disk is broken or corrupted... disk resulted ok by any physical check. Tried to repair boot loader... and other procedure I have found here and there in forums. Nothing seems to work. Running gparted after automatic partitioning*this is how disk has been partitioned

[https://drive.google.com/file/d/1imu6v0VPsn144-5f42KrzWXSH3y4GitD/view?usp=sharing](https://drive.google.com/file/d/1imu6v0VPsn144-5f42KrzWXSH3y4GitD/view?usp=sharing)

Hope anybody can help me.

Thanks. Ioria. (Sorry for not perfect english)

---

### Post by oldfred on 2020-12-31
The PXE boot is normally one of the default boot options in a system. I turn that option off on my systems.
But that means UEFI/BIOS did not find a working install to boot from and just went to next in boot order.

May be UEFI/BIOS settings. 
Looks like it may be an early UEFI system.
Back then both vendors and Linux systems often had issues, particularly with some less popular models.

I would use gpt if you do not have nor want Windows in BIOS boot mode.
But with gpt you need an ESP - efi system partition for UEFI boot or a bios_grub partition for BIOS boot.
When first planning conversion from BIOS to UEFI, I often put both an ESP & bios_grub as first two partitions on new drives & larger flash drives where putting a full install.

It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot.
You can also use gparted but must change default partitioning first.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.
Or use gdisk which is in repository, now standard in newer installs:

How you boot install media, UEFI or BIOS is then how it installs.
Some tools like Rufus only convert ISO to either UEFI only or either BIOS only. So you have to select when creating installer. And then from UEFI/BIOS menu select that boot mode. Many tools create installer that is for both BIOS & UEFI, and you select when booting USB flash drive from UEFI boot menu.
And then you have to have default boot mode in UEFI/BIOS settings to match how you installed.

Your existing partitions look fine, if on gpt drive. You only need bios_grub for BIOS boot, or ESP for UEFI boot.
But when I was first converting from BIOS to UEFI, I always had both on every new or repartitioned drive.
Often better to post terminal output like this in code tags rather than screenshot. Use forum's advanced editor & # icon to add code tags.
sudo parted -l

If you have an install, or think you do:
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ioriaperlinux on 2021-01-01
Thank you oldfred, your indications are clear to me.

By the way, by your suggestion seems like Rufus has been configured correctly and even in my several installations attempts I have also configured partitions manually like you said. But let's see what we have now...

Thank you for your support.

this is the pastebin link. I guess you can access  [URL="https://paste.ubuntu.com/p/86jt8mDcVj/"]https://paste.ubuntu.com/p/86jt8mDcVj/

[/URL]P.S.: except for the installation, HDD right now is empty, all personal data has been saved in a backup and formatting disk or reinstalling everything from scratch is not a particular problem. If you believe I did something wrong and, instead repairing, it is faster to repeat installation following different indications/instructions/steps, please suggest so!

---

### Post by tea for one on 2021-01-01
[COLOR="#0000FF"]Line 17[/COLOR] - Bios boot partition (sda1)
[COLOR="#0000FF"]Line 23[/COLOR] - EFI partition

This is probably causing the difficulty.

As you mentioned that it wouldn't be a great problem to start from scratch, then that is the best course of action.

Insert your USB stick and power on.
Boot the live session in UEFI mode.
During the live session, double check that you have booted in UEFI mode via the terminal
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
```
Open gparted > Device > Create Partition Table > Select GPT
Close gparted and install Ubuntu

You should end up with 2 partitions - EFI and / (i.e.system partition inc. your user directory).

A re-installation should take 30 -45 minutes and is good practice for the future.

Good luck

---

### Post by oldfred on 2021-01-01
Boot-Repair says you booted in BIOS/Legacy mode.
Probably better to be in UEFI mode, but it says it will try to reinstall the UEFI version of grub - grub-efi-amd64. Normally to do repairs you have to be in correct mode.

The only difference between UEFI boot and BIOS boot for an install is the version of grub. It uses grub-pc for BIOS and grub-efi-amd64 for UEFI boot. Some settings are also automatically changed, like mount of ESP in fstab.
But system also needs to be set for UEFI boot, if install is UEFI.

I think it is ok to have both bios_grub & ESP on gpt drive, as I did that for years when first planning & then converting from BIOS to UEFI. 

Usually best to have Ubuntu live installer in same mode as you want to repair system. Or boot live installer in UEFI for UEFI install & repair and boot in BIOS for BIOS install & repair.
Also best to have live installer of current version of Ubuntu that you have installed for future repairs.

---

### Post by ioriaperlinux on 2021-01-01
I am back, I tried to follow procedure described by "tea for one".

I have created first key using rufus and this configuration: Partition scheme --> GPT. See screenshot in link. Xubuntu 20.10

[https://drive.google.com/file/d/1FNwBr99aFcMuTm3hWyUx4bQq-MlhwNYk/view?usp=sharing](https://drive.google.com/file/d/1FNwBr99aFcMuTm3hWyUx4bQq-MlhwNYk/view?usp=sharing)

Problem is that USB is not working in my laptop. Live does not start and usb seems not "boot-able".

So, I have then created the usb with the configuration: Partition scheme --> MBR, Target system --> "BIOS or UEFI". Xubuntu 20.10

[https://drive.google.com/file/d/1Q6QqeSFuOvVJZg3u6yOsgUcKZmUUGuJ_/view?usp=sharing](https://drive.google.com/file/d/1Q6QqeSFuOvVJZg3u6yOsgUcKZmUUGuJ_/view?usp=sharing)

Then I have run ```
[COLOR=#000000][FONT=&quot][ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"[/FONT][/COLOR]
```

Result is "Legacy mode". So, seems starting again in Legacy mode.

I suspect if I start installation, then I am back to where I was before. 

Any help how to proceed? what about if I try 20.04 LTS in Legacy? could it change anything? I have read in some forum that 20.10 and automatic installation, have frequently problem with some old BIOS versions.

Thanks.
Ioria

---

### Post by tea for one on 2021-01-01
When you power on the PC, do you see the PC boot menu (often accessed with a dedicated key such as F10 or F9 or similar)?

If you see the PC boot menu, you then need to boot the selection which begins [COLOR="#0000CD"]UEFI: name of usb device[/COLOR] i.e. Kingston or Sandisk etc.

That selection will load the live session in UEFI mode.

It is important to make the correct selection at the beginning rather than let the PC follow some default boot sequence.

By the way, how old is the PC?

As [COLOR="#0000FF"]oldfred[/COLOR] mentioned earlier, it may have a UEFI implementation that is less than perfect.

---

### Post by ioriaperlinux on 2021-01-01
It's a [COLOR=#000000]Fijitsu Lifebook A531.[/COLOR] Year 2011. Core i3 processor with 8GB of RAM. I guess BIOS does not support UEFI, I don't see a selection UEFI: "....". There is only the USB, HDD and Network...

[COLOR=#000000][/COLOR]I think I will try in legacy mode using version 20.04. I read in other forum that 20.10 have a problem exactly for my case in installation in legacy mode.

Thanks, I will post the result.
Ioria.

---

### Post by ioriaperlinux on 2021-01-02
Hi,
I did it, and ver. 20.04 LTS installation is perfectly working.

My system is a CSM system and must work in legacy mode. This is now clear.

USB key is then started in legacy mode, but in 20.10 (almost all distributions, except Lubuntu as I see) there is a known bug, here: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1893964](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1893964), preventing the installation to work properly.

Being CSM, I set device partition table as msdos, as I have tried to do also with 20.10. If I leave automatic installation, procedure creates me also a partitionEFI and configurations I have shown above in screenshots. those configurations are not needed as you said already.

But if I create only one partition for ROOT, as required for legacy systems, 20.10 goes to a warning saying "you have not created a partitionEFI, proceed at your own risk" even if this partition was not required. If you say "OK" to proceed, installation start but when almost at the end generate a fatal error, which makes the installation procedure to not finish. This does not happen with Lubuntu or other distributions based on 20.04.

If I instead leave the partitionEFI and the 20.10 to go to the end, the installation is not boot-able. That's all.

Thank you all for the help, I guess this is solved.
Ioria

---

### Post by tea for one on 2021-01-02
Well done - the perseverance and experimentation yielded a positive outcome.
It's always nice to read about successful results.

To mark a thread as solved [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

As a point of interest, you mentioned CSM in your last post - this acronym stands for [COLOR="#0000FF"]Compatibility Support Module[/COLOR].

This module allows UEFI systems to boot in Legacy mode.
A true legacy system would not need a CSM therefore I suspect the age of your PC reflects the firmware changes being introduced approx 9/10 years ago.

Some older firmware have configuration settings for Advanced Boot or Advanced Devices or something similar, which is where the UEFI trigger may reside.
It is impossible to give accurate advice because each vendor implements their UEFI/BIOS to their own recipe.

Nevertheless, I digress.........I hope that you enjoy your time with Ubuntu/Xubuntu/Lubuntu and that you will be able to help others in a similar situation.

---

### Post by oldfred on 2021-01-02
You can install using gpt partitioning with BIOS mode. I started that with my old 2006 system in 2010.
And when UEFI started to be a standard in 2012 with release of Windows 8, and I expected to move drives to a new system, I started adding both a bios_grub partition for BIOS/Legacy/CSM boot and an ESP - efi system partition. Only real difference is version of grub, as actual install is the same.

Now only BIOS system is an old 2006 laptop with both bad batteries, but functional. Only works when plugged in, and I have to reset time as without coin battery working it forgets.
I installed Kubuntu 20.04 using gpt with a bios_grub partition.

---

