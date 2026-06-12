---
title: "Installing Ubuntu 21.10 over Mint 20.2 in dual boot"
date: 2021-11-17
forum: Installation &amp; Upgrades
---

### Post by nipplewise on 2021-11-17
Do I click now on the "-" sign of ```
dev/sda6 
```at this point of the installation?

I want to install Ubuntu over Mint and maintain Windows 10; all Mint files are backed up.

Is the *Device for boot loader installation:* option correct? I have only one SSD.

---

### Post by nipplewise on 2021-11-17
OK I clicked on "-" of */dev/sda6* and then on the "+" of *free space*.

Is this and what you can see in the picture correct so far?

---

### Post by Dennis N on 2021-11-17
I think the "-" is to delete that selected partitiion. You don't want to do that.

---

### Post by Dennis N on 2021-11-17
> **nipplewise said:**
> OK I clicked on "-" of */dev/sda6* and then on the "+" of *free space*.

Is this and what you can see in the picture correct so far?

OK, since you are deleting the old one, you are now creating a replacement partition. The dialog looks correct. 
The more direct way is to click "Change" and then specify to use the existing partition as /. But you should get the same result.

---

### Post by nipplewise on 2021-11-17
Thanks a lot.

Can I safely ignore this?

---

### Post by nipplewise on 2021-11-17
OK, I found this:

*So, the error is exactly what it says: you're trying to install Ubuntu in UEFI mode without the necessary EFI System Partition.*

*Since you're trying to install alongside Windows 10, and your Windows 10 is not in UEFI mode (otherwise you'd already have an ESP) you don't want to install Ubuntu in UEFI mode, either. The mode that Ubuntu installs in is determined by the way that you boot the installation media: one way is UEFI mode (which would probably be part of the label when you're choosing it from the boot menu) and the other way is the (much) older BIOS mode. **Boot your installation media in BIOS mode, and it will install Ubuntu in BIOS mode.** Then it won't need (or use) an ESP: Grub (the Linux bootloader) will be installed into the Master Boot Record of your drive, and will then chainload the Windows bootloader. In UEFI mode both the Linux bootloader and the Windows bootloader would be in the ESP.*

*Since OEM installs of Windows 10 are done in UEFI mode, I guess the Windows install was one that you did yourself.*

