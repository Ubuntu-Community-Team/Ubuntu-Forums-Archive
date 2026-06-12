---
title: "Unable to boot Ubuntu 12.04.2 in EFI mode, black screen (dual boot with Windows 8)"
date: 2013-05-17
forum: Installation &amp; Upgrades
---

### Post by veroslav on 2013-05-17
Hi,

I bought a new computer that came with Windows 8 pre-installed. Now I am trying to dual boot it with Ubuntu 12.04.2 (64-bit). Unfortunately, I am unable to boot the Ubuntu Live USB in EFI mode. As soon as I try (by selecting the "Try Ubuntu without installing" option from within GRUB), all I get is a black screen.

The computer is a HP Envy h8 - 1514eo.

I had a good read here before starting to do anything:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And here is what I did in order to try booting the Live USB in EFI mode:

1. I've disabled the following from Secure Boot Config boot menu:
  Legacy Support: Disable
  Secure Boot: Disable
  Fast Boot: Disable
  
2. From within Windows 8 power options, I've unchecked the following option:
  "Activate fast start (recommended)"
  
Finally, I selected to boot from the Live USB on the reboot:

Select boot device:
UEFI Boot Sources:
  UEFI: KingstonDataTraveler (this is my Live USB stick that I choose to boot from)
  Windows boot manager (this is the one for Windows 8)
  
After selecting the option above, I get the GRUB menu where I choose the following:

"Try Ubuntu without installing"

However, instead of Ubuntu starting, all I get is a black screen that is shown indefinately.

Also, if I enable "Legacy Support" option in Secure Boot Config, I am able to successfully run a Ubuntu live session when selecting the "Try Ubuntu without installing" option from the GRUB menu. Although I am more convinced that it is being launched in a non-EFI (legacy) way.

Does anyone knows what I have missed? Why am I unable to boot Live USB in EFI mode?

Also, would it be possible to install Ubuntu in the legacy mode and change it to EFI after the installation? According to the link above it should be possible. Any input on this is appreciated.

Thank you in advance.

Kind Regards,
Veroslav

---

### Post by oldfred on 2013-05-17
Is it dual video or just the nVidia? And from UEFI/BIOS can you set it to one or the other?

With nVidia you need nomodeset for live installer and first boot or until nVidia driver installed.
With UEFI boot you get the grub menu and need to use e to edit menu and change linux line from quiet splash to nomodeset.

Some systems also required other boot options.
 How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
BIOS live installer Boot Options
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

      
 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version:
apt-get update
sudo apt-get install linux-headers-generic

Some other HPs and what they did.

 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

---

### Post by veroslav on 2013-05-17
Thank you for your reply oldfred,

