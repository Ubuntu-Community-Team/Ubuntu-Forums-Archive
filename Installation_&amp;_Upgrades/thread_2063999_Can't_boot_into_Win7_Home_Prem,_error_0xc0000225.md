---
title: "Can't boot into Win7 Home Prem, error 0xc0000225"
date: 2012-09-28
forum: Installation &amp; Upgrades
---

### Post by Hotsuma on 2012-09-28
Hello, I have a Windows 7 x64 ultrabook with no optical drive (Asus Zenbook).

I can no longer boot into Windows. I get the following error: 0xc0000225 

I tried to fix it with a bunch of different programs & methods. I tried to create many versions of the Windows repair/OS CD on a USB stick and it works but always says it is the wrong version, even though I know I have Windows 7 x64 Home Premium.

Boot-repair would only make this record for me:

[http://paste.ubuntu.com/1231265/](http://paste.ubuntu.com/1231265/)

I can see everything in Gparted, but I am in over my head and don't even know how to try to fix it. 

I don't really understand much on this level. I just know my laptop won't boot to Windows anymore and I need to fix it ASAP. I had Vista and Ubuntu on my old laptop with no such problems.

I am running ubuntu off a USB drive right now, I'll worry about finishing installing it once Windows gets sorted. 

Thanks in advance for any help and advice. I am a linux noob so I'd appreciate very basic instructions. ;)

---

### Post by darkod on 2012-09-28
Did you find any explanation for that error code? It must give something specific, but you never mention that.

Also, when booting the windows repair usb, are you booting the stick in UEFI mode? You can see that the computer uses UEFI boot so you need to boot any repair cd/usb in UEFI mode.

So first of all make sure when creating the repair usb that the bootloader supports uefi mode, and then boot it in that mode. UEFI compatible devices should show with UEFI string in front in the boot devices list.

---

### Post by darkod on 2012-09-28
This thread says you can't use usb stick to repair windows, which sounds very odd but it does quote Microsoft KB article:
[http://www.sevenforums.com/installation-setup/178280-error-0xc0000225-boot.html](http://www.sevenforums.com/installation-setup/178280-error-0xc0000225-boot.html)

In case that is true, can you use a external usb cd-rom or similar? And do you have the win7 repair cd or someone that can burn it for you who has the same version?

---

### Post by Hotsuma on 2012-09-28
> **darkod said:**
> Did you find any explanation for that error code? It must give something specific, but you never mention that.

Also, when booting the windows repair usb, are you booting the stick in UEFI mode? You can see that the computer uses UEFI boot so you need to boot any repair cd/usb in UEFI mode.

So first of all make sure when creating the repair usb that the bootloader supports uefi mode, and then boot it in that mode. UEFI compatible devices should show with UEFI string in front in the boot devices list.
Thanks for your help darkod! 

On the code: I didn't find anything more specific than that I should use the Windows recovery CD, which does not work (thus far). 

Can you explain how one would boot to the stick in UEFI mode? A lot of this stuff is new to me so I don't quite understand. It would be awesome if this solved the problem, but I am afraid I'm going to need simpler instructions. ;)

---

### Post by Hotsuma on 2012-09-28
> **darkod said:**
> This thread says you can't use usb stick to repair windows, which sounds very odd but it does quote Microsoft KB article:
[http://www.sevenforums.com/installation-setup/178280-error-0xc0000225-boot.html](http://www.sevenforums.com/installation-setup/178280-error-0xc0000225-boot.html)

In case that is true, can you use a external usb cd-rom or similar? And do you have the win7 repair cd or someone that can burn it for you who has the same version?
I read the same thing a few times, but plenty of other times which said it works including first hand testimonials so I am hopeful it's true but can't be certain. 

Unfortunately I do not have access to either an external cd-rom or someone with the same version of Windows. :(

---

### Post by YannBuntu on 2012-09-28
> **Hotsuma said:**
> [http://paste.ubuntu.com/1231265/](http://paste.ubuntu.com/1231265/)

So you have only Windows7 on this computer.It was installed in UEFI mode, so you must setup your BIOS to boot the HDD in UEFI mode. (if you are not sure, tell us the available entries in your BIOS boot order menu).

If still not good:
1) boot a Ubuntu CD, choose "Try Ubuntu", browse your files in order to backup your documents on an external disk (or DVDs)
2) use a Windows7-64bit disk to fix your installed Win7. See [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
3) if still not good, please ask on Windows forums. (and let us know if you find a solution)
4) if still not good, just reinstall Windows

---

### Post by oldfred on 2012-09-28
I found this on Windows 8 with UEFI.

The issue is UEFI wants to boot from FAT32 but the Windows repair USB is normally NTFS. 
While for Windows 8 I would think you could do the same for Windows 7. Just no secure boot issues. :)

Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

