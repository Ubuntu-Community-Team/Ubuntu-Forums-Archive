---
title: "Dual boot with windows 8, multiple ubuntu installs"
date: 2012-11-05
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2012-11-05
I just brought a new computer and it is being shipped.  I have a 2TB HD with windows 8 installed.  I'm planning on doing a dual boot with either Ubuntu 12.4 or 12.10.  I would like to have a stable install to keep and use, but would love to try other flavors of linux and or new releases.

The question is how do I partition the HD to allow this?  

I currently have a dual boot with windows and Ubuntu 10.10.

Dennis

---

### Post by oldfred on 2012-11-05
If new computer has Windows 8 pre-installed it will have the very new Secure Boot feature that Microsoft requires vendors to enable in UEFI.

You supposedly have a way to turn secure boot off. And Ubuntu's latest grub2 2.00 is supposed to install to secure boot systems.

Secure Boot
[http://www.phoronix.com/scan.php?page=news_item&px=MTEyNDY](http://www.phoronix.com/scan.php?page=news_item&px=MTEyNDY)
[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)

[http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms](http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms)

You also have gpt partitions which mean all partitions are primary, which simplifies partitioning.
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell]("https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell")

With Ubuntu you have to use the 64 bit version and boot installer USB or CD in UEFI mode.

---

### Post by claven123 on 2012-11-06
So, I should have opted to have Windows 7 instead.....

Oh, I'll have a bit of fun getting this to work... but that's makes it interesting.

I'm sure I'll be back to let everyone know how this goes...  

I've got some reading to do....

D

---

### Post by lvgandhi on 2012-11-06
> **oldfred said:**
> If new computer has Windows 8 pre-installed it will have the very new Secure Boot feature that Microsoft requires vendors to enable in UEFI.

You supposedly have a way to turn secure boot off. And Ubuntu's latest grub2 2.00 is supposed to install to secure boot systems.

Secure Boot
[http://www.phoronix.com/scan.php?page=news_item&px=MTEyNDY](http://www.phoronix.com/scan.php?page=news_item&px=MTEyNDY)
[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/](http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/)

[http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms](http://www.linuxfoundation.org/publications/making-uefi-secure-boot-work-with-open-platforms)

You also have gpt partitions which mean all partitions are primary, which simplifies partitioning.
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell]("https://help.ubuntu.com/community/UEFIBooting#UEFI%20Shell")

With Ubuntu you have to use the 64 bit version and boot installer USB or CD in UEFI mode.

I also have windows 8 in my new Acer Aspire V5-571P-6815 laptop.
It has EFI/GPT system for booting and partition.
When I tried to boot my KUBUNTU 12.04lts amd64 dvd in UEFI mode, it failed to boot. But it booted in legacy mode. Is there any seperate iso to boot in UEFI mode?

---

### Post by grahammechanical on 2012-11-06
As referred to by oldfred you need 12.10 not 12.04. See, this link:

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/]("http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")

I cannot help but say it. As windows 8 machines are very, very new, and Ubuntu 12.10 is very, very new, you are now entering the realm of experimentation. You are about to become an expert on installing Ubuntu 12.10 on a Windows 8 machine.

There is less trouble when installing Linux on hardware that is not the very latest. This has been common knowledge for years.

Regards.

---

### Post by oldfred on 2012-11-06
@   	lvgandhi
Better to have your own thread.
Is this a pre-installed Windows 8, so the UEFI has the security lock down as required by Windows? I believe you can either turn that off or use the new 12.10 which has grub2 2.00. They will update 12.04 with grub2 2.00 in January with the next point release.

---

### Post by lvgandhi on 2012-11-06
> **grahammechanical said:**
> As referred to by oldfred you need 12.10 not 12.04. See, this link:

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/]("http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")

I cannot help but say it. As windows 8 machines are very, very new, and Ubuntu 12.10 is very, very new, you are now entering the realm of experimentation. You are about to become an expert on installing Ubuntu 12.10 on a Windows 8 machine.