Source: [https://ubuntuforums.org/showthread.php?t=2436760](https://ubuntuforums.org/showthread.php?t=2436760).

I did install Windows 10 myself.

The Ubuntu USB drive is created using *USB Image Writer* of Linux Mint.

But it seems to me that the BIOS options are set correctly.

*USB UEFI BIOS Support [Disabled]* does not allow me to boot from the USB drive so I have to keep it to [Enabled].

*UEFI/Legacy Boot* is already set to [Legacy Only].

---

### Post by oldfred on 2021-11-17
If you have UEFI hardware, you should have installed Windows in UEFI boot mode. At least plan on long term reinstalling it.
Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since 2012.
But conversion from MBR partitioning to gpt partitioning will erase drive, so you have to have good backups & plan ahead for that type of conversion.

The UEFI/BIOS setting for boot mode is only for your installed system.
How you boot install media, UEFI or BIOS is then how it installs.
Your UEFI boot menu for booting USB flash drive should have two boot options, one clearly UEFI as UEFI [noparse]UEFI:XXXX[/noparse]  and other just XXXX which then is BIOS boot. The XXXX may be label or description of flash drive, mine says PMAP.
Some tools like Rufus only create USB live installer in one mode or the other, so how you create installer then is important as UEFI boot will only have that one option.

But if you have UEFI Secure boot on, the BIOS/Legacy/CSM option is not available and you may even have to turn on a UEFI setting to allow USB boot as USB booting is not considered Secure. With Secure boot off, either boot should be available, but you may still need the USB boot setting with some systems.

---

### Post by Dennis N on 2021-11-17
sda5 which is formatted FAT32 looks like an EFI system partition - but it may not be used. Your boot options in post #6 say "Legacy Only" meaning the OS will only boot BIOS installs. So Mint must have been installed in BIOS mode, as well as your Windows install. 

You should install Ubuntu as BIOS mode, which means you have to boot the USB installer in bios mode. In the USB boot up menu, it can have both options - select the one without mention of UEFI.

---

### Post by nipplewise on 2021-11-17
Thank you both!

I will ponder about my next step.

---

### Post by MAFoElffen on 2021-11-17
Not to be the Devil's advocate... Too late for this, but I have curiosity kinds of questions...

Background... Mint is an Ubuntu derived child distro of Ubuntu. It is already based on and Ubuntu core under the hood. The big plus of Linux, is that it is customizable and pieces interchange...

If you were tired of Cinnamon Desktop, why didn't you just install ubuntu-desktop onto your old/existing Ubuntu based installation? Was it just time to start out with a fresh/clean install?

---

### Post by nipplewise on 2021-11-18
> **oldfred said:**
> If you have UEFI hardware, you should have installed Windows in UEFI boot mode. At least plan on long term reinstalling it.
Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since 2012.
But conversion from MBR partitioning to gpt partitioning will erase drive, so you have to have good backups & plan ahead for that type of conversion.

The UEFI/BIOS setting for boot mode is only for your installed system.
How you boot install media, UEFI or BIOS is then how it installs.
**Your UEFI boot menu for booting USB flash drive should have two boot options, one clearly UEFI as UEFI [noparse]UEFI:XXXX[/noparse]  and other just XXXX which then is BIOS boot. The XXXX may be label or description of flash drive, mine says PMAP.**
Some tools like Rufus only create USB live installer in one mode or the other, so how you create installer then is important as UEFI boot will only have that one option.

**But if you have UEFI Secure boot on, the BIOS/Legacy/CSM option is not available and you may even have to turn on a UEFI setting to allow USB boot as USB booting is not considered Secure. With Secure boot off, either boot should be available, but you may still need the USB boot setting with some systems.**
[I]
Secure boot[/I] is set to *[Disabled]*.

The options I get when booting from the USB drive are those you can see in the screenshot above.

I still get the the EFI warning when trying to install Ubuntu; this time the bootable USB drive was created with Rufus.

I downloaded the ISO from here: [https://ubuntu.com/download#download](https://ubuntu.com/download#download).

This is surprising to me because I have had no issues when installing Mint.

Do you reckon the only option I have now is installing everything from scratch Windows included?

---

### Post by nipplewise on 2021-11-18
> **Dennis N said:**
> sda5 which is formatted FAT32 looks like an EFI system partition - but it may not be used. Your boot options in post #6 say "Legacy Only" meaning the OS will only boot BIOS installs. So Mint must have been installed in BIOS mode, as well as your Windows install. 

**You should install Ubuntu as BIOS mode, which means you have to boot the USB installer in bios mode. In the USB boot up menu, it can have both options - select the one without mention of UEFI.**
As you can see from the screenshot above, the available options of the bootable USB drive are:
```

Ubuntu
Ubuntu (safe graphics)
OEM install (for manufacturers)
Test memory
```
This time I created the bootable drive with Rufus with the *Target system* option set to *BIOS or UEFI*, which is also the only available option.

---

### Post by nipplewise on 2021-11-18
> **MAFoElffen said:**
> Not to be the Devil's advocate... Too late for this, but I have curiosity kinds of questions...

Background... Mint is an Ubuntu derived child distro of Ubuntu. It is already based on and Ubuntu core under the hood. The big plus of Linux, is that it is customizable and pieces interchange...

**If you were tired of Cinnamon Desktop, why didn't you just install ubuntu-desktop onto your old/existing Ubuntu based installation? Was it just time to start out with a fresh/clean install?**
I see what you're saying.

But I actually don't like GNOME I prefer Cinnamon.

I've never had the chance to use Ubuntu for any meaningful amount of time and I want to see whether I can get used to GNOME and if there are drawbacks (in my personal, limited experience) to using Ubuntu over Mint.

Linux Mint is not just Ubuntu with a DE (Cinnamon in this case which I am using) on top of it.

Also yes, I either am going to install Ubuntu 21.10 or Mint 20.2 again.

---

### Post by oldfred on 2021-11-18
Those are grub menu entries.

You should have UEFI boot menu before the grub menu.
Often f12, but varies by brand, check your manual.

 Several examples:

---

### Post by nipplewise on 2021-11-18
OK, with


*Boot device List F12 Option [Enabled]*,
[I]UEFI/Legacy Boot [Legacy Only]

[/I]
After pressing F12 I get the the boot menu you can see in the attachment.

If I select *USB HDD: USB DISK 2.0* I get the same GRUB boot menu which I posted earlier.


With


*Boot device List F12 Option [Enabled]*,
[I]UEFI/Legacy Boot [UEFI Only]

[/I]
after F12 and selecting *USB HDD: USB DISK 2.0* I get a slightly different GRUB boot menu.


Both GRUB menus are those of the Ubuntu USB bootable drive.

---

### Post by oldfred on 2021-11-18
Not sure if your system, then uses UEFI setting on UEFI or Legacy to also control whether booting installer flash drive.
Most systems have those separate & then user may boot installer in one mode, but have system booting in other mode and then have issues.

What brand/model system?

---

### Post by tea for one on 2021-11-18
> **nipplewise said:**
> 
Both GRUB menus are those of the Ubuntu USB bootable drive.

Strictly speaking, those images are not both Ubuntu Grub menus

IMG_20211118_202806511.jpg = Ubuntu Grub menu before a live session or installation
IMG_20211118_201636981.jpg = Boot Menu from your PC (i.e.not Grub)

The Ubuntu Grub Menu will appear after the selection of booting a USB device containing a Ubuntu ISO

---

### Post by nipplewise on 2021-11-18
> **tea for one said:**
> Strictly speaking, those images are not both Ubuntu Grub menus

IMG_20211118_202806511.jpg = Ubuntu Grub menu before a live session or installation
IMG_20211118_201636981.jpg = Boot Menu from your PC (i.e.not Grub)

The Ubuntu Grub Menu will appear after the selection of booting a USB device containing a Ubuntu ISO
I apologize for the misunderstanding I meant to refer to the previous two mentions of GRUB boot in the same post not to the attachments.

---

### Post by nipplewise on 2021-11-18
> **oldfred said:**
> Not sure if your system, then uses UEFI setting on UEFI or Legacy to also control whether booting installer flash drive.
Most systems have those separate & then user may boot installer in one mode, but have system booting in other mode and then have issues.

What brand/model system?

*UEFI/Legacy Boot [Legacy Only]*,
*USB UEFI BIOS Support [Disabled]* won't allow me to boot at all using the bootable Ubuntu USB drive.

*UEFI/Legacy Boot [Legacy Only]*,
*USB UEFI BIOS Support [Enabled]* do.

I am using a ThinkPad T440P.

I also found this on Stack Exchange: [https://askubuntu.com/questions/1308759/20-10-unable-to-setup-either-efi-or-legacy-boot](https://askubuntu.com/questions/1308759/20-10-unable-to-setup-either-efi-or-legacy-boot).

Could it be that I am having difficulty here because of a bug in the Ubuntu 21.10 installer?

**Edit**: I also want to point out that

*UEFI/Legacy Boot [Legacy Only]*,
*USB UEFI BIOS Support [Disabled]*

followed by F12 in order to select *USB HDD: USB DISK 2.0* doesn't work either.

I just tested this with the Rufus created USB bootable drive.

---

### Post by oldfred on 2021-11-18
With Rufus you make either a UEFI/gpt or a BIOS/(CSM/MBR) only bootable flash drive.
If then you do not select the same boot mode in UEFI boot menu (before you would have gotten grub) then it will not boot at all.

UEFI selection screen:
[https://askubuntu.com/questions/1278772/unable-to-access-ubuntu-from-uefi](https://askubuntu.com/questions/1278772/unable-to-access-ubuntu-from-uefi)
Says this is UEFI or BIOS, may depend on version of Rufus:
[https://rufus.ie/en/](https://rufus.ie/en/)
This shows BIOS or CSM only, CSM is BIOS boot on UEFI system.
[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#3-usb-selection](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#3-usb-selection)

CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

---

### Post by MAFoElffen on 2021-11-18
Back to adding something from the outside, without trying to muddy this up... 

I personally have a Lenovo ThinkPad T520. Very similar, but older. Also, mine is dual boot, with Win10 and 20.04 LTS. 6TB internal storage, between 2 x 2TB SSD drives and a 2TB MSATA drive... 

I'm also a Techie. Certified Lenovo, Dell and HP Service Tech... But I am modest. More years of experience... that is embarrassing.

I don't understand... why on this hardware, that you would install as Legacy only. There's actually a BIOS option there to boot as either. What is the reasoning?

I have machines here installed as dual boot in both Legacy and UEFI. But most my machines, I setup my root drives to exist and both Legacy and UEFI boot... So that If I have a machine go down, that if can go to anything, hardware wise. The thing is UEFI had no been around over 9 years now. Yiur hardware supports it.

Please help me understand the reasoning.

Like oldfred said, if you are using Rufus, you can format and set MBR... which will boot Legacy or UEFI. If you set Rufus to  GPT, then if will only boot as UEFI. But... It also depends what you have 'your' BIOS boot mode set at. It will not boot Legacy, if it is set at UEFI only. My own BIOS on the Laptop I am posting from, that T520 only has two modes. UEFI only, or UEFI/Legacy mixed. Either way, mine can boot UEFI from either of those two modes.

---

### Post by nipplewise on 2021-11-19
> **oldfred said:**
> With Rufus you make either a UEFI/gpt or a BIOS/(CSM/MBR) only bootable flash drive.
If then you do not select the same boot mode in UEFI boot menu (before you would have gotten grub) then it will not boot at all.

UEFI selection screen:
[https://askubuntu.com/questions/1278772/unable-to-access-ubuntu-from-uefi](https://askubuntu.com/questions/1278772/unable-to-access-ubuntu-from-uefi)
Says this is UEFI or BIOS, may depend on version of Rufus:
[https://rufus.ie/en/](https://rufus.ie/en/)
This shows BIOS or CSM only, CSM is BIOS boot on UEFI system.
[https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#3-usb-selection](https://ubuntu.com/tutorials/create-a-usb-stick-on-windows#3-usb-selection)

CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

*Secure boot* is already set to *[Disabled]*.

I indeed created the bootable USB drive using the options

*Partition Scheme: MBR*,
[I]Target system: BIOS or UEFI
[/I]
on Rufus.

The other option being *GPT* which targets* UEFI (non CSM)*.

At this point I give up because I don't want to reinstall also Windows.

---

### Post by nipplewise on 2021-11-19
> **MAFoElffen said:**
> Back to adding something from the outside, without trying to muddy this up... 

I personally have a Lenovo ThinkPad T520. Very similar, but older. Also, mine is dual boot, with Win10 and 20.04 LTS. 6TB internal storage, between 2 x 2TB SSD drives and a 2TB MSATA drive... 

I'm also a Techie. Certified Lenovo, Dell and HP Service Tech... But I am modest. More years of experience... that is embarrassing.

**I don't understand... why on this hardware, that you would install as Legacy only.** There's actually a BIOS option there to boot as either. What is the reasoning?

I have machines here installed as dual boot in both Legacy and UEFI. But most my machines, I setup my root drives to exist and both Legacy and UEFI boot... So that If I have a machine go down, that if can go to anything, hardware wise. The thing is UEFI had no been around over 9 years now. Yiur hardware supports it.

Please help me understand the reasoning.
I don't want to.

The option

*UEFI/Legacy Boot [Legacy Only]*

was already set in the BIOS, maybe by the previous owner.

What I did was first installing Windows and then Linux Mint.

Now that I am trying to install Ubuntu on top of Mint while also maintaining the Windows partition, I can't seem to be able to do so (without also having to reinstall Windows apparently).
> **MAFoElffen said:**
> 
Like oldfred said, if you are using Rufus, you can format and set MBR... which will boot Legacy or UEFI. If you set Rufus to  GPT, then if will only boot as UEFI. But... It also depends what you have 'your' BIOS boot mode set at. **It will not boot Legacy, if it is set at UEFI only.** My own BIOS on the Laptop I am posting from, that T520 only has two modes. UEFI only, or UEFI/Legacy mixed. Either way, mine can boot UEFI from either of those two modes.
It makes sense.

I was documenting the fact that I had tried various combinations.

---

### Post by MAFoElffen on 2021-11-19
"That" (now) makes perfect sense.

The confusion people (me included) comes from from the second photo attachment in your first post... It has on /dev/sda, partitions sd[1-6]. That would mean that it had a GPT partition table. And the layout of the other partitions are Windows, in the MS Win installer-planned layout, as if it was originally installed as a Windows UEFI boot installation. The original Lenovo branded Windows OEM installation media for your Laptop was UEFI boot.

Does it boot Windows on your machine it you change the boot mode to UEFI? The reason I ask is that, you are reinstalling your Linux instance anyways... Just figuring out all the options you have open to you...

---

### Post by nipplewise on 2021-11-19
I'm glad this is more clear now.

I'll have to add a bit more context in regards to the Windows installation.

It is clear at this point that the original BIOS settings (in the sense that I did not tinker with these after purchasing the laptop from a first owner) were:

*Secure Boot [Disabled]*,
*UEFI/Legacy Boot [Legacy Only]*,
* - CSM Support [Yes]*.

I removed the old SSD and then installed Windows 10 on a brand new SSD.

The Windows ISO was downloaded from the Microsoft website (Windows is licensed with the same license of the Windows installation on the old SSD), but I don't remember whether at the time I used Mint's USB Image Writer or Rufus to create a Windows installer.

Note that from where I live I cannot download from the Microsoft website the tool for creating an installation media for Windows; instead I am redirected to the ISO download. **Edit**: This is actually not the case, it's because I was trying to download such tool from Linux and an online friend living elsewhere was able to download it without issues so I thought it was about restrictions based on countries. I just tried and I can successfully download it from Windows.

I then installed Linux Mint.

I don't remember setting the partitions manually when I did so; I think I only had to choose how much space to allocate for Linux.

Everything was done with the BIOS settings above.

With the same BIOS settings I can boot from the bootable Ubuntu USB drive but I have the problem shown in the attachment of [https://ubuntuforums.org/showthread.php?t=2469025&p=14067440#post14067440](https://ubuntuforums.org/showthread.php?t=2469025&p=14067440#post14067440).

That attachment is from the attempt I made while using Mint's *USB Image Writer* to create the bootable USB drive but I don't think USB Image Writer it to blame.

1. With the options

*Secure Boot [Enabled]*,
*UEFI/Legacy Boot [UEFI Only]*,
* - CSM Support [No]*

I can't boot at all, the GRUB menu for choosing between Windows 10 and Linux Mint does not appear and instead I am redirected to the the boot menu which usually appears after pressing F12 (selecting *ATA HDD0: Samsung SSD 870 QV0 1TB* won't work).

*UEFI/Legacy Boot [UEFI Only]*,
* - CSM Support [No]*

are required after having set

*Secure Boot [Enabled]*

2. I get the same result with:

*Secure Boot [Disabled]*,
*UEFI/Legacy Boot [UEFI Only]*,
* - CSM Support [No]*.

3. The settings

*Secure Boot [Disabled]*,
*UEFI/Legacy Boot [Legacy Only]*,
* - CSM Support [Yes]*

are the only ones which allow me to boot Windows 10 or Linux Mint.

* - CSM Support [Yes]* in this case is required after having set

*UEFI/Legacy Boot [Legacy Only]*.

---