---

### Post by Hotsuma on 2012-09-29
> **YannBuntu said:**
> So you have only Windows7 on this computer.It was installed in UEFI mode, so you must setup your BIOS to boot the HDD in UEFI mode. (if you are not sure, tell us the available entries in your BIOS boot order menu).

I took some screenshots with my phone of the relevant information I found in the BIOS, GParted, and Partiton Wizard. I think it's easier to post them than it is to explain because I don't really understand everything so well. 

Can you please explain how I might setup the BIOS to boot to the HDD in UEFI mode?

I can explain that yes there is only Win7 on the laptop so far. I didn't even get to the point of installing Ubuntu, but luckily I have been running it off of a USB stick for now. 

> **YannBuntu said:**
> 
2) use a Windows7-64bit disk to fix your installed Win7. See [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

It seems like this should work if I can just get the right Win7 recovery disk. I tried about 7 times, but it always says it is the wrong version of Windows even tho I know it is the same. I think the problem goes back to the laptop having the EFI bios and I have not been able to resolve that yet, although it seems like it should be possible. It's hard when it's all over my head but I'll keep trying!

---

### Post by Hotsuma on 2012-09-29
> **oldfred said:**
> I found this on Windows 8 with UEFI.

The issue is UEFI wants to boot from FAT32 but the Windows repair USB is normally NTFS. 
While for Windows 8 I would think you could do the same for Windows 7. Just no secure boot issues. :)

Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
This sounds like it could be the same sort of problem I was having with the Win 7 recovery not working (see last post), so I will give these instructions a shot and hope for the best, thanks! :)

Do you know if it is possible to create this repair USB from within ubuntu? Basically a linux version of the same instructions. I ask because I am concerned it might be a problem to follow step #2 since my old laptop is 32-bit Vista (dual boot with ubuntu, actually, but I still don't know how to do this in linux!) but I don't know for sure. I'll try anyway.

Furthermore, the volume button stuff (step #3 and on) seems specific to Samsung or something. Especially since my laptop has no such buttons, unfortunately. Nevertheless, it seems like the theory behind this post is applicable to my problem as well so I'd like to try to adapt it or work from here and maybe have good luck.

Thanks again for your help!

---

### Post by darkod on 2012-09-29
Not the HDD, I said the cd or usb stick, depending what you are booting to repair win7, and to install ubuntu too.

Often it's easier not to go into BIOS but only to bring the built-in boot menu during boot, usually with F12. Do you have a message during boot like F12 Boot Menu or similar? Also, many messages can be hidden by a manugacturer image. They are more interested in you looking at a picture rather than watch what is happening when booting. :)

Any device able to be booted in UEFI mode will have two entries in the mentioned built-in boot menu, standard option and UEFI option. You need to select the UEFI so it can boot in UEFI.

See if you can enter this menu with F12 and see what you have there as options to boot from.

---

### Post by Hotsuma on 2012-09-29
> **oldfred said:**
> I found this on Windows 8 with UEFI.

The issue is UEFI wants to boot from FAT32 but the Windows repair USB is normally NTFS. 
While for Windows 8 I would think you could do the same for Windows 7. Just no secure boot issues. :)

Windows 8 UEFI repair USB must be FAT32
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)

I tried to follow these instructions the best I could considering the differences, however I got the wrong version of Windows error, again. I formatted the USB stick exactly the same way and created the ISO/USB stick in Vista. 

I can load the stick but after I choose my language I get this 'wrong version' error.

---

### Post by Hotsuma on 2012-09-29
> **darkod said:**
> Not the HDD, I said the cd or usb stick, depending what you are booting to repair win7, and to install ubuntu too.

Often it's easier not to go into BIOS but only to bring the built-in boot menu during boot, usually with F12. Do you have a message during boot like F12 Boot Menu or similar? Also, many messages can be hidden by a manugacturer image. They are more interested in you looking at a picture rather than watch what is happening when booting. :)

Any device able to be booted in UEFI mode will have two entries in the mentioned built-in boot menu, standard option and UEFI option. You need to select the UEFI so it can boot in UEFI.

See if you can enter this menu with F12 and see what you have there as options to boot from.
F12 unfortunately doesn't do anything. 

