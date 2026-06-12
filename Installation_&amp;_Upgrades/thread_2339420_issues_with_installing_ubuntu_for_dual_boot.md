---
title: "issues with installing ubuntu for dual boot"
date: 2016-10-08
forum: Installation &amp; Upgrades
---

### Post by technodactyl on 2016-10-08
I've been trying to install ubuntu on my laptop alongside win10, but no luck in getting it to work.

System: Dell Inspiron 7559 (64-bit) with BIOS mode: UEFI, BIOS version 1.1.7, SMBIOS version 3.0.
USB Stick: SanDisk Cruzer Blade 8GB

I had tried Ubuntu GNOME on this same laptop, and it seemed to work perfectly the first time. Then i decided to shrink the C: drive (by 19.5GB) so that i wouldn't have to get rid of Windows, as i would need it for other stuff.

But, now whenever i try booting into ubuntu, all it does after the GNU GRUB screen is show the boot loading logo which freezes after a while.

I tried other versions of ubuntu, like Lubuntu, but even that gives me the same problem.

I thought the problem may lie in the USB stick i'm using, but that boots just fine on my iMac -- both versions.

I tried formatting the USB Stick countless times, but i see no change.

I've just been trying to install ubuntu to learn and get myself started with linux, but i've been frustrated with this.:(

I'm super-new to linux, like, not-been-able-to-use-it-fully new to linux.

Please help a lost boy out?

---

### Post by Bucky Ball on 2016-10-08
*Thread moved to **Installations and Upgrades**.*

Better support here. Welcome. Are you sure you have hibernation switched off in Windows 10? You have to boot into Win to switch it off I think. 

Are you booting the UEFI install of Ubuntu? Win10 will be in UEFI mode, so boot to the BIOS and switch off faststart and secureboot and choose the USB with (EFI) or something like it next to it as first boot device. 

You can also choose it by hitting F12 after boot and that gets you to a boot device menu on a lot of machines.

Hope that helps.

---

### Post by colmax on 2016-10-08
Have you tried running your install from dvd instead of usb memstik
Consolidating free space is advisable before shrinking volumes
Cheers

---

### Post by deadflowr on 2016-10-08
> **colmax said:**
> Have you tried running your install from dvd instead of usb memstik
Consolidating free space is advisable before shrinking volumes
Cheers

That would require it have a dvd drive.

---

### Post by colmax on 2016-10-08
Indeed :)
External dvd/bluray normally run off usb but seems the mbr makes a difference
sometimes a different angle works :)
Cheers

---

### Post by technodactyl on 2016-10-09
i tried that, but hibernate seems to be off everywhere. Trying the BIOS option now.

---

### Post by technodactyl on 2016-10-09
> **Bucky Ball said:**
> *Thread moved to **Installations and Upgrades**.*

Better support here. Welcome. Are you sure you have hibernation switched off in Windows 10? You have to boot into Win to switch it off I think. 

Are you booting the UEFI install of Ubuntu? Win10 will be in UEFI mode, so boot to the BIOS and switch off faststart and secureboot and choose the USB with (EFI) or something like it next to it as first boot device. 

You can also choose it by hitting F12 after boot and that gets you to a boot device menu on a lot of machines.

Hope that helps.


I managed to disable secure boot and fast start. 

It looked like it was working, because both lubuntu and ubuntu gnome worked the first time i tried them, 

but then i tried to install them, and then they showed the original problem.

---

### Post by Bucky Ball on 2016-10-09
Think we're getting somewhere. When you boot the install media, when you get to the purple screen with the icon and the bar, hit F6. Should take you to a screen with some options when you hit F6 again (from memory, haven't needed to do it in awhile). From those options, choose 'nomodeset'.

Taking a punt on which GPU you have here, so fingers crossed. If it doesn't work, no harm done. Reboot, back to square one.

If the above doesn't get you to the option, the main thing is to be running with that option. You haven't installed yet I'm presuming? Can you get to 'Try Ubuntu' rather than 'Install Ubuntu'?

PS: You are choosing the USB with [UEFI] next to it for the install? You MUST install Ubuntu in UEFI mode as Win10 will be. Double check that it is, but if pre-installed it will be definitely.

---

### Post by oldfred on 2016-10-09
If you have a system with Windows 8 pre-installed then it is UEFI. And you should not be getting purple screen, but grub menu, if you boot install media in UEFI boot mode.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If re-installing best to always use Something Else and choose the existing / (root) again as new root. Otherwise auto install may ignore that install and shrink NTFS again for new install.

       
 One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
