---
title: "Bootloader problem with Xubuntu 13.10 installation"
date: 2013-12-08
forum: Installation &amp; Upgrades
---

### Post by knight91 on 2013-12-08
I am currently trying to install Xubuntu 13.10 on a Lenovo Thinkpad x121e. I use a DVD in an external drive to install from and also used WLAN during the installation. Problem:    Starting up after a successful installation, no operating system is found, manually choosing the appropriate drive (the only drive; a 128GB SSD) to boot from, does not help either.  In the installation, I chose to use the complete hard disk and use an encrypted LVM. The installation runs through without any error. Boot-repair now states that the boot sector has been repaired successfully, yet I am informed that there is no boot loader installed.      The report can be found here: [http://paste.ubuntu.com/6542309](http://paste.ubuntu.com/6542309)    I have already tried to delete current partitions, install grub manually in some way, but after doing so and running the complete installation with "use complete hard disk" & disk encryption, the situation does not change at all. I have tried this now many times and also switched to installing Ubuntu Gnome 13.10, which gives me the exact same problem. I checked the install DVDs for errors.    Before trying to install Xubuntu today, I already had Debian installed (with disk encryption)  with a working grub boot loader, after installing Xubuntu (again, each time I chose to use the whole disk) I have no operating system and no boot loader. Why is there no boot loader installed automatically when choosing to erase the whole drive before installing?  As you can see, I do not care for preserving any data, any preferences, anything at all – I would just like to get a working operating system that is even recognized on startup.    I am happy for any advice.

---

### Post by oldfred on 2013-12-08
Welcome to the forums.
You have grub installed what looks correctly into the efi partition. It will not be installed to MBR.
Are you tryng to boot in secure boot mode or CSM/BIOS boot modes?
You need to have CSM off.
It does look like you have installed the signed versions of grub  & kernel, so it should boot with secure boot on. But a few UEFI have been modified by vendor to only boot Windows.

Have you checked that you BIOS is the most current version from the vendor. They also are making many fixes for UEFI booting.

There are work arounds for UEFI that only boot Windows, but check your settings in UEFI first.

---

### Post by knight91 on 2013-12-08
First of all, thanks for your response.  I checked any option in my BIOS menu, the only thing that looked slightly like anything you said was the choice UEFI/legacy boot: Default value is "both", changing to "UEFI only" or "Legacy only" does not have any effect.  Note that I already had grub as boot loader for Debian running with the existing BIOS, so in my insignificant opinion, it should not be the problem of a BIOS only booting Windows. Moreover, I bought the Thinkpad without OS, so there never was Windows installed on it.  Regarding "secure mode" or "CSM mode" – I hope you do not overestimate my knowledge and skills, I do not know how to willfully boot in either of those modes, nor did I find anything resembling those expressions in the BIOS menu.  I tried to update my BIOS using an image provided by Lenovo. The update notes did not state anything that seemed to be related to my problem. I could not perform the update yet, because it won't run unless my battery is fully charged, which might take a while.  So, if the BIOS update does not solve the problem, what would you suggest me to do?

---

### Post by knight91 on 2013-12-08
Update: I have now updated BIOS, with no effect on finding an operating system and no effect on the available options. Sorry for that. Moreover, I am sorry to see that my posts are published without a single break, I do not know why that is, either. I am even glader that there are people reading the blocks and trying to help nonetheless.

---

### Post by oldfred on 2013-12-08
Correct mode is UEFI or UEFI with secure boot enabled since you have signed kernels.

But I do not know if there are some issues with UEFI and full disk encryption with LVM. I do not know much about either.

It looks like when you ran Boot-Repair it was from a BIOS boot mode?
I might try again with UEFI boot. Does it ask for passphase to mount encrypted lvm?

This shows both so you know which you are booting with.
       Shows install with screen shots for both BIOS & UEFI, so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

I know some want the full disk encryption, but LVM adds a level of complication to an install. I do not think it is for beginners. And then encryption adds more difficulty. Be sure to have good back ups as any failure that may prevent correct mounting and asking for your passkey will prevent even you from accessing data. Standard recovery & partition tools do not work with LVM and encryption.

This user in post #9 likes LVM

 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