When I turn on the computer I can only get to the error 0xc0000225 screen. From there, when I press enter or escape, I can get to the BIOS or boot to USB (if one is inserted). 

From the USB I can run the Win7 'Disc' or System Recovery 'Disc', but it never works because it says the wrong version no matter what I have tried — or I can run Ubuntu, Partition Wizard, etc.. seems anything that can boot to USB works fine.

So, tho I am no expert the solution seems to be to 
A) Get the Windows 'disc' version to work.
B) Fix the EFI stuff from within the BIOS screen or something I can run off the USB like Ubuntu or Partition Wizard. 

Thanks for your help. :)

---

### Post by darkod on 2012-09-29
1. For a windows rescue cd/usb to be able to repair UEFI installation you need to boot it in UEFI mode. If you boot it in non-UEFI it will always say the version is not correct even if it's the same.
2. If the boot files are missing or corrupt, you can't do much from the BIOS screen since you can't add boot files from BIOS.

The so called BIOS POST (Power On Self Test) starts first during power on but on new machines is very fast. Plus, many brands sometimes have some sort of quick boot activated and logo (picture) display. Also, the option to enter a boot menu is shown only during this first part of the boot.

If it already tries to boot some OS and shows you error, you are already too late to press any keys. But what you can do in BIOS to help you, is look carefully around and disable the options that sound like:
- logo/picture
- quick boot

You don't need the logo and you don't need fast boot when troubleshooting. On the contrary, you need to see the initial boot process displayed on the screen, that should also include the message what key to press for the boot menu.

Refer to the machine manual how to do some of these things in BIOS and how to use the boot menu too. It might help you to get it going.

---

### Post by Hotsuma on 2012-09-29
> **darkod said:**
> 1. For a windows rescue cd/usb to be able to repair UEFI installation you need to boot it in UEFI mode. If you boot it in non-UEFI it will always say the version is not correct even if it's the same.
This would certainly explain the problem, and it does seem logical here!

I don't understand how to make it so that it does boot in UEFI mode, however?

I mentioned in a previous reply when happened when I tried to follow those Samsung instructions. Is there a way to do this in Ubuntu, perhaps? 

It feels like it is so close but so far!

 
> **darkod said:**
> 2. If the boot files are missing or corrupt, you can't do much from the BIOS screen since you can't add boot files from BIOS.

The so called BIOS POST (Power On Self Test) starts first during power on but on new machines is very fast. Plus, many brands sometimes have some sort of quick boot activated and logo (picture) display. Also, the option to enter a boot menu is shown only during this first part of the boot.

If it already tries to boot some OS and shows you error, you are already too late to press any keys. But what you can do in BIOS to help you, is look carefully around and disable the options that sound like:
- logo/picture
- quick boot

You don't need the logo and you don't need fast boot when troubleshooting. On the contrary, you need to see the initial boot process displayed on the screen, that should also include the message what key to press for the boot menu.

Refer to the machine manual how to do some of these things in BIOS and how to use the boot menu too. It might help you to get it going.
I do see an Asus logo when it first starts and before the error message, but very briefly.
 
I went thru the BIOS options and there is a Post Logo Type selection but I can only choose to change it to animated from static, rather than disable it. 

However I will try F12 a bunch more times to see if it makes a difference. 

Thanks again!

---

### Post by Hotsuma on 2012-09-29
After several days, I solved the problem!

I will explain for the benefit of anyone who might have a similar problem in the future and finds this thread.

I followed all of the steps up to 6 on this page:
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)

The only difference was that 'Windows 7 USB/DVD Download Tool' did not result in a bootable USB, so I made it with a different program and proceeded with the rest of the directions and it resulted in a version of Windows 7 x64 on the USB which my EFI laptop approved of. Finally.

I used my old Windows Vista x32 system to make the bootable USB, so it did not need to be done on a x64 system, as I had read in several places.

So&#8230; after step 6, I tried the USB again and this time when I clicked to repair I received no error &#8212; it found the problem and that did the trick, one click, really easy.

Anyway thanks so much to everyone who took the time to help me, every little bit helped me become educated enough to find the solution! :)

Cheers.

---

### Post by oldfred on 2012-09-29
It is sure nice of Windows to make it easy to create a UEFI bootable flash drive. :)

---

### Post by Hotsuma on 2012-09-29
> **oldfred said:**
> It is sure nice of Windows to make it easy to create a UEFI bootable flash drive. :)
LOL, tell me about it! :D

It's insane how something so simple could be so complicated, so to speak. O_o

---

