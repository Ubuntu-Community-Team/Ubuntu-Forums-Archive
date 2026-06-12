---
title: "Windows 8  and Ubuntu 12.04 Dal Boot"
date: 2012-12-20
forum: Installation &amp; Upgrades
---

### Post by harikrish07121991 on 2012-12-20
Can any1 tell how to install ubuntu using wubi.exe in already existing windows 8 system?

---

### Post by oldfred on 2012-12-20
Welcome to the forums.

It is my understanding that wubi does not work with gpt partitions and since Windows 8 pre-installed systems are all UEFI, they are then gpt partitioned.

But with gpt partitions there is no 4 primary partition limit, so you can easily shrink Windows by 25GB using the Windows mmc and install a smaller test install. Or shrink more and install into as much space as you want.

Some have to turn secure boot off, but Ubuntu will work with secure boot. You also will need Boot-Repair to make some fixes after the install.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive or DVD in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

Others that have installed:
       Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by gdubz on 2012-12-24
> **oldfred said:**
> Welcome to the forums.
 
It is my understanding that wubi does not work with gpt partitions and since Windows 8 pre-installed systems are all UEFI, they are then gpt partitioned.
 
But with gpt partitions there is no 4 primary partition limit, so you can easily shrink Windows by 25GB using the Windows mmc and install a smaller test install. Or shrink more and install into as much space as you want.
 
Some have to turn secure boot off, but Ubuntu will work with secure boot. You also will need Boot-Repair to make some fixes after the install.
 
You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive or DVD in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
 
Others that have installed:
Asus x202e dual boot Win 8 full and Ubuntu post #13
[http://ubuntuforums.org/showthread.php?t=2092966](http://ubuntuforums.org/showthread.php?t=2092966)
Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)
 
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 
I'm new to Ubuntu and this forum, but here is one to add to your list:
 
[FONT=Calibri][SIZE=3]I just got Ubuntu 12.10 to boot on a new HP Envy DV7 a couple of days ago. [/SIZE][/FONT][FONT=Calibri][SIZE=3]This is how I achieved dual boot with vendor (HP) installed Windows 8 / Ubuntu 12.10 on the machine that&#8217;s in the linked data sheet, with manufacturing date 08/12:[/SIZE][/FONT]
 
[[FONT=Calibri][SIZE=3]http://www.shopping.hp.com/shopping/pdf/c2h70ua.pdf[/SIZE][/FONT]]("http://www.shopping.hp.com/shopping/pdf/c2h70ua.pdf")
 
[FONT=Calibri][SIZE=3]The chipset is HM77 (35w Ivy Bridge i5 Dual Core processor)[/SIZE][/FONT]
 
[FONT=Calibri][SIZE=3]I put the x-64 12.10 Live ISO on a USB stick for install. I think I used a USB 3.0 port.[/SIZE][/FONT]
 
[COLOR=#333333][FONT=Tahoma]In UEFI (F10 menu):[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]&#8226; &#8226;Disable Secure Boot. I could not achieve boot in any configuration with it on. [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]&#8226; &#8226;UEFI boot scheme (not Legacy BIOS). I tried Legacy mode, and can boot from disk/USB, but not from an installation on the hard drive. UEFI flies right by it during boot every way I tried with it on. [/FONT][/COLOR]
 
[COLOR=#333333][FONT=Tahoma]In Ubuntu:[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]&#8226; &#8226;/Boot=EFI, /=EXT4, /Home=EXT4, SWAP=swap. With UEFI, [/FONT][/COLOR]
 
[COLOR=#333333][FONT=Tahoma]I don't beleive it matters if the partitions are primary or logical, because UEFI support >4 primary partitions...but just in case I made the EFI boot partition primary, and the other 3 listed as logical. Back on W8 All now 7 combined partitions (3 Windows, 4 Linux) show up as the same level without designation (primary or logical).[/FONT][/COLOR]
 
[COLOR=#333333][FONT=Tahoma]With this configuration I can boot with user intervention during the boot sequence: [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]1) During the boot sequence, select F9 to obtain Boot options in UEFI (BIOS) [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]2) In UEFI / BIOS, select the available Ubuntu Linux 2.6.32-21 option and proceed. [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]3) Ubuntu GRUB boot option screen is now available. Select preferred option and proceed. [/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]4) I'm in.[/FONT][/COLOR]
 
Of note: The exact same procedure with Mint 14.1 did not work. No matter what configuration I tried, the install on the hard drive would not boot. UEFI / W8 flew right by it, and no option in UEFI for Mint was present.

---

