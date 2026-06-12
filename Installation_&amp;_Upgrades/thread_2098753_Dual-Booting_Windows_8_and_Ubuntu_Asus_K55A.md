---
title: "Dual-Booting Windows 8 and Ubuntu Asus K55A"
date: 2012-12-27
forum: Installation &amp; Upgrades
---

### Post by BulletproofIdeal on 2012-12-27
Hi all, so I just got a new Asus K55A laptop pre-installed with Windows 8. I've been researching how to get a dual-boot environment working with UEFI and Win8 and came across this [post]("https://help.ubuntu.com/community/UEFI"), following this I've been able to this screen

[IMG]http://pix.toile-libre.org/upload/original/1347445084.png[/IMG]

however whether I select Try or Install I just get taken to a black screen and nothing happens. I've had no experience with WIn8 or UEFI up until this point so I'm not quiet sure what the problem could be. Any help would be appreciated as I would much rather dual-boot than virtualize Ubuntu. Thanks in advance

---

### Post by oldfred on 2012-12-27
You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings or you may not be able to get back into UEFI/BIOS menu.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

    You may want to review this thread. He seemed to resolve most of the issues with Boot-Repair.

       ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)

    Often extra boot parameters are required for Video issues, but some systems need others.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by BulletproofIdeal on 2012-12-27
Yup I am using 12.10 x64 I disabled Secure Boot in the BIOS and I can actually boot into Ubuntu now. I'll go back and turn off fast boot as well then I'll dive into the actual install. Thanks for the info

---

### Post by BulletproofIdeal on 2012-12-27
Thanks for your help I did have to use boot repair (just used the recommended repair option for future reference) to get Windows booting again after the install finished but everything seems to be working great now. Also for anyone else once you use boot repair I found that I had to launch windows using the WIndows UEFI Loader entry rather than the Windows 8 Loader entry.

---

### Post by dcunited on 2013-01-15
How is it going with the install and Ubuntu on this system in general.  I am really considering buying one.

---