the video card is just nVidia GeForce GTX660 (it's a desktop) so no Optimus here.

I tried your suggestion to edit the GRUB parameters (replaced "quiet splash" with "nomodeset") but I've still got the black screen afterwards.

What I find strange (regarding to your suggestions regarding the boot parameters for nVidia) and also the missing kernel headers, is that when I enable "Legacy Support" in Secure Boot Config boot menu, and select Ubuntu Live USB to boot it in EFI mode, it actually boots to the Ubuntu live session after selecting the "Try Ubuntu without installing" from the same GRUB menu as above.

I still get the GRUB menu even after enabling legacy support and the live session is working without problems. Shouldn't I get the same problems as when legacy support is disabled (and efi boot is therefore forced) regarding the nVidia kernel options?

Also, your suggestion to install missing kernel headers would only be valid if I was already able to login to live session (in efi mode) but I never get that far?

I must admit that this is the first time I am attempting to install Ubuntu on an EFI system so I might be stating something obvious but I am lost at the moment. 

Will need some time to process all of the links you posted, it might be more clear when I done with that.

Thank you, any other tips are much appreciated.

P.S. I've also read about a guy having exactly the same issue with his Dell XPS I believe (cant fint the thread now thought) and the only thing that worked was to install in in legacy mode and then run Boot Repair in order to convert the installation to EFI afterwards. No kernel boot parameters helped him. Perhaps I am facing the same issue?

Kind Regards,
Veroslav

---

### Post by oldfred on 2013-05-17
Some Secure boot systems will only install in BIOS mode. And you can use Boot-Repair to convert by uninstalling grub-pc (BIOS) and installing grub-efi (UEFI). Not sure if the issue is really system or that now with UEFI and BIOS if it is some settings in BIOS and unless you use the right pixie dust is just does not work.

The only one that has not worked as far as I know is ASUS-K55N and I think users were able to install in BIOS mode but never could get video mode from UEFI to work even after install. Something about how UEFI reports video which is different than how BIOS reports video to system to boot from. Probably a bug in UEFI, but often Linux has to find boot parameters or other configurations to work around Windows designed systems. Most HPs seemed to work with some Boot-Repair type fixes.

UEFI boot uses grub, BIOS boot uses syslinux and you get the tiny icons at the bottom of the screen with the keyboard & user icons. Any key and f6 is then how you add nomodeset to boot.
I only have BIOS with nVidia but use grub to boot all my installs and just have to have nomodeset as a parameter as it just turns off monitor (Older versions) or goes to black screen.

Some only boot with secure boot on. Some also only boot the Windows efi file, but Boot-Repair does a file rename work around to make that work. But you have to get past video issue first. And until you have it installed you cannot easily install nVidia driver to liveCd. I think I did once and it normally want reboot which of course does nto work with live flash drive. But you can log out and log back in and get it to work (as least with BIOS). But you have to get in with low video mode first to even do that.

---

### Post by veroslav on 2013-05-17
Thank you for providing me with more details oldfred. It is getting late here (Sweden) so I will have to leave for tonight now.
I am too tired and don't want to make any unnecessary errors due to that, will take my time.

But as I understand, my main issue is the graphics and I will focus primarly on that tomorrow (got a whole day to play with it).

Will also try to re-enable "Secure Boot" and see if that renders in a different outcome. I disabled this one straight away but perhaps it is not necessary in my case.

Thanks again and I will post back after I've processed everything you've said and done some trial-and-error. :)

Kind Regards,
Veroslav

---

### Post by oldfred on 2013-05-17
When I look up your spec, it says you  have both. I do not know if Optimus is only a laptop trademark, but you may have something similar?
Do you have a setting in UEFI/BIOS to turn off one or the other video systems? I think it was a Dell laptop had something that seemed unrelated in Intel settings that worked.

---

### Post by veroslav on 2013-05-18
> **oldfred said:**
> When I look up your spec, it says you  have both. I do not know if Optimus is only a laptop trademark, but you may have something similar?
Do you have a setting in UEFI/BIOS to turn off one or the other video systems? I think it was a Dell laptop had something that seemed unrelated in Intel settings that worked.

Thank you for your reply. It does appear that I have the dreaded optimus system. I went into BIOS and found the following:

Integrated Video: Disable
PCI Graphics Configuration:
Nvidia VGA controller: Primary VGA device
Intel VGA controller: Non-boot device

Unfortunately I was a little too quick and changed the options to:

Integrated Video: Enable
PCI Graphics Configuration:
Nvidia VGA controller: Non-boot device
Intel VGA controller: Primary VGA device

