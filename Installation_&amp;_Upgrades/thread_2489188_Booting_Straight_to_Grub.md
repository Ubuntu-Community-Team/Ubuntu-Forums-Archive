---
title: "Booting Straight to Grub"
date: 2023-07-21
forum: Installation &amp; Upgrades
---

### Post by triggerhz on 2023-07-21
Hey all,

I'm currently trying to sort out my dual booting for Windows and Ubuntu (and I don't do much at all with Linux). This used to work like a charm, then Ubuntu updated, and it just goes to a grub prompt now. I tried reinstalling it and it did the same, so I wiped both my SSD's so it was completely fresh and started totally from scratch, stuck Ubuntu on using the "Install alongside Windows" option, and I'm back to grub so I'm guessing it's more BIOS related but it's weird that this happened after I went into Ubuntu fine and did an update.

When I try to list drives, it's only seeing the main one, not the second bay so I assume that's part of the issue as it looks like ubuntu very cleverly used the spare partition that I created on that drive as I can see the various Ubuntu folders there when I boot into a Live USB session.

BIOS does know that that drive is there as far as I can tell. When I was playing with various install options before, it came up as a bootable device with ubuntu on, but went to Grub.

I've tried disabling secure boot, enabling legacy boot, and disabling fast boot in Windows. I've seen some stuff about pointing grub to the boot folder, but this is on the second drive which it can't see. Also tried the Ubuntu Boot-Repair but had no luck on that front.

When it boots up into the Grub (as should be Ubuntu) it is currently pointing to the boot manager on the main drive.


I didn't know what information would be useful, so apologies if this is a bit sparse! Let me know what you need and I can see if I can get it.

---

### Post by yancek on 2023-07-21
Run boot repair again and this time do not try any repairs but select the Create BootInfo Summary option.  When it finishes, it will give you a link which you can post here so you can get help.

---

### Post by triggerhz on 2023-07-21
Thanks for coming back to me Yancek. Here's the pastbin link. I've run this from within a USB live Ubuntu session, not sure that matters too much.

