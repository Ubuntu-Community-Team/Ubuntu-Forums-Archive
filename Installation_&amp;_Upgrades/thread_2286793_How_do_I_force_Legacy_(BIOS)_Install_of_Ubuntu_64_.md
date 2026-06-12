---
title: "How do I force Legacy (BIOS) Install of Ubuntu 64 bit?"
date: 2015-07-14
forum: Installation &amp; Upgrades
---

### Post by markz2 on 2015-07-14
Hey guys, long time lurker, first time poster. Got an interesting problem.

I have an Acer Aspire V5-471 laptop. It has a UEFI, but supports legacy booting. However, forcing legacy BIOS mode is not an option in the BIOS settings (manufacturer lockout).

I installed Windows 7 64 bit in legacy mode, and now want to install Ubuntu 64 bit in legacy mode. However, the Ubuntu 64-bit CD will only boot in UEFI mode - 32-bit CD boots in legacy mode, but then I can't use the 8 GB of RAM. If I continue with the installer in either 32- or 64-bit, neither sees the Windows 7 installation. Yesterday, when I had 32-bit Windows installed for a bit, the 32-bit Ubuntu installer did see the Windows install and I was able to dual boot.

I was wondering if there was a way to modify the 64-bit Ubuntu CD so as to disable UEFI boot and force a legacy boot, since I don't have that option from the PC's BIOS (Phoenix SecureCore Tiano).

Thanks in advance.

---

### Post by oldfred on 2015-07-14
You should have two boot options in UEFI boot menu. One UEFI: name of flash drive and the other just :name of flash drive which is then the BIOS boot. If you were able to select CSM/BIOS/Legacy for Windows, I do not understand why you cannot select it for Ubuntu. 

You may also have to turn on allowing USB booting or USB ports. You may have to turn off all UEFI settings and only allow CSM/BIOS settings.

Acer is one that for all its UEFI seem to require a password (never lose that) to open up other settings.

       Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[URL="http://www.youtube.com/watch?v=QGiG1oljjZI"]http://www.youtube.com/watch?v=QGiG1oljjZI
[/URL]
 Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

 Screenshots of secure boot settings Asrock, Asus, HP, Acer
[URL="https://neosmart.net/wiki/disabling-secure-boot/"]https://neosmart.net/wiki/disabling-secure-boot/

      [/URL]
 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

    [URL="https://neosmart.net/wiki/disabling-secure-boot/"]
[/URL]

[URL="http://www.youtube.com/watch?v=QGiG1oljjZI"]
[/URL]

---

### Post by markz2 on 2015-07-14
That's the thing, I don't have any UEFI: vs unmarked (BIOS) boot options in the list. I set passwords in the bios, but it doesn't open up any other options.

The laptop came with Windows 7 from the factory - no Secure Boot stuff, no Windows 8.

For installing Windows 7, as I understand it - when you get to the partitioning screen, when Windows wants to create "additional partitions," a BIOS install results in your OS partition and a 100MB partition. An EFI install results in 4 partitions being created. I was going off the number of extra partitions it created.

Here's the weird part. As soon as I got to the partitioning screen (with a blanked SSD, no partitions, etc.), if I clicked Advanced options and created a new partition, it creates two partitions, the OS partition in the size I specified, and a 100MB partition. However, if I click Refresh BEFORE trying to create partitions, it makes 4 partitions, one of which is an EFI partition.

