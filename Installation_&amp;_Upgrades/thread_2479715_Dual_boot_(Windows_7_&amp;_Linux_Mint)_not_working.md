---
title: "Dual boot (Windows 7 &amp; Linux Mint) not working"
date: 2022-10-04
forum: Installation &amp; Upgrades
---

### Post by saketo on 2022-10-04
Hello Ubuntu lovers,


I am trying to sort out the issues that I have with the dual booting. I use Asus K555L laptop with Windows 7 as my main OS. Secure boot is turned off. I already have Ubuntu 22.04 installed on the same drive and the volumes look like this:

[IMG]https://i.ibb.co/jHcf6w3/Linux.jpg[/IMG]
** Had to create a separate EFI volume, so I could install Ubuntu successfully (512 MB).*

When booting through the PC Boot menu I can choose the OS that I wish loaded and they work just fine. However, at the beginning I did not have any available boot menu. Then I used under Windows EasyBCD and managed to get that menu working, however when I click on the Ubuntu option it does not load. The error message that I get is this one:

> GRUB4DOS 0.4.6a 2018-11-05, root is (0x00, 1)
Processing the preet-menu ....
GRUB4DOS 0.4.6a 2018-11-05, Mem: 630K/2250M

Minimal BACH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename

----

I guess the reason is within this info:

There are a total of 2 entries listed in the bootloader.


Default: Windows 7
Timeout: 10 seconds
EasyBCD Boot Device: C:\


Entry #1
Name: Windows 7
BCD ID: {current}
Drive: C:\
Bootloader Path: \Windows\system32\winload.exe


Entry #2
Name: Ubuntu
BCD ID: {eccc07dd-7432-11e5-a943-b2b0a8fe6357}
**Drive: C:\**
**Bootloader Path: \NST\AutoNeoGrub0.mbr**

---

How could I solve this issue, please? Any ideas to point me in the right direction? Thank you.

---

