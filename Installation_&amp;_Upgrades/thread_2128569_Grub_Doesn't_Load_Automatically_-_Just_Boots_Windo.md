---
title: "Grub Doesn't Load Automatically - Just Boots Windows - Boot Repair Didn't Help"
date: 2013-03-23
forum: Installation &amp; Upgrades
---

### Post by Phugoid on 2013-03-23
Hi there,

So, I just installed Ubuntu 12.10 and then Windows 8 on my laptop, which runs UEFI. Both installations went fine, but it boots straight to Windows without the grub loader opening to let me select my OS.

So I installed boot-repair and ran the recommended repair from an Ubuntu Live Session and that went smoothly and finished without errors.

But grub still doesn't load automatically, and instead, Windows just boots. If I press F9 at start up it enters the boot device options, and there's an option there for something to do with Ubuntu, and when I select that, it then loads Grub from which I can boot from either Windows or Ubuntu. But this grub menu does not load automatically - so perhaps it's the case that my grub loader is on the wrong partition or something like that?

Anyway, I'd like to set Ubuntu to the default OS and I'd like to have my grub menu appear by default when I startup instead of having to press F9 to manually select a different boot device.

Here's my pastebin from boot-repair: [http://paste.ubuntu.com/5640845/](http://paste.ubuntu.com/5640845/)

Any help greatly appreciated!!

---

### Post by darkod on 2013-03-23
I don't use uefi boot but as far as I have understood, in uefi boot it's the uefi manager running the show, not grub2. So, you might need to make an entry for ubuntu, and then using the uefi manager you boot either windows or ubuntu. It sort of replaces grub2.

---

### Post by Phugoid on 2013-03-23
> **darkod said:**
> I don't use uefi boot but as far as I have understood, in uefi boot it's the uefi manager running the show, not grub2. So, you might need to make an entry for ubuntu, and then using the uefi manager you boot either windows or ubuntu. It sort of replaces grub2.

What is the UEFI manager and how do I access it?

---

### Post by darkod on 2013-03-23
You will have to check the documentation about your machine/board for that. I'm not sure how it called exactly either. It might be the menu you enter with F9 if it allows you to create an ubuntu entry.

Basically that's the bootloader. Once you have it working, inside ubuntu in grub2 you might as well disable os-prober since you don't need it to detect windows. You will boot the OS you want to boot from the uefi manager.

---

### Post by oldfred on 2013-03-23
Your f9 is a one time boot key. As Darko says you have to go into UEFI/BIOS and select ubuntu as boot and then it will be default.

Most systems keys are listed here:
 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

In grub menu you have this entry. Does it take you to UEFI menu?


menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
     fwsetup 
}

---

### Post by Phugoid on 2013-03-23
> **oldfred said:**
> Your f9 is a one time boot key. As Darko says you have to go into UEFI/BIOS and select ubuntu as boot and then it will be default.

Most systems keys are listed here:
 UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

In grub menu you have this entry. Does it take you to UEFI menu?


menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
     fwsetup 
}

Hi there,

I've tried F10 which takes me to BIOS setup, but there's no option there to configure any UEFI settings, apart from to switch Legacy Support on/off. It doesn't let me point to any particular OS as a default start up or anything like that.

The System Setup option just takes me to a menu which lists the F keys and various submenus associated with them - There's F9 and F10, which as I've said, don't help. There's one on diagnostics which lets you do memory and hdd test. But nothing that seems useful to solve my issue of not having grub load as default.

---

### Post by oldfred on 2013-03-23
Because it is UEFI it will have a setting somewhere perhaps a different screen, or in some submenu. It should be the same settings you see with the one time boot key, just that it sets it as the default.

---

### Post by Phugoid on 2013-03-24
> **oldfred said:**
> Because it is UEFI it will have a setting somewhere perhaps a different screen, or in some submenu. It should be the same settings you see with the one time boot key, just that it sets it as the default.

There's definitely nothing like that. From the main menu (pressing ESC after boot, or loading "System Setup" from grub menu), I get the following options:

F1 System Information
F2 System Diagnostics
F9 Boot Device 
F10 BIOS Setup
F11 System Recovery

F1 just gives me a list of info about my hardware, F2 just gives me the option to do a memory/hdd test, F9 just lets me change the boot device on a one-time basis, F11 is just standard System Recovery.

