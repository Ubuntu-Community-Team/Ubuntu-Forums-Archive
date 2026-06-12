---
title: "Install Ubuntu on UEFI Laptop"
date: 2013-08-21
forum: Installation &amp; Upgrades
---

### Post by ahalverson on 2013-08-21
I recently got a computer(Asus K55N-DB81), and have been trying to install Ubuntu. If I leave UEFI on, the Ubuntu disk displays "Binary whitelisted". But if I disable UEFI and turn on "legacy ROM", it displays nothing, and within 10 seconds the disk would shut off and I would be left with a blank screen. I have read a lot of posts, but all of them suggest turning off Secure Boot. My BIOS(or whatever they call it now) doesn't have an option for turning it off.

EDIT: The Ubuntu version that I want to install is 13.04

Thanks,

Andrew

---

### Post by grahammechanical on 2013-08-21
What version of Ubuntu? Secure boot is designed to prevent the installation of software that has not been authorised. This in itself is a fine aim. Ubuntu 12.10 was the first Linux distribution to have a kernel that was signed by a key that would be accepted by Secure Boot machines. Early versions of 12.04 did not have this signed kernel. It should be present in the lastest version of 12.04 available from the download page (12.04.2) and in 13.04.

You will also need the 64bit version.

> If you have a PC with the Windows 8 logo or UEFI firmware, choose the 64-bit download.

That is from the download page.

Many recommend turning off secure boot but it should not be neccessary since the release of 12.10. Other things may well be necessary.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by ahalverson on 2013-08-21
Even when I use the newest version, it still blanks and does nothing.

---

### Post by oldfred on 2013-08-21
You have the only system that we have seen where it does not work. Many new UEFI systems have issues and lots of work arounds which are different by vendor & model, but no one could get a K55N to work.
Maybe Asus has released a newer UEFI/BIOS which you should install.

 Asus K55N just does not boot Ubuntu in UEFI mode. Some things to try, but no solution
[http://ubuntuforums.org/showthread.php?t=2137233](http://ubuntuforums.org/showthread.php?t=2137233)
Asus K55n will not boot in UEFI mode. Boot Parameters? Feb 2013
[http://ubuntuforums.org/showthread.php?t=2111720](http://ubuntuforums.org/showthread.php?t=2111720)
ASUS-K55N is just not able to boot an EFI linux, converted to BIOS with MBR partitioning - UEFI Windows 7
[http://ubuntuforums.org/showthread.php?t=2061646&p=12635283#post12635283](http://ubuntuforums.org/showthread.php?t=2061646&p=12635283#post12635283)

Slightly different Asus that have worked.
 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
      
 Asus x55u UEFI change to BIOS
[http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html](http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html)

---

### Post by ahalverson on 2013-08-21
Oh, :(. I'll keep looking.

Thanks.

---

### Post by Kevin_House on 2013-10-13
I was able to install ubuntu on this exact model by doing what [this guy]("http://forums.linuxmint.com/viewtopic.php?f=46&t=140874") did. All I did was change the options in the BIOS and that solved it. I didn't even have to deal with the GRUB stuff. Also, I was just replacing windows instead of trying to set up a dual boot, so it was all quite straight-forward.

---

