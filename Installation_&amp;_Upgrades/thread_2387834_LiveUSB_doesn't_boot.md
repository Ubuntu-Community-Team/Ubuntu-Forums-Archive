---
title: "LiveUSB doesn't boot"
date: 2018-03-24
forum: Installation &amp; Upgrades
---

### Post by thebittenpeach on 2018-03-24
Hello,

I am new to Ubuntu though I am no beginner in PC. 
I was trying to install Ubuntu 17.10 on my Win 10 notebook but without success... I downloaded the right iso x64 file and used Rufus to mount it on my 1st USB stick. When I visited the UEFI page, the USB wasn't listed there. So I tried to use 2nd USB and again, without success. The format was always fat32, I tried all the partition schemes (MBT & GPT for UEFI, MBT for BIOS & UEFI)... I don't know what I did wrong. I search the solution for so long (2nd day now) and it's still not working. I even tried to disable Secure boot. 

Somewhere on the web was written that I should change the Boot settings or whatever to Legacy, but I do not see the option anywhere in UEFI.

Would someone be willing to help me? It would be much appreciated.

My PC is Acer Spin 1 x64, Windows 10, quite new (I have never installed any OS on it, I only once did a clean reinstall).

---

### Post by C.S.Cameron on 2018-03-24
The latest UNetbootin has worked for me making boot drives that work with both BIOS and UEFI from a Windows machine.
Mkusb works from a Linux machine

---

### Post by thebittenpeach on 2018-03-24
I just tried the UNetbootin program and the result is still the same - no booting of the USB and UEFI can't see any USB connected.

---

### Post by C.S.Cameron on 2018-03-24
Hmm. YUMI has a **beta UEFI** version that also worked for me.

---

### Post by thebittenpeach on 2018-03-24
> **C.S.Cameron said:**
> Hmm. YUMI has a **beta UEFI** version that also worked for me.

I might try that too but I don't think it's gonna work either. Think the problem's somewhere else.

---

### Post by yancek on 2018-03-24
With a pre-installed windows 10, it will be using EFI/GPT so you must install Ubuntu EFI/GPT.  THis is explained in the Ubuntu documentation at the link below.  Do not change BIOS settings to Legacy.  Do you not see the name of the usb when you go to the boot options?  Are you unable to boot the usb at all?  Have you or can you test it on another machine?  I believe Acer requires you to set Trust somewhere in the BIOS to install another system.  Might check your user manual.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by thebittenpeach on 2018-03-24
> **yancek said:**
> With a pre-installed windows 10, it will be using EFI/GPT so you must install Ubuntu EFI/GPT.  THis is explained in the Ubuntu documentation at the link below.  Do not change BIOS settings to Legacy.  Do you not see the name of the usb when you go to the boot options?  Are you unable to boot the usb at all?  Have you or can you test it on another machine?  I believe Acer requires you to set Trust somewhere in the BIOS to install another system.  Might check your user manual.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Hello, I will check that out, thanks!

Yes I don't see the name of the USB in boot options, the PC behaves as there's no USB at all. Unfortunately I cannot test the USB on any other device right now. 

I'll also try to find that user manual. Thanks a lot.

---

### Post by yancek on 2018-03-24
BIOS settings vary widely based on manufactuer but usb drives are often listed under hard drives, HHD in BIOS.

---

### Post by thebittenpeach on 2018-03-25
Yes but even if I select HDD to boot first, nothing happens and Windows starts as usual.

Also I've searched in the user manual but there's nothing there... I don't know how to set Trust as I don't really know what that is. I thought installing linux would be easier:confused:

---

### Post by thebittenpeach on 2018-03-25
> **thebittenpeach said:**
> Yes but even if I select HDD to boot first, nothing happens and Windows starts as usual.

Also I've searched in the user manual but there's nothing there... I don't know how to set Trust as I don't really know what that is. I thought installing linux would be easier:confused:

If Trust means setting a supervisor password, then I have already done that. But that's all I can do. I've tried to set Secure Boot on disabled and enabled and it just doesn't work. I don't know... is it worth it to install Ubuntu when there's so many problems with it from the beginning?

---

### Post by oldrocker99 on 2018-03-25
When you do get it booting, make sure that the USB boots in a legacy manner, NOT UEFI. The result is likely to result in a failure to install GRUB, without which the PC won't boot. 

When you use Unetbootin, or any other means, make sure that the USB drive is formatted as FAT32 only.

---

### Post by thebittenpeach on 2018-03-29
Hello,

so I think I have done a little bit of progress. I formated the USB drive to NTFS with GPT partition for UEFI and now the USB stick is recognized by the UEFI boot mode. 

If I select the USB to boot as first though, there's a screen with my PC's logo Acer (as always with starting the PC) and in the upper left corner something is being written. The last thing it says is "Launching NTFS EFI loader". I have waited for like 10 minutes and still the last thing it said was this. 

So, I'm happy that the UEFI will now at least recognize the USB stick but it seems to be stuck at the Launching NTFS EFI loader... I also had to disable secure boot.

---

### Post by thebittenpeach on 2018-03-29
I can't seem to change the mode of booting. My PC is kinda new, so that might be the reason. Or perhaps I'm just not experienced enough. It is impossible for me to switch to the Legacy mode at this point though.

---

### Post by thebittenpeach on 2018-03-29
> [COLOR=#000000]When you do get it booting, make sure that the USB boots in a legacy manner, NOT UEFI. The result is likely to result in a failure to install GRUB, without which the PC won't boot. [/COLOR]

[COLOR=#000000]When you use Unetbootin, or any other means, make sure that the USB drive is formatted as FAT32 only.[/COLOR]

I can't seem to change the mode of booting. My PC is kinda new, so that might be the reason. Or perhaps I'm just not experienced enough. It is impossible for me to switch to the Legacy mode at this point though.

Also, if formatting to FAT32, the USB doesn't load at boot unlike if formatted to NTFS.

---

### Post by deanr2 on 2018-03-29
I've said it before and been laughed at but I'll say it again - boot from a DVD. This way you don't have the issues with EUFI, secure boot, BIOS settings which do their best to preserve WIN10 etc. Believe me, it's much easier this way :-)

---

### Post by thebittenpeach on 2018-03-29
> **deanr2 said:**
> I've said it before and been laughed at but I'll say it again - boot from a DVD. This way you don't have the issues with EUFI, secure boot, BIOS settings which do their best to preserve WIN10 etc. Believe me, it's much easier this way :-)

Can I even buy the DVD as for today? :D I haven't use it for such a long time... Maybe you're right though. If I get to buy a DVD I might try that option.

---

### Post by deanr2 on 2018-03-30
> **thebittenpeach said:**
> Can I even buy the DVD as for today? :D I haven't use it for such a long time... Maybe you're right though. If I get to buy a DVD I might try that option.

I spent hours and hours trying to boot my various computers from USB. I tried everything and every variation of setting in the BIOS found on various forums and websites etc. - and nothing. It would either fail to recognise the USB, recognise it by stall, simply freeze the moment the Ubuntu flash screen appeared, seem install but on restart boot to Windows 10 with no grub options etc. As a last resort I burned the iso onto a DVD. Worked immediately with zero hassle :)

---

### Post by thebittenpeach on 2018-03-30
> **deanr2 said:**
> I spent hours and hours trying to boot my various computers from USB. I tried everything and every variation of setting in the BIOS found on various forums and websites etc. - and nothing. It would either fail to recognise the USB, recognise it by stall, simply freeze the moment the Ubuntu flash screen appeared, seem install but on restart boot to Windows 10 with no grub options etc. As a last resort I burned the iso onto a DVD. Worked immediately with zero hassle :)