F10 just enters me into a BIOS where the only thing I can change about the boot is the boot order - but the all I can do there is change the boot order between USB, Network Card, OS Manager, Internal CD Drive and External CD Drive.

I take it the OS Manager is what I want to get into and edit, but there's no option to do so.

I did format my whole harddrive at one point a few days ago, and so I might well have deleted a partition with a UEFI menu. But (A) seems a bit screwed up that something so fundamental (and supposedly to replace BIOS) wouldn't be placed on ROM, but instead on a non-secure HDD partition, and (B), even if I've done that surely there's some way to get it back????

---

### Post by oldfred on 2013-03-24
Some have posted different screens. 
You can use camera, shrink photos to screenshot size, and under the advanced editor use the paperclip icon to attach the screenshots.
It may be under a setting like select hard drive.

---

### Post by Phugoid on 2013-03-25
> **oldfred said:**
> Some have posted different screens. 
You can use camera, shrink photos to screenshot size, and under the advanced editor use the paperclip icon to attach the screenshots.
It may be under a setting like select hard drive.

Hi there, I have attached my screen shots of the options available to me through the BIOS (some in this post, more in the posts below!).

As I said I am given the options of (see MAINMENU.JPG):

F1 System Information
F2 System Diagnostics
F9 Boot Device Options
F10 BIOS Setup
F11 System Recovery

Pressing F1 gives me basic hardware information about my computer (SYSINFO.JPG). F2 gives me tests to run on my memory/hdd, etc - there are some bios related options there, but they're just to update or rollback the bios (DIAGNOSTIC.JPG). Pressing F9 (see BOOTMGR.JPG) gives me the one-time option to choose my boot - and thankfully I can boot the grub bootloader from there (see GRUBLOAD.JPG). There are multiple options on the grub bootloader, but all of them either run Windows, or Ubuntu, or take me back to the screen of MAINMENU.JPG.

In the BIOS Setup I have 4 tabs - Main (MAIN.JPG), Security (SECURITY.JPG), System Configuration (SYSCONFIG1.JPG) and Exit (EXIT.JPG).

In SYSCONFIG1.JPG I can select boot options (SYSTEMCONFIG2.JPG). In there I can change boot orders between the 5 options given, but none of them replicate the option I have from pressing F9 - the one to load the bootloader!!!!

So, what now?!

[ATTACH=CONFIG]240561[/ATTACH][ATTACH=CONFIG]240560[/ATTACH][ATTACH=CONFIG]240559[/ATTACH][ATTACH=CONFIG]240558[/ATTACH][ATTACH=CONFIG]240557[/ATTACH]

---

### Post by Phugoid on 2013-03-25
More pics, see post above:

[ATTACH=CONFIG]240562[/ATTACH][ATTACH=CONFIG]240563[/ATTACH][ATTACH=CONFIG]240564[/ATTACH][ATTACH=CONFIG]240565[/ATTACH][ATTACH=CONFIG]240566[/ATTACH]

---

### Post by oldfred on 2013-03-26
In your bootmgr.jpg, you have two ubuntu entries. If you move ubuntu to the top, it should default to booting to the grub menu. Not sure why Ubuntu & ubuntu or what difference is?

---

### Post by Phugoid on 2013-03-26
> **oldfred said:**
> In your bootmgr.jpg, you have two ubuntu entries. If you move ubuntu to the top, it should default to booting to the grub menu. Not sure why Ubuntu & ubuntu or what difference is?

But bootmgr.jpg is what I get when I press F9... I.e. It is only a temporary boot selection. That screen doesnt allow me to permanently change the boot order, and the ubuntu option doesn't show up in the bios boot settings where I can permanently change the order.

---

### Post by oldfred on 2013-03-26
Following the UEFI screen takes me to this page that your system configuration is the correct screen. You do have the UEFI boot order settings. If you click on those what happens? Does it open more, or allow changes?

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en#N80](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en#N80)

---

### Post by Phugoid on 2013-03-26
Nevermind, I just took the laptop back and got a full refund.

This new EFI **** is not worth the trouble. I've been dual booting windows and Linux for a good while on previous machines and it has never been an issue - there's no way in hell I'm going to spend 3 weeks just trying to get the OSes to behave nicely with one another.

---