There is less trouble when installing Linux on hardware that is not the very latest. This has been common knowledge for years.

Regards.

> **oldfred said:**
> @   	lvgandhi
Better to have your own thread.
Is this a pre-installed Windows 8, so the UEFI has the security lock down as required by Windows? I believe you can either turn that off or use the new 12.10 which has grub2 2.00. They will update 12.04 with grub2 2.00 in January with the next point release.

Thanks for the responses. I will start a new thread.

---

### Post by claven123 on 2012-11-06
It seems I just use the 64bit version of 12.10 and then I'm ok with the install.

The other question is... can I set up an 'area' for data etc.... before I install or set up the partitions.

I'm a bit rusty on partitions, I will have to review that stuff again (and how it pertains to win 8 and GPT etc...)


Thanks for the information.

D

---

### Post by teastman on 2012-11-24
> **claven123 said:**
> It seems I just use the 64bit version of 12.10 and then I'm ok with the install.

The other question is... can I set up an 'area' for data etc.... before I install or set up the partitions.

I'm a bit rusty on partitions, I will have to review that stuff again (and how it pertains to win 8 and GPT etc...)


Thanks for the information.

D

Hi! Teastman here,.

Has this issue been favorably resolved with a Dual Boot/ Win 8 machine? Do you get the typical Grub OS choice at boot up now? What were the BIOS settings you needed to end up with?

I may be facing the same issue soon.
thx.

---

### Post by claven123 on 2012-11-25
To be honest its a nightmare....

At this point I WOULD not give advice to anyone to try ubuntu for the first time if they are going to dual boot win 8 and Ubuntu 12.10.

This is a sad, sad day for Ubuntu.... and linux.    

D

---

### Post by lvgandhi on 2012-11-25
I am multi-booting win8, kubuntu 12.04, wheezy and mint maya kde using rEFInd as boot manager.

---

### Post by gdubz on 2012-12-24
[FONT=Calibri][SIZE=3]For general reference,  this is how I achieved dual boot with vendor (HP)  installed Windows 8 / Ubuntu 12.10 on the machine that’s in the linked data sheet,  with manufacturing date 08/12:[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[[FONT=Calibri][SIZE=3]http://www.shopping.hp.com/shopping/pdf/c2h70ua.pdf[/SIZE][/FONT]]("http://www.shopping.hp.com/shopping/pdf/c2h70ua.pdf")
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri][SIZE=3]The MB chipset is HM77. (35w Ivy Bridge i5 Dual Core Processor).  [/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[COLOR=#333333][FONT=Tahoma]In UEFI (F10 menu):[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]• •Disable Secure Boot. I could not achieve boot in any configuration with it on. [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]• •UEFI boot scheme (not Legacy BIOS). I tried Legacy mode, and can boot from disk, but not from an installation on the hard drive. UEFI flies right by it during boot every way I tried with it on. [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma][/FONT][/COLOR] 
[COLOR=#333333][FONT=Tahoma]In Ubuntu:[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]• •/Boot=EFI, /=EXT4, /Home=EXT4, SWAP=swap. [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma] [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]With this configuration I can boot with user intervention during the boot sequence: [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]1) During the boot sequence, select F9 to obtain Boot options in UEFI (BIOS) [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]2) In UEFI / BIOS, select the available Ubuntu Linux 2.6.32-21 option and proceed. [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]3) Ubuntu GRUB boot option screen is now available. Select preferred option and proceed. [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]4) I'm in.[/FONT][/COLOR]

---

### Post by IsaacJGL on 2012-12-24
I kind of figured that since the windows 8 laptop/tablet just came out, and that [I don't think] there are any very new updates for linux that are as new as windows 8, that it wouldn't be compatible with linux.

Much like how apple computers can't use different operating systems for stupid money reasons.

---