Well I have now figured that my notebook has no CD drive! I was so used to having the drive that I actually forgot that my little 2in1 pc doesn't have it. 

The last option for me would be an SD card, cause obviously my notebook has the slot for it.

Anyway, after lots of searching on the net, I've found that setting the network mode to ***enabled*** (while USB being formatted as NTFS for GPT partition) will take me further. It showed me GNU GRUB window... However, as I'm not that experienced, I won't install it that way (with GRUB).

So I, again, tried formatting the USB to FAT32 (still GPT partition) and while I again wasn't able to boot from the stick, I could find the USB folder in the "Set as UEFI trust file (or something similar to that)". I think I should select <USB>/<EFI> and then GRUBx64 (or something like that) and perhaps it would work then.

I am too scared to do that though. I don't know if that could in any way mess up my computer... So I am asking for your help!

---

### Post by orca100 on 2018-03-30
I feel for you and agree. I am kicking my but for downloading Ubuntu. May as well dump my new laptop in the bin. One has to be computer savvy to be able to drive this.

---

### Post by deanr2 on 2018-03-31
[B][I][COLOR=#000000]Well I have now figured that my notebook has no CD drive! I was so used to having the drive that I actually forgot that my little 2in1 pc doesn't have it. 

[/COLOR][/I][/B][COLOR=#000000][INDENT]***I feel for you and agree. I am kicking my but for downloading Ubuntu. May as well dump my new laptop in the bin. One has to be computer savvy to be able to drive this.***[/INDENT]
[/COLOR]

I've got a USB external CD drive. Could you borrow / buy a cheap one? Of course, another solution for you both would be to take the pc to a shop and ask them to install (dual-boot?) Ubuntu for you and set the bios to allow future USB installs. I know my local service centre does this for approx. £10.

Despite the problems I've had (see another post) I've now got Ubuntu / Linux OSs on all 4 of my working computers (3 of which were by necessity installed from DVD) and have pretty much migrated fully from WIN10. 

I'm sure it'll be worth it in the long term :-). And if you do get it working, follow the advice somebody gave me - stay away from the terminal!

---

### Post by deanr2 on 2018-03-31
***[COLOR=#000000]When you do get it booting, make sure that the USB boots in a legacy manner, NOT UEFI. [/COLOR]***

I read somewhere that Linux Mint installs from USB regardless of the UEFI settings. If that can be confirmed, maybe that would be a good option for the OP??

---

### Post by thebittenpeach on 2018-03-31
Ok so the USB is now working. I had to enable Secure Boot, enable Network boot and add BOOTx64 as a trusted UEFI file. Now I have another problem - If I try to install the OS, the installer is stuck at installing GRUB package... I will create a new thread.

---

### Post by orca100 on 2018-04-02
Originally posted by amp-man.

[COLOR=#000000]1) After download from USB, it will boot back into Windows. Shut down again. Reboot and hit F2 to enter the BIOS again.[/COLOR]
[COLOR=#000000]2) Under "Security", choose "Set Supervisor Password", and set one. You will need this password any time you go back into the BIOS. A bunch of options on the page should change from grey to blue.[/COLOR]
[COLOR=#000000]3) The "Select an UEFI file as trusted for executing" should now be available. If it's not available, check that Secure Boot is still Enabled, if not, Enable it. Select it, and navigate to HDD0->EFI->ubuntu->grubx64.efi. The BIOS will ask you for a name for it, I called it Grub.[/COLOR]
[COLOR=#000000]4) Hit F10 to save and exit, then immediately hit F2 again to re-enter the BIOS. [/COLOR]
[COLOR=#000000]5) Now go to "Boot", set "Secure Boot" to "Disabled", and arrow down to the bottom of the list to your new "Grub" entry. Hit F6 until it's the top of the list.[/COLOR]
[COLOR=#000000]6) Hit F10 one last time. Your system should now reboot to the Grub boot loader![/COLOR]

---

