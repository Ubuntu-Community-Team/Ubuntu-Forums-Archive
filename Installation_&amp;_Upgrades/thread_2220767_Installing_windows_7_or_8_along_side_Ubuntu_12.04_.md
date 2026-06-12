---
title: "Installing windows 7 or 8 along side Ubuntu 12.04 installation"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by nandan on 2014-04-29
Hello,
I have a slightly unique problem, in the sense I did not come across any thread answering this.

I have Ubuntu 12.04 and WinXp on dual boot. Win XP is not working well and does not even start anymore.

I want to upgrade to Win 7 or 8 (legally!) and keep a dual boot system with Ubuntu 12.04 intact. 

Is there any step by step procedure for this? I want to be fairly sure that it is possible before I put my money in Windows. 

Help is appreciated.

(Hardware is 32 bit.)


Regards,

Nandan

---

### Post by sudodus on 2014-04-29
Installation of an operating system is risky, so please backup your computer before starting.

Remember to get a 32 bit system.

But before buying a new license, please specify your computer. I makes it easier to give relevant advice.

Brand name and model
CPU
RAM (size)
graphics chip/card
wifi chip/card

---

### Post by Mark Phelps on 2014-04-29
First of all, there is no straightforward way to "upgrade" to Win7 or Win8 from XP, MS does not support this.  So basically, you will have to reinstall all your apps.

Second, you will need to preallocate some disk space before installing as Windows does not understand Linux filesystems.  To do that, boot from Ubuntu install media, select Gparted, and shrink your Linux filesystem by 40GB.  When  that's done, create an NTFS partition in the new space.

Third, when you install Windows, use the option to reformat the NTFS partition -- this is important.

Fourth, when done, Windows will have overwritten your MBR so you will have to reinstall GRUB: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by pfeiffep on 2014-04-29
> **nandan said:**
> Hello,
I have a slightly unique problem, in the sense I did not come across any thread answering this.

I have Ubuntu 12.04 and WinXp on dual boot. Win XP is not working well and does not even start anymore.

I want to upgrade to Win 7 or 8 (legally!) and keep a dual boot system with Ubuntu 12.04 intact. 

Is there any step by step procedure for this? I want to be fairly sure that it is possible before I put my money in Windows. 

Help is appreciated.

(Hardware is 32 bit.)


Regards,

Nandan

[from Microsoft's site]("http://windows.microsoft.com/en-us/windows7/products/system-requirements")
[COLOR=#454545][FONT=WOL_Reg][FONT=WOL_Bold]**If you want to run Windows 7 on your PC, here's what it takes:**[/FONT][/FONT][/COLOR]

[LIST]
[*]1 gigahertz (GHz) or faster 32-bit (x86) or [64-bit (x64)]("http://windows.microsoft.com/en-us/windows7/products/features/64-bit-support") processor
[*]1 gigabyte (GB) RAM (32-bit) or 2 GB RAM (64-bit)
[*]16 GB available hard disk space (32-bit) or 20 GB (64-bit)
[*]DirectX 9 graphics device with WDDM 1.0 or higher driver
[/LIST]
_Remember these are minimums_


If you can manage to start Win XP try  [Microsoft Advisor]("http://www.microsoft.com/en-us/download/details.aspx?id=20")

---

### Post by nandan on 2014-04-29
Hello and thanks for the interest shown!

I am using an 'assembled' desktop.

The specs are as follows:

Processor: Intel Core 2 Duo CPU E7500@ 2.93 Ghz * 2

Graphics: Intel G41 x86/MMX/SSE2

RAM: 1.9 GB

Wi-fi is an external router provided by the Internet Service Provider. This is a desktop computer.

I have a 1TB hard disk, which has been partitioned and Win Xp has around 78 GB, Ubuntu 12.04 has around 450 GB. Around 390 GB is unallocated on the Windows side (NTFS).

My guess is the specs should be OK for win 7 or 8 installation.  And I guess I will have to "overwrite" the installed XP, not for space considerations, but it is just not working.

---

### Post by sudodus on 2014-04-30
Yes your computer has enough horsepower and memory :-)

The processor can run 32-bit and 64-bit systems. I don't know if some other hardware (for example the motherboard) would limit you to 32-bits. You can try that with downloading a [free] 64-bit Ubuntu and try it live (booted from DVD or USB). But a 32-bit Windows system should be OK.

Check that you get a licence that is valid for your computer! Some cheap licences are only valid when sold with a computer, other licences are valid on any single computer.

-o-

There should be enough space if you overwrite Windows XP. I have too little knowledge of installing Windows into computers, where there is already Ubuntu, so I can't tell if it will be happy with only one partition, or if it wants more than one partition. This may be different between Window 7 and Windows 8. I think the other guys who have replied in this thread will add information about partitioning.

And after the installation, you have to reinstall the grub bootloader in order to get back dual booting.

---

### Post by nandan on 2014-04-30
Hi,
Thanks again!

I am looking for step-by-step instructions to install win 7 or 8. My concern is that Windows setup may walk roughshod over my UBuntu installation and delete it. Is there any guide or post around which shows this? Any precautions (apart from data back up) that I need to take to ensure that I am not left with one OS or worse, two non-functioning OSes?

---

### Post by oldfred on 2014-05-01
Several that install Windows have lost Linux partition in an extended partition. Usually able to get it back with testdisk, but it just is Windows rewriting partition table and not 'seeing' the Linux partition.

Does not hurt to back up partition table itself. Do this after any changes but before installing Windows. If you change partitions after backup then you cannot restore from the backup.
This is for MBR only.
 Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

Windows will overwrite grub boot loader in MBR, so have Ubuntu live installer, Boot-Repair, Supergrub or some way to reinstall grub.

      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by nandan on 2014-05-02
Thanks again, but is there any documented experience and a list of do's and dont's in this? I was able to guess the overwrite issue, but would like to know what other issues I need to be aware of. I don't know what I don't know about installing Win 7/8 on an existing installation of Ubuntu 12.04.

Would appreciate if you could point me to resources...

---

### Post by oldfred on 2014-05-02
Most install Windows first. Most of links are pretty old, some discuss Windows 7.
Issues with Windows 8 are fast boot or always on hibernation which must be off if dual booting.

You need a primary NTFS partition with the boot flag for Windows to install. It normally installs a separate 100MB boot primary partition if you install into unallocated space, but will use just one NTFS partition if created in advance.

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
       [URL="https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"]https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows

[http://lifehacker.com/5403100/dual-boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual-boot-windows-7-and-ubuntu-in-perfect-harmony)       [/URL]
 Older but discusses the issues, reinstall grub2, not other alternatives:
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)
[https://help.ubuntu.com/community/WindowsDualBoot#Installing](https://help.ubuntu.com/community/WindowsDualBoot#Installing) Windows After Ubuntu

    [URL="https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows"]
[/URL]

---

### Post by nandan on 2014-05-02
Great! Guess will read through and figure out 1. whether I should go for Win7 or 8 on my ubuntu desktop and if yes, 2. how to do so.

Closing this thread. Thanks again for your help!

---

