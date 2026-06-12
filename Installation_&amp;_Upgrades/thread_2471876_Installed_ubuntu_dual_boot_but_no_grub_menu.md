---
title: "Installed ubuntu dual boot but no grub menu"
date: 2022-02-11
forum: Installation &amp; Upgrades
---

### Post by old.dog on 2022-02-11
I installed ubuntu mate 20.04 on my HP laptop model 15-db0085cl in a dual boot configuration with Windows 10.  After installation and before rebooting I verified that ubuntu was working.  However, after reboot it goes directly into windows.

In bios, under Boot Device Options, I see that there are two boot loaders. I selected the ubuntu loader and it loaded through the initial startup screen and then hangs.  Ubuntu does not appear in the boot order menu so I am unable to change it.  

Any help will be appreciated.

Dan

---

### Post by ajgreeny on 2022-02-11
See **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 

**Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system. 

This may show that you installed Ubuntu-Mate using legacy BIOS/MBR which means a dual boot will be almost impossible; ***both OSs must be installed using the same mode***, both UEFI or both BIOS/MBR, not one of each.

---

### Post by old.dog on 2022-02-11
Sorry for the delay but I have pasted the results at [https://paste.ubuntu.com/p/2Sv2VMWSy4/](https://paste.ubuntu.com/p/2Sv2VMWSy4/)

---

### Post by oldfred on 2022-02-11
With UEFI Secure  Boot on, you can only dual boot from UEFI boot menu, not from grub.
Something about grub and Windows cannot transfer Security to another boot loader.
you should be able to always boot from UEFI boot menu.

Those with HP, often have to update UEFI.
And HP users seem to have to change boot order in UEFI settings, not UEFI menu.
Every other system works with efibootmgr and setting boot order. Grub uses efibootmgr to set boot order. Not sure what HP does, or if syncing BCD and then the Windows is always first.
see
man efibootmgr

UEFI update helped:
[https://ubuntuforums.org/showthread.php?t=2448563](https://ubuntuforums.org/showthread.php?t=2448563)
HP Envy - use UEFI to change boot order
[https://askubuntu.com/questions/1332255/dual-boot-only-booting-into-windows-no-option-to-choose-between-windows-or-ubun](https://askubuntu.com/questions/1332255/dual-boot-only-booting-into-windows-no-option-to-choose-between-windows-or-ubun)

---

### Post by old.dog on 2022-02-12
I updated the BIOS to the latest version.  However, when enter BIOS setup (F10), and look at the boot order, ubuntu is not listed so can not change boot order. 
I also tried "Boot Device Options" (F9) again.  If I select "OS boot manager (UEFI) - ubuntu (ST2000LM007-1R8174)"  I get a grub menu that has ubuntu but not Windows.  Selecting ubuntu hangs with a black screen with random flashes.
Is it time to run boot-repair?  If so,  should I run "Recommended repair" or some other options?
Thanks again,
Dan

---

### Post by oldfred on 2022-02-12
If you are getting grub menu, you are booting thru what Boot-Repair primarily fixes.
It typically updates grub menu or optionally can totally reinstall grub.

Can from grub menu, you choose the second boot option, recovery mode. May be in sub-menu?

What video card/chip do you have? 
If nVidia you need nVidia driver which should have been installed if you chose to install restricted options when you installed. You may be able to boot with nomodeset in a low quality graphics or from recovery mode install restricted drivers, if needed.

Grub not does not show Windows by default. They have updated grub settings to turn os-prober off by default. There is some security issue. But you have secure boot on, so grub would not boot Windows anyway.

---

### Post by old.dog on 2022-02-12
Yes, I can get to the grub menu but only by way of  the BIOS "boot device options" (F9).  When I booted in recovery mode, a message popped up with  something about UEFI stub but went away quickly.  It then booted into ubuntu and worked OK.  

Graphics is listed as "llvmpipe (LLVM 12.0.0, 256 bits)

---

### Post by oldfred on 2022-02-12
I thought llvmpipe was a default when the correct driver is not installed?
Do you have nVidia?

---

### Post by grahammechanical on 2022-02-12
Recovery mode > Resume loads to a desktop using a low resolution open source video driver. Quite likely llvmpipe. Proprietary video drivers are not loaded until we reboot. This is normal behaviour for recovery mode.

Regards

---

### Post by old.dog on 2022-02-12
The video is AMD Radeon&#8482; R5 Graphics.  If I had been smarter I would have gone directly to the HP website and checked the specs.  :-(

---

### Post by oldfred on 2022-02-12
Do not know AMD, but most things I have seen said it auto installs driver.
And some models may then support a pro driver.

But have this in notes:
Ubuntu 19.10 Doesn't Ship With AMD Navi / Radeon RX 5700 Support Working, But Easy To Enable
[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-19.10-Radeon-RX-5700](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-19.10-Radeon-RX-5700)
AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
AMD Releases BIOS Fix To Motherboard Partners For Booting Newer Linux Distributions July 2019
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Releases-Linux-Zen2-Fix)
[https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2](https://www.phoronix.com/scan.php?page=article&item=ryzen-3700x-3900x-linux&num=2)
400 series chipsets need BIOS/UEFI update for Ryzen 3000, 500 seires standard with 3000
[https://ubuntuforums.org/showthread.php?t=2430149&p=13904266#post13904266](https://ubuntuforums.org/showthread.php?t=2430149&p=13904266#post13904266)
RADEON &#8212; August 2019
In addition to AMD releasing the Radeon Pro Software for Enterprise 19.Q3 Linux driver, they also quietly released a new Radeon Software Linux driver release for consumer GPUs.

[https://ubuntuforums.org/showthread.php?t=2443998](https://ubuntuforums.org/showthread.php?t=2443998)
[https://amdgpu-install.readthedocs.io/en/latest/](https://amdgpu-install.readthedocs.io/en/latest/)
 latest PRO driver for Ubuntu 20.04. as of May 2020, check that your card is supported
[https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-10](https://www.amd.com/en/support/kb/release-notes/rn-amdgpu-unified-linux-20-10)

---

### Post by old.dog on 2022-02-12
Hi oldfred,

I will peruse the links you provided and report back if I learn anything worthwhile.  Right now I feel like I need a break from computer stuff so I can do something I am better at.

Thanks again

---