[/URL]
 [http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html](http://www.everydaylinuxuser.com/2015/11/how-to-install-ubuntu-linux-alongside.html)
SSD & HDD, but I prefer full backup before deleting recovery partitions
[http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html](http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html)
But I suggest using Windows to shrink Windows if installing on same drive and reboot Windows first. 
But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html) 


[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by technodactyl on 2016-10-10
> **Bucky Ball said:**
> Think we're getting somewhere. When you boot the install media, when you get to the purple screen with the icon and the bar, hit F6. Should take you to a screen with some options when you hit F6 again (from memory, haven't needed to do it in awhile). From those options, choose 'nomodeset'.

Taking a punt on which GPU you have here, so fingers crossed. If it doesn't work, no harm done. Reboot, back to square one.

If the above doesn't get you to the option, the main thing is to be running with that option. You haven't installed yet I'm presuming? Can you get to 'Try Ubuntu' rather than 'Install Ubuntu'?

PS: You are choosing the USB with [UEFI] next to it for the install? You MUST install Ubuntu in UEFI mode as Win10 will be. Double check that it is, but if pre-installed it will be definitely.


I've been trying to use Ubuntu GNOME, so i'm guessing that the first part should be the same with the grey screen and the Ubuntu GNOME logo. Right...?

Anyway, nothing comes up when i press F6.

Try Ubuntu actually worked once when i started it up today, but then i checked if install Ubuntu worked, but that didn't,

and ever since, neither does Try Ubuntu.

---

### Post by Bucky Ball on 2016-10-10
This is the procedure from [this thread]("https://ubuntuforums.org/showthread.php?t=1613132"):

[QUOTE=P4man]If you boot ubuntu from a livecd (or USB stick), right after the bios splash screen you will get a purple screen with a keyboard logo at the bottom:

Press any key at that moment to access a menu. Select your language with the arrow keys, press enter and you will see this menu:

If you press the F6 key, a menu at the bottom will open allowing you to set kernel options with the space bar or enter key.[/QUOTE]

It might be slightly different in Gnome but not much. The main thing is you want to try with the nomodeset option. Have a look around for how you set this on the livecd for Gnome if the above isn't working for you.

---

### Post by technodactyl on 2016-11-18
> **Bucky Ball said:**
> This is the procedure from [this thread]("https://ubuntuforums.org/showthread.php?t=1613132"):



It might be slightly different in Gnome but not much. The main thing is you want to try with the nomodeset option. Have a look around for how you set this on the livecd for Gnome if the above isn't working for you.

Hey, I'm back.

Sorry i couldn't pay attention to this thread and almost abandoned it; i was busy with exams and other stuff which took a lot of time.

I've given up trying to install ubuntu on my laptop's internal hard drive.
 HOWEVER, i've been doing some research because i want to use/learn linux.

I was wondering if it would be feasible to install ubuntu on an external hard drive.

Thee initial problem has still not been resolved, though. 
I still can't boot into ubuntu on my laptop.

I don't receive the purple accessibility screen; my computer boots in UEFI, so it takes me directly to the GRUB screen.

Please help me on this?

---

### Post by Bucky Ball on 2016-11-18
Have you tried running with the nomodeset option, as suggested? I linked to how in my last thread. What makes you think this is going to be any different on an external drive? If Ubuntu is not playing with your hardware, i.e. graphics, then that won't make any difference at all. Actually, you'll probably find yourself screwing around trying to get an install on an external drive to play nice more so that an internal dual-boot.

Try the nomodeset option if you haven't (and if you have you haven't mentioned anything about it) and report back.

> I don't receive the purple accessibility screen; my computer boots in UEFI, so it takes me directly to the GRUB screen.

And? It doesn't boot into Ubuntu ? Have you got it installed on the internal drive? What is the issue with not seeing the purple screen? Please clarify. Thanks. ;)

If is unclear what your issue is not, though.

---

### Post by oldfred on 2016-11-18
You can install to an external, I have both BIOS & UEFI full installs on flash drives.

But UEFI is a bit more complex and that makes installing to an external more complex.

Generally you must gpt partition in advance & include the ESP - efi system partition. But when you install grub will only install to the ESP on sda drive or internal drive. Then copy files from sda's ESP to external's ESP twice, once to /EFI/ubuntu and once to /EFI/Boot. Then rename shimx64.efi in /EFI/Boot to bootx64.efi. That is because UEFI boots externals from /EFI/Boot/bootx64.efi. And the copy of shim is hard coded to find other files in /EFI/ubuntu. So both copies needed.

---

### Post by technodactyl on 2016-11-23
> **Bucky Ball said:**
> This is the procedure from [this thread]("https://ubuntuforums.org/showthread.php?t=1613132"):



