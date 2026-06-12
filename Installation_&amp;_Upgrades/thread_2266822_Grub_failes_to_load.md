---
title: "Grub failes to load"
date: 2015-02-25
forum: Installation &amp; Upgrades
---

### Post by Damir_Anicic on 2015-02-25
Hi, I have a freshly installed ubuntu 14.04 on my acer aspire E 15 alongside windows 8.1. The installer didnt recognize windows 8.1 and after hours of googling and trying gdisk, fdisk, gparted etc, which all failed due to varius reasons ( error messages linked with GPT and MRB, im a ubuntu/computer newbie and the posts about changing filetypes etc were too challenging etc) I decided to select the something else option and do it myself. I freed about 400 gig space and created partitions and installed ubuntu following this guide: [http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation) and using the second option. Everything seems to work fine and ubuntu is installed but i go right into windows when i reboot. I have turned off secure boot and changed the boot order so windows boot is at the bottom (there is no grub boot option in bios, dont know if there should be?). I started ubuntu from the USB stick again and ran boot-repair, but it still wont work. Heres my boot-repair logfile: [http://paste.ubuntu.com/10411722/](http://paste.ubuntu.com/10411722/).

I dont know what else to do, please help.

---

### Post by oldfred on 2015-02-26
I do not think Boot-Repair works with your partition configuration. It only recognizes a separate /boot not all the other partitions and you probably have to mount those also on any chroot.

Normal default install is just / (root) & swap. We often suggest a separate /home and/or separate data partitions. If dual booting with Windows a separate NTFS formated data partition is suggested.

You have an ubuntu boot entry in UEFI:
```
 Boot0003* ubuntu    HD(2,12c800,96000,ff997e74-a157-43cb-8c1e-9dd1767d180b)File(EFIubuntushimx64.efi)


```

But some vendors modify UEFI to only boot the Windows entry and we have to create work arounds.
One that many use is the copy of grub/shim files into /EFI/Boot folder. But you already have a backup & renamed files. Not sure what Boot-Repair put there.
/EFI/Boot/bkpbootx64.efi /EFI/Boot/bootx64.efi 

Is your bootx64.efi a copy of Windows or grub or shim files? Compare sizes.

Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

 Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)
Herman's 2014_02_09 - My Adventure with Secure Boot in an Acer Aspire E1-531 Laptop
[http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html](http://members.iinet.net/~herman546/2014_02_09%20-%20My%20Adventure%20with%20Secure%20Boot%20in%20an%20Acer%20Aspire%20E1-531%20Laptop.html)

---

### Post by Damir_Anicic on 2015-02-26
Thank you very much for your answer. I installed it again with only / and /home partition. Im still loading straight into windows but i managed to get into grub by pressing  f12 and selecting ubuntu in the windows boot loader. I'll use this as a temporary solution and then i'll try to use the workarounds u mentioned.

---

### Post by oldfred on 2015-02-26
Did you install in UEFI or BIOS boot mode? 
And with a re-install you must use Something Else or current versions of Ubuntu may erase entire hard drive. See caution in link in my signature below.

---