Once I figured this out, I refrained from clicking Refresh to detect disks (force of habit, there's only one drive in the laptop), and it did a BIOS install.

I read some instructions once for modifying a Windows 7 CD to force BIOS boot by deleting the files that would be detected to start an EFI boot - was wondering if something similar could be done with the Ubuntu CD, since I can't force a BIOS boot from the BIOS settings or boot menu.

---

### Post by oldfred on 2015-07-14
The issue is that Ubuntu will want to convert drive to gpt for UEFI boot. And you have to have MBR for Windows to boot in BIOS mode.
If the other way around or a second drive, Ubuntu can be booted from a gpt partitioned drive with either UEFI or BIOS.
But BIOS has to be MBR(msdos) partitioned.

I do not think removing the efi partition on the installer will boot in BIOS Mode. It needs to be booting in BIOS mode. It has both modes configured and in BIOS you have to choose.

Atached shows typical UEFI and BIOS for a Toshiba flash drive.

Some systems may have you just set to UEFI only or CSM only and then flash drive will only boot in that mode.

---

### Post by kurt18947 on 2015-07-15
Someone will correct me if I'm wrong here but

> However, the Ubuntu 64-bit CD will only boot in UEFI mode - 32-bit CD  boots in legacy mode, but then I can't use the 8 GB of RAM.

is true of Windows but not Ubuntu or other linux distros. Linux has supported something called PAE (physical address extension) for several years. PAE allows up to 64 GB. RAM. From Wikipedia:[INDENT]
The [Linux kernel]("https://en.wikipedia.org/wiki/Linux_kernel") includes full PAE mode support starting with version 2.3.23,[SUP][[18]]("https://en.wikipedia.org/wiki/Physical_Address_Extension#cite_note-18")[/SUP]  enabling access of up to 64 GB of memory on 32-bit machines. A  PAE-enabled Linux kernel requires that the CPU also support PAE. The  Linux kernel supports PAE as a build option and major distributions  provide a PAE kernel either as the default or as an option.

 The NX bit feature requires a kernel built with PAE support.[SUP][[19]]("https://en.wikipedia.org/wiki/Physical_Address_Extension#cite_note-19")[/SUP]
 [Linux distributions]("https://en.wikipedia.org/wiki/Linux_distributions") now commonly use a PAE-enabled kernel as the default, a trend that began in 2009.[SUP][[20]]("https://en.wikipedia.org/wiki/Physical_Address_Extension#cite_note-fedora11-20")[/SUP] As of 2012 many, including [Red Hat Enterprise Linux]("https://en.wikipedia.org/wiki/Red_Hat_Enterprise_Linux") / [CentOS]("https://en.wikipedia.org/wiki/CentOS"), [Ubuntu]("https://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29") (and derivatives like [Linux Mint]("https://en.wikipedia.org/wiki/Linux_Mint")),[SUP][[21]]("https://en.wikipedia.org/wiki/Physical_Address_Extension#cite_note-21")[/SUP][SUP][[22]]("https://en.wikipedia.org/wiki/Physical_Address_Extension#cite_note-22")[/SUP] have stopped distributing non-PAE kernels, thus making PAE hardware mandatory.
 Distributions that still provide a non-PAE option, including [Debian]("https://en.wikipedia.org/wiki/Debian") (and derivatives like [LMDE]("https://en.wikipedia.org/wiki/Linux_Mint")), [Slackware]("https://en.wikipedia.org/wiki/Slackware"), and [LXLE]("https://en.wikipedia.org/wiki/LXLE_Linux") typically do so with "i386", "i486" or "retro" labels.[SUP][[23]]("https://en.wikipedia.org/wiki/Physical_Address_Extension#cite_note-23")[/SUP][SUP][[24]]("https://en.wikipedia.org/wiki/Physical_Address_Extension#cite_note-24")[/SUP]
[/INDENT]
  
I believe that no single app can use more than 4 GB. RAM with PAE.

---

### Post by oldfred on 2015-07-15
And the 64 bit Ubuntu ISO is configured for both UEFI & BIOS. It is FAT32 on flash drive & has an efi partition so UEFI can find it. But it also has syslinux which is a BIOS type boot loader in the MBR. 

So it can boot either way, but you have to select from UEFI/BIOS or use one time boot key like f10 or f12. If a UEFI system it normally shows two choices to boot.

PAE lets you use more RAM but not all at once.
 Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

---

### Post by markz2 on 2015-07-15
I understand that a UEFI system would normally show two choices to boot, but this one doesn't. The laptop's documentation and the way the Windows and Ubuntu installers are loading shows that it is a UEFI system, but the F2 Settings menu or F12 Boot menu do not provide the option to select UEFI or BIOS boot.

Good to know about the PAE support, but 32-bit Ubuntu, while booting in BIOS mode, still doesn't see any other OS (Windows 7) on the machine.

---

### Post by oldfred on 2015-07-15
Have you set the UEFI password as all other Acer users have posted?

---

### Post by markz2 on 2015-07-15
Yeah, I set the Supervisor and User passwords in F2 Settings (not the HDD password).

---

