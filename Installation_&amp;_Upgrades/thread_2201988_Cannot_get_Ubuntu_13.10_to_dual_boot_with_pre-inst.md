---
title: "Cannot get Ubuntu 13.10 to dual boot with pre-installed windows 8.1. Weird problem"
date: 2014-01-26
forum: Installation &amp; Upgrades
---

### Post by ali12 on 2014-01-26
So I've installed Ubuntu on multiple pcs multiple times and this time i am stumped. So I have a UEFI bootloader and I've turned off secure boot, fast boot, and put it into csm mode. At one point i had them both booting perfectly but then i deleted the partition because i didn't like the partition layout. So what im encountering now is that every time i install ubuntu after formatting my hd partition and setting aside free space for it(using windows diskmanagement), the grub menu always boots into minimalist bash commands mode which makes it impossible to boot ubuntu. I've tried boot repair with the Live CD but it doesn't seem to work. What's weird is that i've reinstalled it about 7 times and each time im getting the same grub terminal at the start once i set my bios to boot ubuntu first. Something to take into account is that not once has my windows os has been affected in way shape or form. I somehow am always able to boot into windows perfectly. Could anyone give me any insight on this?

edit: I have an asus x550lc model notebook

---

### Post by oldfred on 2014-01-27
Did your first install work because it was CSM/BIOS. From grub you would not be able to dual boot if Ubuntu is in CSM mode. But can dual boot from UEFI menu or one time boot key.

Some systems only boot Windows from UEFI menu, Boot-Repair has a work around.
And they may only install in BIOS mode, and Boot-Repair can convert to UEFI.

Asus seems to have a different model number on every computer it builds. Not sure what may be similar to yours.

       ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)
  [SOLVED] Dual Boot on Asus K55vd SX696H - 8 GB (Solved) EFI
[http://ubuntuforums.org/showthread.php?t=2151394](http://ubuntuforums.org/showthread.php?t=2151394)
Asus N56VJ-SH71-CD Shows default Windows partitions Post #25 install instructions
[http://ubuntuforums.org/showthread.php?t=2105622](http://ubuntuforums.org/showthread.php?t=2105622)
HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)
ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Asus UltraBook - kernel comparisons K56CA
[http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI](http://www.phoronix.com/scan.php?page=news_item&px=MTMzOTI)
Asus Zenbook Prime UX31A (UEFI)  Blank screen resolved by turning secure boot off, many tests of Boot parameters
[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)
 install 13.04 on asus ux32a, problems with usb boot - several reports working well no details
[http://ubuntuforums.org/showthread.php?t=2146440](http://ubuntuforums.org/showthread.php?t=2146440)
Asus x55u UEFI change to BIOS
[http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html](http://www.canbike.ca/information-technology/2013/03/12/asus-uefi-boot-from-cd-dvd-x55u.html)
Asus ASUS Zenbook Prime UX32VD  Windows vs Linux
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_zenbook_gfx&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_zenbook_gfx&num=1)

---

