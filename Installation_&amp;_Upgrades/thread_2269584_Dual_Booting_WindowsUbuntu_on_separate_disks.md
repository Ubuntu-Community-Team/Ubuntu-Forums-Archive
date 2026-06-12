---
title: "Dual Booting Windows/Ubuntu on separate disks"
date: 2015-03-16
forum: Installation &amp; Upgrades
---

### Post by shooter_of_arrows on 2015-03-16
Hello there,

I'm still *fairly* new to Ubuntu/Linux, but have quite a bit of experience in it. However, I in an interesting situation. I want to install Ubuntu onto a separate hard drive from my Windows install. I seem to have done that kind of, but strange things are happening.

_Backstory/steps I took:_
I'll start off with some back-story, which does relate to this situation (but is possibly a bit long-winded). 

I've had a hard drive that I used for my system drive for a long time now (6 years). Recently, I got an SSD and installed windows onto it instead. Because my install of Windows at the time was becoming to get slow, I decided to do a fresh install on the SSD. I didn't unplug the old hard drive when I did this, and it looks like the boot manager on the old hard drive was just updated to point to the SSD. My evidence is that when I loaded up the Ubuntu disk, the SSD partition didn't have a "Boot Loader" or w/e it's actually called (far right column of the screen). 

I didn't pay too much attention to it because I was going to use Grub to point to the other disk anyways. This disk still had my old install of Windows on it, so I chose to erase Windows and install Ubuntu over the top of it. The process to install Ubuntu was the most painful install of Ubuntu I've done so far (had to turn on IOMMU in UEFI/BIOS to get my mouse/keyboard to work, was still having "IO_PAGE_FAULT"s with something before even getting to the installer, etc, etc), but I got it to install.

When I discovered that Grub wasn't seeing my Windows install, I decided try to boot back into windows. This is where I discovered the problem that it won't boot. After monkeying around trying different things in the Windows Repair Disk utilities, I found out that if I have the Ubuntu drive physically plugged into my mobo, the Recovery Tools didn't even see the Windows install on the disk. However, unplugging the Ubuntu drive Recovery Tools was able to see the Windows partition, and after more monkeying around with it, I got it to boot into Windows again.

[U]Problem I'm having:
[/U]I'm able to boot into Windows now, and am currently typing to you on the computer in question. However, if I plug the Ubuntu drive back into my mobo, Windows doesn't boot correctly. It tries to load, but eventually ends up with "Operating System not found" or something along those lines. When I unplug the Ubuntu drive Windows is still in a broken state, but it's able to restores back to a restore point and boot correctly again.

I haven't tried to boot back into Ubuntu and see if Grub will see Windows now, and that may be the next step, but I don't want to run the risk of breaking it further after fixing it from near-brick state without some feedback/what to look for.

I'm still intent on getting Ubuntu working on my computer, but don't want to break Windows in the process.

---

### Post by oldfred on 2015-03-16
Best to see details: Post link to summary report. 
With multiple drives do not run auto-fix only advanced mode. Auto fix installs grub to every MBR.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Windows has to have its drive as default in BIOS if a BIOS/MBR system to see the correct NTFS partition with the boot flag to make repairs. After fixes or an install then you can change BIOS to boot any drive. Windows always installs its boot loader partition into drive set as boot in BIOS.
Grub always defaults to install its boot loader to sda. You have to use Something Else and even there change the default entry in the combo box to the same drive you are installing Ubuntu.

Even then with UEFI grub seems to always install its boot files into the efi partition on sda.

---

### Post by shooter_of_arrows on 2015-03-16
I don't want to sound rude or anything (which totally means I'm going to sound rude...but w/e, just know I don't mean to), but I want to make sure I have this all correct. I had a little trouble understanding your grammar (see, there's the rude part...).

You are saying to:
1. Make sure Windows stays as the default drive in BIOS
2. Load up Ubuntu either from the drive or live CD (or create a Boot-Repair live USB)
 - Install Boot-Repair on either and let it run (unless live USB method)
3. Add Windows to grub (unless Boot-Repair already did that)
4. Set Ubuntu as default drive in BIOS?

Again, I just want to make sure I get this all right before I mess up my computer further.

---

### Post by grahammechanical on 2015-03-16
First run Boot Repair. You will get a URL to a pastebin site. Post the URL here then we can click on it and see the boot repair report.

When repairing Windows the Windows drive needs to be the default drive that is loading. Boot Repair will re-install Grub into every drive unless we use the Advanced options to give a specific instruction on where to install Grub. Preferably on the Ubuntu Drive.

Grub may no longer be aware of the location of the Windows boot files and that is why you are getting the "operating system not found" message when the Ubuntu drive is attached. Or it could be that it is the Ubuntu drive that the BIOS is looking to when it tries to load Windows and of course it does not find it on the Ubuntu drive.

That Boot Repair report will give a clearer picture. I guess the aim is to have the Windows boot manager on the Windows drive and the Ubuntu boot manager (Grub) on the Ubuntu drive. Then you can use the BIOS/UEFI to change which drive to load an OS from. With the benefit that the Ubuntu boot loader will detect the Windows OS whereas the Windows boot loader will not detect a Linux OS.

The Ubuntu installation process will by default install Grub into the first hard drive (sda) which maybe the Windows drive. To prevent that happening have to install using the Something Else option as that gives the option of have Grub installed into the second drive (sdb) or the third drive (sdc) and so on.

Regards.

---

