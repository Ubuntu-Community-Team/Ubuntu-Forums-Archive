---
title: "Ubuntu 16.04 Installation, Disk not recognzied"
date: 2017-09-29
forum: Installation &amp; Upgrades
---

### Post by sparkflame27 on 2017-09-29
I am trying to install Ubuntu 16.04 on an old desktop donated to me. 

I tried the Ubuntu 16.04 live versionlive version, and used gparted to format and read the 1Tb hard drive I installed, and it seems is read just fine. after formatting I went to the install, and for some reason my disk is not being seen by Ubuntu 16.04. It is recognized in GParted but not under the Installation type tab in the install software. The current hard drive setting is on AHCI in the bios. 

I have tried a few different file types to make sure it isn't that (which it shouldn't have been anyways). 

Here are computer specs if they matter
Intel core 2 quad 6600
8Gb DDR2 800Mhz
Nvidia 7900Gs
Asus Workstation MOBO
1Tb Seagate Barracuda

---

### Post by Autodave on 2017-09-29
Is this a blank HD: no other operating system on it? Is the HD installed inside the machine or is it external? What messages, if any, are you seeing?

---

### Post by efflandt on 2017-09-29
What type of partition table did you use? If the did not have any partitions on it, with gparted you should have first created an msdos partition table on it and then add whatever partition(s) you want (up to 4 primary or extended partitions, but an extended partition can contain any number of logical partitions. You should also be able to do that while installing Ubuntu, by going to "Other" when it comes to the partitioning part, which should also be able to select which drive mbr to install grub to if you have more than one drive. Otherwise if you only have 1 drive, there should be a selection to "Use entire disk" instead of "Other".

But different people have different definitions of "old". This explanation is if the computer originally came with Win7, Vista, WinXP or older. If it originally came with Win8 or newer the procedure may be different if it uses UEFI instead of legacy BIOS. Although, at work I had a Lenovo Win8.1 all-in-one PC that still used msdos partitions and legacy BIOS instead of UEFI.

---

### Post by oldfred on 2017-09-29
Is it not booting after install?
You have an older nVidia card and may need nomodeset.
You have to hold shift key until grub menu appears then replace quiet splash with nomodeset.
Then once booting in low quality video, you should be able to add the correct nVidia driver. You will need one of the older legacy drivers. Only install from Ubuntu repository.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

If using Something Else and drive not seen, you may still need nomodeset with BIOS on installer you add nomodeset with anykey while tiny accessibility (keyboard/person) icons at bottom of screen, then f6.
 
These are all reported issues with older BIOS systems.

 **Common BIOS  grub install issues:**
BIOS settings to disable "Boot Sector Virus Protection" or called Security or locked down Boot sector, Bitlocker
Though my drive was appearing in the bios and working for install it was actually "disabled"! 
 bios had a setting for "Fixed disk boot sector" and it was set at "Write Protect"
NTFS partition needs chkdsk, gparted will not see drive if chkdsk flag set, flag is set on resize
Raid meta data on drive - even if one drive (Vendor happend to set it on) or Intel SRT on Ultrabook
Old gpt data on drive where Windows installed in BIOS/MBR mode
**Other issues users have reported:**
BIOS in not updated to latest revision
BIOS shows floppy or firewire and you do not have those
BIOS - enable the IMMOU so USB2 ports work - Many Gigabyte boards, others ?
BIOS settings need USB mouse & keyboard, USB detection turned to "UEFI Only"
BIOS setting, Keyboard response in grub really slow
BIOS not loading no key works - disconnected power for about 10-15 minutes and the bios reset itself.
BIOS not set to boot CD or USB first
BIOS has hard drive turned off - Operating system not found error Also unplugged, bad connections etc
Disable Quickboot in BIOS
BIOS/Windows Fast Boot setting prevents keyboard from working & other issues
 Dell security software on Windows 7 ties in with the BIOS cannot write to drive
changing newer BIOS SATA 6 Gbit/s  from 6 Gbs to a SATA II - 3Gbs 
Old BIOS, new drive 137GB max boot size or very large / partition over 100GB

---

### Post by sparkflame27 on 2017-10-02
it is a blank HD, I deleted all data on in when reformating in Gparted

---

