---
title: "new Toshiba laptop, windows installer failed (windows 8)"
date: 2013-01-11
forum: Installation &amp; Upgrades
---

### Post by E411 on 2013-01-11
Hi there,

I tried to install Ubuntu through the windows installer on a brand new Toshiba laptop (C850 or so) that came (unfortunately) with Windows 8 preinstalled.

Now I get the option to boot on either Windows 8 or Ubuntu, but only Windows will load successfully.

When choosing Ubuntu, this is what I get:


> Windows Boot Manager

Windows failed to start. A recent hardware or software change might be the cause. 

(...)

File: \ubuntu\winboot\wubildr.mbr
Status: 0xc000007b
Info: The application or operating system couldn't be loaded because a required file is missing or contains errors.

Any suggestion?

---

### Post by darkod on 2013-01-11
Yeah, install proper ubuntu on its own partition, the way any OS is meant to work.

I don't think wubi works with uefi and win8.

---

### Post by E411 on 2013-01-11
Thanks darkod. I tried to install it from a USB stick but it says that USB is not a booting option (although USB is indeed included in the boot sequence). I changed the sequence and it didn't make any difference.

Why could that be?

---

### Post by oldfred on 2013-01-11
If Windows 8 is pre-installed you have secure boot. You have to turn that off to install anything else.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

Then you will need Boot-Repair to fix the grub bug on not creating a correct chain load entry to Windows efi file.
       
 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by darkod on 2013-01-11
Win8 comes with Secure Boot I believe. One way to stop you to dual boot. And it usually comes with UEFI.

I don't use neither since I always make my own machines and select my hardware. But you can google for win8 ubuntu dual boots with secure boot and uefi, it will give lots of hits, many issues. Not sure if there are solutions yet.

PS. oldfred beat me to it. He has many links bookmarked for these cases.

---

### Post by E411 on 2013-01-18
- downloaded the 64 bit version and could indeed boot through the usb stick
- installed and ran Boot-repair, after that nothing was working anymore, the computer was booting none of the two systems (Win8 and Ubuntu)
- was fed up, decided to delete the disk and install Ubuntu alone

So as darkod said, I now have a "proper ubuntu on its own partition, the way any OS is meant to work" ;)

Thank you for helping me guys.

---

### Post by Jolt360 on 2013-05-22
I'm having a HUGE issue installing Ubuntu on my Toshiba satellite C850, I too have erased windows 8 and attempted to install Ubuntu 12.10 but about half way through the install I get an input/output error. Any chance you can share your secrets if you've gotten it to work?!?! 

Thanks!!!

---

### Post by Jolt360 on 2013-05-22
> **E411 said:**
> - downloaded the 64 bit version and could indeed boot through the usb stick
- installed and ran Boot-repair, after that nothing was working anymore, the computer was booting none of the two systems (Win8 and Ubuntu)
- was fed up, decided to delete the disk and install Ubuntu alone

So as darkod said, I now have a "proper ubuntu on its own partition, the way any OS is meant to work" ;)

Thank you for helping me guys.

I would promise to pay it forward ;)

---

### Post by ubfan1 on 2013-05-22
Assuming you checked the downloaded iso with md5sum, and ran the media check OK, I have seen an I/O error caused by a corrupted /EFI/ubuntu directory.  If you mount your EFI partition from the live media, can you successfully take a directory of the ubuntu directory?  If you get an I/O error with the directory, repeated runs (like up to 4) of:   sudo dosfsck -r /dev/sda2   (or whatever your EFI partition is if not sda2) will eventually clean it out, and a fresh install may then work. boot-repair will still be needed most likely.  Other Toshiba specific issues will be:  1) You will need the latest firmware update 6.60 (release in Jan 2013)  2)Even corrected Windows grub menu items will not boot (bug 1091464)  3)Your corrupted directory may result in grub-install entering a wrong entry (for dual secure boot) in the uefi boot menu (but if you have turned off secure boot, the grubx64 entry (instead of shim) may work just fine).  Backup the EFI files before any install, they possibly can be clobbered.

---