[https://paste.ubuntu.com/p/57WhJb56Tp/](https://paste.ubuntu.com/p/57WhJb56Tp/)

---

### Post by yancek on 2023-07-22
Have you tried accessing the BIOS firmware boot options and setting Ubuntu to first in the boot order.  Lines 16-27 of the boot repair output show the EFI files for both windows and Ubuntu and the correct files are there.  Both drives are GPT so you need an EFI install for windows which you have.  Ubuntu put its EFI boot files in sda1 (windows drive) which is common behavior for the Ubuntu installer.  That drive would need to be first in boot order.  sda is the smaller (119GB drive).  The UUID for the Ubuntu / (root filesystem) partition is 4e16c0db-9e32-4b67-864f-70e8e560c75d which is what is also shown in the grub.cfg file on the EFI partition on line 217, the /boot/grub/grub.cfg file (line 223) and the /etc/fstab file on line 234.  The changes I've suggested should rectify this problem.

---

### Post by oldfred on 2023-07-22
Report also still showed UEFI Secure boot on.
Try again with it off. 
Updating UEFI which is recommended, & often done by Windows with newer systems may reset UEFI settings to defaults. Any you changed to install Ubuntu often have to be redone.

---

### Post by tea for one on 2023-07-23
> **triggerhz said:**
> and I don't do much at all with Linux
Then, you may want to consider alternative ways to use Ubuntu and let the Windows Boot Manager perform its normal function.

Have you considered using Ubuntu:-
[LIST]
[*]As a live session on an external USB device
[*]As above but with persistent storage
[*]Fully installed on an external device with user and password
[*]Fully installed on your second internal disk with its own ESP (each OS independently uses its relevant boot procedure)
[/LIST]
Two internal disks allow the user to avoid Grub boot problems if the OS installations are carefully planned.

---

### Post by triggerhz on 2023-07-24
So thanks to yourselves, I've been able to make a few more observations now I've found some time to have a play around:

> **yancek said:**
> Have you tried accessing the BIOS firmware boot options and setting Ubuntu to first in the boot order.  Lines 16-27 of the boot repair output show the EFI files for both windows and Ubuntu and the correct files are there.  Both drives are GPT so you need an EFI install for windows which you have.  Ubuntu put its EFI boot files in sda1 (windows drive) which is common behavior for the Ubuntu installer.  That drive would need to be first in boot order.  sda is the smaller (119GB drive).  The UUID for the Ubuntu / (root filesystem) partition is 4e16c0db-9e32-4b67-864f-70e8e560c75d which is what is also shown in the grub.cfg file on the EFI partition on line 217, the /boot/grub/grub.cfg file (line 223) and the /etc/fstab file on line 234.  The changes I've suggested should rectify this problem.


My UEFI firmware is rubbish. It seems to be locked into a basic mode, I can choose a type of device in the boot order, but not the individual devices (I'm working on this)

> **oldfred said:**
> Report also still showed UEFI Secure boot on.
Try again with it off.
Updating UEFI which is recommended, & often done by Windows with newer systems may reset UEFI settings to defaults. Any you changed to install Ubuntu often have to be redone.

Turning Secure Boot off still didn't immediately fix the issue however, I was able to then choose to boot from an EFI file, and if I choose shimx64 it boots happily. Turning secure back on, and it's back to the lovely GRUB screen. I tried installing shim-signed as per the below, but it says it's installed (I was under the impression that recent Ubuntu liked secure boot as well, is that wrong?)
[How to install shim-signed on Ubuntu]("https://howtoinstall.co/package/shim-signed")

> **tea for one said:**
> Then, you may want to consider alternative ways to use Ubuntu and let the Windows Boot Manager perform its normal function.

Have you considered using Ubuntu:-
[LIST]
[*]As a live session on an external USB device
[*]As above but with persistent storage
[*]Fully installed on an external device with user and password
[*]Fully installed on your second internal disk with its own ESP (each OS independently uses its relevant boot procedure)
[/LIST]
Two internal disks allow the user to avoid Grub boot problems if the OS installations are carefully planned.

Definitely see your point about just using something external and a live session. Only reason I aren't going down that line is simply so I can learn a few bits and have a play. Still appreciate the suggestion though!

I may resort to just tweaking my drives again and pulling the Windows M.2 while I install Ubuntu so it's all setup separately as you suggest, see how long it takes me to throw my toys out the pram trying to fix it :P

---

### Post by oldfred on 2023-07-24
You should not have to remove NVMe drive. Most UEFI have settings for disabling or turning off a drive. But you may have to use a Windows repair disk to recreate the UEFI boot entry for Windows. When a drive is removed, UEFI changes the settings. But many uEFI also find a Windows entry in the ESP, but not an Ubuntu entry.

Its not just signed grub, but kernel & all drivers must be signed. Usually best to install with Secure Boot on. I am not sure if you use Boot-Repair's advanced mode when booted with secure boot on & choose to totally reinstall grub and install new kernel, if that works.

---

### Post by triggerhz on 2023-07-25
> **oldfred said:**
> You should not have to remove NVMe drive. Most UEFI have settings for disabling or turning off a drive. But you may have to use a Windows repair disk to recreate the UEFI boot entry for Windows. When a drive is removed, UEFI changes the settings. But many uEFI also find a Windows entry in the ESP, but not an Ubuntu entry.

Its not just signed grub, but kernel & all drivers must be signed. Usually best to install with Secure Boot on. I am not sure if you use Boot-Repair's advanced mode when booted with secure boot on & choose to totally reinstall grub and install new kernel, if that works.


:guitar:Whoo ooo We're half way there, Whoo ooo, Ran a grub repair!! :guitar:

I hope you're a Bon Jovi fan or that won't be as funny, and I'm already pushing it.



So the Grub repair did help. I can now enable legacy boot, and choose Ubuntu from the UEFI boot menu as I should be able to do (apologies it was Legacy that was enabled, not just secure boot disabled that let me get to the EFI file and boot from there). So that's a step closer. I tried the kernel reinstall and that was just sitting there spinning for a good 30 minutes, which it said would only take several so I rebooted it and it doesn't seem to have done anything, is it worth trying again and was I just being impatient??

I don't know if now I'm probably at the point I have to choose sticking with legacy boot and not having secure on and reimaging it without the NVMe (stupid locked down UEFI so I can't just disable it) so it's all in one place which might be what's needed to get it booting happily as it was before the great update of a few days ago?

---

### Post by oldfred on 2023-07-25
There were some older UEFI systems that needed Legacy mode on, to boot in UEFI mode with Secure boot off.
Then most systems had 3 boot modes UEFI, UEFI with Secure boot & Legacy/BIOS/CSM. Legacy only works with Secure boot off.

New systems starting about 2020, eliminated the CSM/Legacy mode entirely. Or only UEFI. Still  seem to have UEFI Secure boot on or off available.
But every vendor varies settings. Similar models often have same UEFI settings, just not all the same options. But vendors also update UEFI so new system may not be same as old. 

If Internet working ok, update should be relatively quick, unless you also have some drive type issue & need fsck.

---

### Post by triggerhz on 2023-07-26
I've double checked and UEFI/BIOS/firmware is all up to date.

It was updated when the issue started as I did have it all up and running until Ubuntu did an update and all this started, which I sort of lost sight of myself in all of this (too busy making Bon Jovi puns), so it should be OK with the version and set up that I have, including not needing legacy boot to be enabled and being able to just choose it from the boot manager rather than having to go digging for the EFI file.

I'm starting to think I just bite the bullet and reinstall it as I mentioned do you think? A shame as it's sort of cheating, but sometimes you got to do what you got to do!

---

### Post by triggerhz on 2023-08-01
Fixed it! Though I must admit I committed a sin, I performed two different potential fixes at once so I can't be certain which resolved it but I suspect both were needed.

First I pulled my Windows m2 chip (couldn't disable it in the bios as HP are tyrannical about it) and installed it fresh on the second drive in it's own partition with a separate EFI partition also. I think this sorted the issue with it booting to GRUB specifically.

Second thing I did was choose the install third party software option. I hadn't noticed before but this had options to configure secure boot, so I could then apply the key it created. Hadn't noticed this with it being greyed out unless you choose to install 3rd party so ticked that box, ticked configure secure boot, set my password and chose the option to apply key then next through it. Thinking this sorted out it wanting to be in legacy mode with secure boot disabled.

Hopefully this will help someone in future!

---

