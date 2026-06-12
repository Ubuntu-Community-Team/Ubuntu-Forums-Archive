---
title: "windows 8 not detected"
date: 2014-06-16
forum: Installation &amp; Upgrades
---

### Post by Pedroski55 on 2014-06-16
Hi, my friend asked me to install Ubu 14.04 on his Toshiba laptop which runs Win 8.

His hard drive had /dev/sda1, 2, 3, 4, 5 I don't know why Win 8 sprawls so much. Win bootmgr is in /dev/sda2 I shrank his backup win partition, which was half his hd down to 40GB, then made a swap partition. Then made a virtual partition /dev/sda7/ to install Ubu on. 

Ubuntu does not find Win 8. After installing, I re-ran update-grub. No joy.

I have a screenshot of gparted below. At installation, Ubuntu moaned about installing grub. It did not say, "it is probably safe to install grub in the mbr", which I usually see. I am not sure where it installed it.

I tried copying the win part of my grub.cfg into my friend's grub.cfg, but grub just came up with "no such partition"

Here is the win part of my grub.cfg

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-52144CA3144C8C43' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  52144CA3144C8C43
    else
      search --no-floppy --fs-uuid --set=root 52144CA3144C8C43
    fi
    parttool ${root} hidden-
    chainloader +1
}

How can I alter it to make Win 8 work on my friend's computer?? Should I run grub-install again, or what?

---

### Post by squakie on 2014-06-16
Have you tried boot-repair?

---

### Post by Pedroski55 on 2014-06-16
There is nothing wrong, I don't need boot repair. I just thought of something though: using Ubu 12.04, update grub would not find my Fedora insallation. I had to mount it first. I'll try that with Windows!! In Fedora, grub2-mkconfig always finds Ubu and Win without having to mount them!

---

### Post by oldfred on 2014-06-16
If Windows is in UEFI mode, and you installed Ubuntu in BIOS mode using the gpt partitioned drive's MBR then you cannot boot Windows from grub menu. 
UEFI and BIOS are not compatible, so once you start booting in one mode you cannot switch to other boot mode. Or by the time grub menu has loaded you are stuck in one mode and can only boot systems installed in the same mode as grub/Ubuntu.

You can use Boot-Repair to convert a BIOS install to UEFI. Or install in UEFI boot mode. But see MAJOR caution on reinstall in UEFI info link in my signature if you reinstall. It may erase drive if you do anything other than Something Else.

---

### Post by Pedroski55 on 2014-06-16
You are right. Ubuntu would not install in UEFI mode, because I could not set the BIOS to boot from the usb stick. So I set the bios to legacy or CSM I think it was. Only then would it boot from the usb stick. I thought everything was good then!! 

I will read your links carefully.

Any suggestions about the best way forward in this particular situation? Seems like a can of worms! Why can't Ubuntu 14.04 boot in UEFI mode from a usb stick?

I gather from a quick read that windows has practically done this to prevent the use of other systems. Is that really so? Even in the US there must be laws against that!

---

### Post by oldfred on 2014-06-16
I thought Toshiba's were ok, I know users have issues with HP & Sony.
Some older Toshiba with early UEFI had major issues.

        [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)
How to install Ubuntu 13 dual boot with Windows 8 Ubuntu Studio
[http://ubuntuforums.org/showthread.php?t=2186838](http://ubuntuforums.org/showthread.php?t=2186838)

---

### Post by Pedroski55 on 2014-06-16
Put another way: I know I have UEFI. I want to install Ubuntu 14.04 from a usb stick (or dvd). The computer will not boot from the usb stick. What is the best way to get Ubuntu 14.04 up and running in a dual boot situation. I don't mind reinstalling. Can I do this without having to do a 'boot repair'?? Since UEFI is not too new, I'm surprised 14.04 can't handle it.

Thanks for the links. I will read them carefully.

---

### Post by Pedroski55 on 2014-06-16
Wikipedia on UEFI: Secure boot is supported by [Windows 8]("http://en.wikipedia.org/wiki/Windows_8"), [Windows Server 2012]("http://en.wikipedia.org/wiki/Windows_Server_2012"), and a number of [Linux distributions]("http://en.wikipedia.org/wiki/Linux_distribution") including Fedora, OpenSuse, and Ubuntu.

---

### Post by oldfred on 2014-06-17
Ubuntu will install with secure boot. But currently grub has a bug with Windows 8.1 where you cannot boot Windows from grub menu if secure boot is on. That probably is all distributions as grub2 is common. The only difference may be version or version with more fixes.

Often you have a UEFI/BIOS setting to turn on USB boot or USB port use with UEFI. 
A few system require you to set a password to open those menu settings, but if you create a UEFI password never ever lose that password.

UEFI secure boot is more a Windows marketing where Windows has had many security issues. But almost none of the security issues have been related to booting. The largest boot sector virus and only major one was actually issued by Sony to control your system if using Sony software.

       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

### Post by Pedroski55 on 2014-06-17
Thanks for that. I messed with my friends Toshiba today. Ubuntu starts fine. The boot mode for Ubuntu is CSM. If I enter the bios and change the settings in tab 'Advanced' to boot mode = UEFI and in the tab 'Security' (I think, can't remember right now)  set secure boot = enabled, Windows boots. So both systems are up and running and in good condition.

The trick now is, get them both in the grub boot.

I'm thinking of a new install using this: [https://wiki.ubuntu.com/USBStickUEFIHowto](https://wiki.ubuntu.com/USBStickUEFIHowto)

But the first stumbling block is, I can't find usb.img. Not on my computer, not on the usb stick. What are they talking about? Is the page out of date??

---

### Post by oldfred on 2014-06-17
I think in that case they are saying the image on the flash drive. Macs use .img files. PCs use ISO and all ways that you install Ubuntu to a flash drive make a dual UEFI or BIOS boot system.
It looks like they are installing a separate /efi partition.

The flash drive installer is FAT32 which UEFI will read and look in /boot where grub exists. Or syslinux is in MBR for BIOS boot.

Ubuntu site has standard install instructions which work for many.
       Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