After saving the changes in the BIOS and rebooting, I am unable to see anything, not even the BOOT menu. :(

I am really desperate for some help at the moment :(

Kind Regards,
Veroslav

---

### Post by veroslav on 2013-05-18
I managed to boot into Windows 8 after removing the Ubuntu Live USB stick. I am still unable to see the BIOS menu unfortunately.
Even after I select to reboot into UEFI menu from within Windows 8, it only displays a black screen on reboot.

I know that I am in fact inside the UEFI boot menu, as I can press "Esc" in order to select "Ignore changes and exit" option there and then press "Enter" to confirm. After I do that, Windows 8 boot normally.

Any help?

Thank you.

Kind Regards,
Veroslav

---

### Post by veroslav on 2013-05-18
So, I managed to fix the invisible boot menu problem (by searching for images of the Setup Utility menu and blindly assuming the same structure in my case, it worked!) :)

Now I can focus on my original issue: trying to boot Ubuntu 12.04.2 in EFI mode.

As oldfred suspected, I do indeed have a Optimus desktop (I thought it only applied to laptops but I was wrong).

How would I proceed now knowing that?

I think I should still focus on the following boot menu options, but I am not sure what the values should be (obviously NOT the ones I tried before):

Integrated Video: Disable
PCI Graphics Configuration:
Nvidia VGA controller: Primary VGA device
Intel VGA controller: Non-boot device

Also, I am still struggling to understand why Ubuntu Live session boots when I boot it in legacy mode but not in EFI mode? Are there any differences between EFI/Legacy boot mode in relation to whether a system is an optimus one or not? Is that the problem?

I am getting better and better understanding as I progress but I am still struggling with the black screen when booting live USB in EFI mode.

Any input is appreciated.

Thank you very much!

Kind Regards,
Veroslav

---

### Post by veroslav on 2013-05-18
Some more info:

Here are the outputs of lspci command while being logged in to Live session (legacy mode):

```
user@user-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation Device 1185 (rev a1)
```

I've also tried booting the Live session in EFI mode with the following kernel parameters:

```
"i915.modeset=1 nomodeset"
```

but no change, still getting a black screen immediately after choosing to try Ubuntu before installing from GRUB.

I've now shrunk Windows 8 partition and if nobody objects I plan to install Ubuntu in legacy mode and hope that Boot Repair can convert the installation to EFI after it is done.

Not sure what else to try :(

Regards,
Veroslav

---

### Post by oldfred on 2013-05-18
I only know nVidia as I have an older nVidia card not dual video. And nomodeset works for me. 
But some new systems seem to need nomodeset and other boot parameters. 
And some with Intel need the default screen size set as boot parameter.

Some have used these, but I so not know about your system specifically.
  Some systems need these boot parameters, but some were for Intel chip not nVidia?
ACPI=Off nomodeset 
pci=nomsi noapic
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
      acpi_osi=linux pci=noacpi
Also one used nolapic.

It is my understanding that UEFI does not use irq so any setting for that would not apply.

 [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

     But I am sure Boot-Repair can convert BIOS to UEFI but without knowing boot parameters that work, first boot may still be an issue. Once drivers are installed it should be ok.

 Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

Nvidia just released a new proprietary driver that partitally works with dual video. I gather it only runs in nVidia mode for performance, but not power savings with Intel chip. But if a desktop you may not care about power savings.

It may also need the newest kernel that will be in the next Ubuntu 13.10.

 Released 319.17 certified driver May 2013 only uses nVidia so power consumption high
[http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html)
Some discussion of limits of new nVidia driver with some Optimus support
[http://ubuntuforums.org/showthread.php?t=2142215](http://ubuntuforums.org/showthread.php?t=2142215)
Installing new nVidia driver 319.12 beta
[http://www.barunisystems.com/index.php/site/page?view=blog](http://www.barunisystems.com/index.php/site/page?view=blog)

---

### Post by veroslav on 2013-05-18
Thank you for helping me with your detailed explanations, it certainly is helping oldfred.

Let me try those boot parameter combinations you've posted and see what happens.

Just one more thing: what do you think about the BIOS graphics setup, which is currently:

Integrated Video: Disable
PCI Graphics Configuration:
Nvidia VGA controller: Primary VGA device
Intel VGA controller: Non-boot device

With these settings it appears that only nVidia card is enabled (which would explain the output from the lspci command I posted previously from within the live session). Is this OK or should I fiddle more with the settings, i.e.try to disable the nVidia card and only allow the Intel one?

Thank you.

Regards,
Veroslav

---

### Post by oldfred on 2013-05-18
I know nVidia more, but not sure my knowledge of my standalone older 9600GT applies in your case. I have seem some with the Intel have issues, but the Intel driver is supposed to just work. Intel only has one driver and it is the open source one that is standard. But they have been updating it and I do not know how up to date the Ubuntu version is.

What you do have to be careful of is which video mode you are in and then which boot parameters that mode needs as the are different. 
You may want to read the info on Optimus. I do not know if there is any info on booting, it may be more important after you have installed.
       nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)
Released 319.12 Beta April 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE)
Released 319.17 certified driver May 2013 only uses nVidia so power consumption high
[http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html)
Some discussion of limits of new nVidia driver with some Optimus support
[http://ubuntuforums.org/showthread.php?t=2142215](http://ubuntuforums.org/showthread.php?t=2142215)
Installing new nVidia driver 319.12 beta
[http://www.barunisystems.com/index.php/site/page?view=blog](http://www.barunisystems.com/index.php/site/page?view=blog)
> The problem was caused by another technology by Intel called the Integrated Network Interface Controller (NIC) that was conflicting with my USB controller that prevented my LiveUSB from working
Some BIOS
turn off discrete graphics
turn off "os optimus detection"

---

### Post by veroslav on 2013-05-18
I've tried all of the following:

ACPI=Off nomodeset 
pci=nomsi noapic
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
      acpi_osi=linux pci=noacp
video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

and none worked. I'm stunned! I'll do more reading about Optimus now from the thread link you've posted. I know a bit about Optimus as I already have a Dell laptop with nVidia/Intel combo, however, the only thing I needed to do in that case was to install Bumblebee after I've installed Ubuntu. It was only in order to disable nVidia card. I didn't had any issues with booting into the live session as I recall.

Still wondering why it works in Legacy/BIOS but not in EFI, this is the part I am most confused about :( I mean I am not passing any kernel parameters in this case and I am still able to reach live session desktop. And only nVidia card is active then.

Maybe I'm just unlucky, perhaps it is impossible to install in EFI in this case?

oldfred, would it help if I post command outputs about the available hardware? Any particular command? BIOS/UEFI screenshots?

Prepared to do anything in order to get it to boot!

P.S. Also tried with a Live DVD instead of USB this time around, same problem.

Thanks.

Regards,
Veroslav

---

### Post by oldfred on 2013-05-18
I am surprised it does not work.
The link I posted above to another user with a HP Envy 6 does not mention any video issues. Perhaps he did not have the dual video.

Do you have a setting for Intel NIC network controller? I do not see how that would matter but user said it did.

While a Dell Intel tech may be similar. see post #16
 Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)

Also is your UEFI/BIOS the current version from HP?

---

### Post by veroslav on 2013-05-20
Thank you for the support oldfred and sorry for my somewhat late reply.

I got sick of trial-and-error that lead me nowhere so I decided I would wipe Windows 8 completely and install Ubuntu 12.04 only (in BIOS mode).

When I tried to do this, I noticed that the computer also came with a SSD disk and my knowledge of installing and optimizations involving an SSD disk is non-existent.

At this point I simply gave up.

It is my father's computer (had it been my own I would have been more patient and would probably got it to work sooner or later). Unfortunately, my father does not share my patience so he decided he would be returning the computer to the store he bought it from.

I feel defeated and dissapointed to say the least. Never had any issues while installing before (BIOS) so I will need to do even more reading on the subjects (EFI and SSD) before I convince my father to buy a new computer and let me attempt an Ubuntu installation on it. Would have liked to keep experimenting at least for a few more days, but my father thought it was not worth the effort.

oldfred, I would like to thank you so much for sharing your knowledge and guiding me even though I didn't get there in the end. I am sure I will be asking more questions as soon as I try installing on some other computer in the future.

Thanks again.

Kind Regards,
Veroslav

---

### Post by oldfred on 2013-05-20
Sorry you could not get it to work. There just are so many new options withe UEFI and each vendor seems to have done some things differently. It may take a while before install with dual Video and SSD in UltraBooks becomes easier. Not sure if it will ever be "easy".

Some have just installed / (root) to SSD. A few have converted to just Ubuntu in BIOS mode. Some with just Ubuntu in UEFI mode with the two drives, or still dual boot but Ubuntu in the SSD or only on hard drive and re-enable the Intel SRT.

You are not the only one who gave up. But I think the only computer that only worked in BIOS mode was an Asus K55N and that seemed to boot in UEFI mode but never could get past video issues. Since it worked in BIOS mode and other computers do work in UEFI, then it is Asus's UEFI not reporting video correctly. But it usually is up to Linux developers to work around bugs in other systems.

---