It might be slightly different in Gnome but not much. The main thing is you want to try with the nomodeset option. Have a look around for how you set this on the livecd for Gnome if the above isn't working for you.

Ok, i think this should work.

I tried nomodeset, and i can FINALLY boot into ubuntu.

BUT, now it looks really weird...


[ATTACH=CONFIG]272322[/ATTACH]

Everything's stretched out and flattened, just barely appealing.

Is there any way to fix this?


==================================================================================================================================

EDIT: Also, this

[ATTACH=CONFIG]272335[/ATTACH]

Is this a problem? Should it be there?

I'm not really sure, it might be nothing, but just to check

---

### Post by oldfred on 2016-11-23
I updated my Skylake system with instructions here by mc4man, but it still gave an error on a driver. It seems it cannot tell Skylake from Kabylake and the error is a missing Kabylake driver which my Skylake should not have. Or ignore some errors.

 instruction of installing "i965-va-driver" (despite is not mentioned "skylake") and other package gstreamer works:
[https://ubuntuforums.org/showthread.php?t=2328993](https://ubuntuforums.org/showthread.php?t=2328993) 

      
 Intel Driver updates
[https://ubuntuforums.org/showthread.php?t=2342137](https://ubuntuforums.org/showthread.php?t=2342137)
Updates often needed for Skylake
[https://01.org/linuxgraphics/intel-linux-graphics-firmwares](https://01.org/linuxgraphics/intel-linux-graphics-firmwares)

---

### Post by technodactyl on 2016-11-24
> **technodactyl said:**
> Ok, i think this should work.

I tried nomodeset, and i can FINALLY boot into ubuntu.

BUT, now it looks really weird...




Everything's stretched out and flattened, just barely appealing.

Is there any way to fix this?


==================================================================================================================================

EDIT: Also, this



Is this a problem? Should it be there?

I'm not really sure, it might be nothing, but just to check

Ok, i think i fixed it.

Instead of "nomodeset", i used "nouveau.modeset=0", and the graphics are how they're supposed to be.

I'm still in "Try Ubuntu" though; i still have to install it, which i'll probably do when i get the external drive.
I'll know for sure whether or not this issue is fixed after i install it. I'll get back once that happens.

Also, is there anything that i can do so that i don't have to insert the nomodeset line every time?

---

### Post by oldfred on 2016-11-24
That turns off the nVidia open source driver.

Normally you then install the nVidia proprietary driver from the Ubuntu repository unless you have a very new like 10x0 series and then you need to add a ppa. 

If you already installed a nVidia driver you must be sure to purge before attempting another, as then you get conflict. New driver does not uninstall old. Or if you have installed bumblebee you must purge that & related drivers.

---

### Post by Bucky Ball on 2016-11-24
When you install you will be installing a fresh slate. As oldfred is saying I think, use the option you are using now to install and that will get you through it. Once you are installed, yes, you can actually make that command permanent so you don't need to add it every time you boot Ubuntu, but better to install the NVidia drivers for your card once you are installed. Waste of time attempting that when you're running a live session because ... why? If you reboot they are gone and when you install they will be gone and you'll need to install again.

You could see the option you are using as a workaround to get Ubuntu installed. Once installed, install the NVidia drivers using 'Additional Drivers' or a PPA, as suggested (only for very new GPUs).

---

### Post by technodactyl on 2016-11-26
One more thing:

I was trying other versions of Ubuntu (Kubuntu, Xubuntu, Studio)

and for some reason, the icons and windows are REALLY small.

I don't know what is causing this; because Ubuntu Gnome looks just fine.

Any thoughts?

---

### Post by Bucky Ball on 2016-11-26
> **technodactyl said:**
> One more thing:

I was trying other versions of Ubuntu (Kubuntu, Xubuntu, Studio)

and for some reason, the icons and windows are REALLY small.

I don't know what is causing this; because Ubuntu Gnome looks just fine.

Any thoughts?

Yes. This is a totally new question and is off-topic as it bears no relation to your original support request. ;)

> I've been trying to install ubuntu on my laptop alongside win10, but no luck in getting it to work ... whenever i try booting into ubuntu, all it does after the GNU GRUB screen is show the boot loading logo which freezes after a while.

Consequently, for the best chance of support with it, start a new thread rather than burying it here on a thread that was started ... two months ago about something else and is now over twenty posts deep?

You will increase your chances greatly. Good luck. :)

---

### Post by technodactyl on 2016-11-29
I did it.

I recently got my external hdd and have finally booted into ubuntu-Gnome. Startup time is still slow, but everything else seems to be in order. I've also installed the latest nVidia driver.

Thanks to you guys so much for your help and assistance.
Cheers

---

