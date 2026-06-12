---
title: "No available partitions on Acer Aspire E 15 with Windows 8.1"
date: 2015-03-24
forum: Installation &amp; Upgrades
---

### Post by Ruben Remus on 2015-03-24
Bought a new Acer Aspire E 15 (E5-521-48KN) loaded with Windows 8.1. I want to partition my drive to install Ubuntu with separate partitions for root, swap, boot, home and Windows data. I fired up gparted and found what looks like five physical partitions.

One has some sort of warning symbol, is labeled Microsoft reserved partition and does not show up in the Windows Disc Management.

What are my options for creating an extended partition that I can create all the logical partitions I want?

I have attached screenshots of gparted and Windows Disc Management.

Thanks!

---

### Post by grahammechanical on 2015-03-24
Windows 8.1 pre-installed = GUID Partiton Table (GPT) and not the old Master Boot Record (MBR) partition table with a limit of a maximum of 4 primary partitions.

You will also have a UEFI boot sytem and not a BIOS boot system. So, you should read this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Remember, use Windows utilities to defrag Windows more than once checking each time that Windows loads. Use Windows utilities to resize Windows partitions to create unallocated space for Linux partitions. Use a Linux partitioner to create Linux partitions out of the unallocated space and with an Ext4 format. Gparted in a Ubuntu Live session will do it. And then use the Installer's Something Else options to direct the installer to the partitions you want Ubuntu to install into and use.

Oh, one more thing. There are many threads on this forum relating to Installing Ubuntu with Windows 8.1. Read them. See what to expect.

Regards.

---

### Post by oldfred on 2015-03-24
Microsoft reserved is unformatted, so gparted has issues with unformatted partitions. It will also show similar issue with a bios_grub partition which is unformatted or any encrypted partitions as it cannot parse them to know what format they are formatted.

Additional links to most of the UEFI info you need is in link in my signature. Lots of data, but UEFI is a bit more complicated.

Important issues are to have good backups of Windows & efi partition, a Windows repair flash drive and use Windows to shrink its NTFS partition and reboot immediately. Make sure Windows fast boot or hibernation is off, and if UEFI has fast boot turn it off also. 

       Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

Acer's seem to need users to set passwords to allow you to change settings. Never lose that password.

 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
While different models, Acer will be similar across most models:

 Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)

---

### Post by Ruben Remus on 2015-03-25
Thank you so much to both of you!

---

