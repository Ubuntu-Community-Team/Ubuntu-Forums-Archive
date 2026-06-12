---
title: "[Kubuntu] 14.04 Dual Boot: Win8 Not Booting, Boot-Repair Errors"
date: 2014-04-25
forum: Installation &amp; Upgrades
---

### Post by asdinnie2 on 2014-04-25
Hi All

**After the 14.04 install: Kubuntu boots fine, Win8 will not boot (get GRUB error about missing efi file?).**

Have installed Kubuntu 14.04 onto a Dell Inspiron 7000 series laptop, with existing Win8 partition.
Win8 used for BIOS upgrades, etc, and the other stuff you can only presently do under Windows.

With the 14.04 install disabled the Intel Smart Response Technology (SRT) and FastStartup as instructed.
I could not disable QuickBoot/FastBoot as I could not find such an entry in the Dell BIOS settings (should be in Advanced, according to some other Dell systems).

Have installed 14.04 in EFI mode (according to the terminal output)

**Warning errors happened during the running of boot-repair (under Live DVD).** 
During the checking phase it told me:
- "EFI detected, please check the advanced options"
- "Disable Secure Boot in the BIOS"

I gather that disabling Secure Boot will mess up the existing Win8 install (& probably the 14.04 install in place) so not keen to do it.
I am not keen about making changes to the boot-repair defaults without expert advice ( as advised in the boot-repair instructions).

**My boot-repair summary is at [http://paste.ubuntu.com/7327052/](http://paste.ubuntu.com/7327052/)**

BTW Can I run boot-repair from within the existing 14.04 installation? The notes did not say so & its much easier to do so.

Any help would be greatly appreciated.

Cheers, thanks

Andy

---

### Post by oldfred on 2014-04-25
System should boot with secure boot on or off without issue for both Windows & Ubuntu. Many have installed Ubuntu and dual booted with secure boot off.

Did you resize Windows from inside Windows or with Ubuntu installer. Windows need chkdsk after a resize. And if fast boot or hibernation is on that also will cause issues.

Grub menu entry to chain load back to Windows efi entry looks correct.

Can you directly boot Windows from UEFI menu or one time boot key (f12 on my old system)
       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

You can run Boot-Repair from inside you Ubuntu install. 

 Only if trusty 14.04, you need a work around to install, Boot-Repair for 14.04 trusty not yet released
 ----------- WORKAROUND 0 sandyd  compiled it
 [https://launchpad.net/~sandyd/+archive/boot-repair](https://launchpad.net/~sandyd/+archive/boot-repair)
 ----------- WORKAROUND 1
+ You can download the DEBs packages here: [https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages](https://launchpad.net/~yannubuntu/+archive/boot-repair/+packages)
+ First install the 'glade2script' DEB, then 'boot-sav', then 'boot-repair'.
+ 
+ ----------- WORKAROUND 2
+ Use Boot-Repair-Disk [https://sourceforge.net/p/boot-repair-cd/home](https://sourceforge.net/p/boot-repair-cd/home)
+ ----------- WORKAROUND 3
[https://bugs.launchpad.net/boot-repair/+bug/1307218](https://bugs.launchpad.net/boot-repair/+bug/1307218)
Workaround. Change ppa from trusty to saucy.
[http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335](http://ubuntuforums.org/showthread.php?t=2216051&p=12986335#post12986335)
gksudo gedit /etc/apt/sources.list.d/yannubuntu-boot-repair-trusty.list
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/trusty/main/binary-amd64/Packages)'
'[http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/yannubuntu/boot-repair/ubuntu/dists/saucy/main/binary-amd64/Packages)'

The 14.04 version has a lot of updates to kernel, support software & video drivers so many fixes from older versions may not be required.

 Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)

---

### Post by asdinnie2 on 2014-04-25
Hi oldfred

Thanks for the quick response.

I understand that I would have to *reinstall* both Win8 & 14.04 if I turn secureboot off?  I did not get the original Dell media with this laptop so reinstalling Win8 would be difficult.

I did resize the partition under Windows, but used a package called "Mini Tool Partition Wizard" ([www.partitionwizard.com]("http://www.partitionwizard.com")).
This was because I could not get a reasonable new parition size (for Kubuntu) under the default Windows Partitioning tool. 
I did not do a chkdsk afterwards but I think the package used did the checks for me?

BTW The problem appears to be with Grub entries itself? The error message pops up when selecting the Win8 grub entry then I am returned to the Grub menu

I can run Win8 fine from under the UEFI menu.  Its only under Grub that it does not work...

Had a look at those other links you gave me but no new information apart from what I have done?

Cheers, thanks

Andy

---

### Post by asdinnie2 on 2014-04-25
Update:
I have got part of the Grub error message that comes up when loading Win8:
```
/EndEntire
file path: /ACPI(a0341d0,9)/PCI(2,1f)/Sata(0, ..... Microsoft\Boot)/File(bootmgfw.efi)/EndEntire
error: cannot load image
```

The formatting, lack of spaces between the various bits (/ACPI, /PCI, etc.) are exactly as is.  The "...." are mine as the camera missed those bits!

Hope this helps.

Cheers

---

### Post by oldfred on 2014-04-25
All grub does is call this:

       chainloader /EFI/Microsoft/Boot/bootmgfw.efi

You see all the rest of that line like you posted if this will extract the details. But some do not? It should be the same as UEFI when it loads the Microsoft entry.

sudo efibootmgr -v

 [http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

There was a bug on grub booting Windows with secure boot on, but I thought it was fixed. Does it work with secure boot off?

---

### Post by asdinnie2 on 2014-04-27
Hi oldfred

> **oldfred said:**
> 
There was a bug on grub booting Windows with secure boot on, but I thought it was fixed. Does it work with secure boot off?

Eureka...  you have found it!
I turned OFF Secure Boot and the problem appears to be fixed.  Can boot either Win8 & 14.04 now at my own will.
So there is either a bug still in Grub or a strange thing is happening on my laptop.

Much appreciate your help.  You have earned your keep here.
I have a few other post install issues to resolve here ... but will get the rest of the install/data-copy finished on the new laptop so I can actually get some work done!

Many thanks again.

Cheers.

Andy

---

### Post by oldfred on 2014-04-27
Glad you got it working. :)

If you get to some issue that you need help on post a new thread with that in the title. Then those who may know more about that type of issue may offer to help.

---

