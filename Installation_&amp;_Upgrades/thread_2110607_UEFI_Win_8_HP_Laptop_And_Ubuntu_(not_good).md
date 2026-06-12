---
title: "UEFI Win 8 HP Laptop And Ubuntu (not good)"
date: 2013-01-30
forum: Installation &amp; Upgrades
---

### Post by koldreader on 2013-01-30
Hello Ubuntu Community 

I am posting to inform you all of a recent experience I had with you ubunu IF YOU HAVE RECENTLY BOUGHT A NEW WINDOWS 8 COMPUTER YOU MAY WANT TO READ THIS!

I tried installing Ubuntu to boot along side Win 8, the booting failed so I looked into it. It turns out the normal installation is not compatible with UEFI systems but there is a page ubuntu provides that have instructions on how to install ubuntu on UEFI computers. It tells how to use the "boot repair" to fix the issue, so that's what I did."

This prevented Windows from booting anymore and windows repair tool failed to fix the problem, HPs factory restoration failed and eventually became inaccessible! Lucky for me HP offers repair disks that they are mailing me to fix my computer but otherwise ubuntu ruined it pretty good! The boot repair gave me this URL for further details

[http://paste.ubuntu.com/1573485/](http://paste.ubuntu.com/1573485/)

I post this because I wanted people to know Ubuntu EFI might be flawed at the moment and users with new Windows 8 machines might wanna hold off installing it to avoid this frustration I am dealing with.

At the moment I am running Linux Mint 14 live from a USB stick but wouldn't dare try to install it and damage my machine further!

---

### Post by oldfred on 2013-01-30
It looks like you tried to install wubi. Wubi does not work with gpt partitions and all systems with Windows 8 preinstalled and UEFI use gpt.

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

    
Only a few versions of Linux work with secure boot.
        The State Of Linux Distributions Handling Secure Boot
[http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI](http://www.phoronix.com/scan.php?page=news_item&px=MTI2MzI)

    
Some have installed to HP and many others. Major issues do exist with some Samsungs.
       HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)

---

### Post by bcbc on 2013-01-31
I'm not sure why boot repair would install a MBR bootloader on a EFI system, or be messing with the boot flags. I don't know if this break anything per se, but why mess with stuff unnecessarily.

Wubi doesn't work with Windows 8 preinstalled - period. Running boot repair or anything else won't help. Making random modifications to your system won't work either.

Did you make any other changes? e.g. switch from UEFI to legacy boot? That will stop windows from booting as well.

I've mentioned the problem with boot repair and wubi a couple of times, but it appears to have fallen on deaf ears.

---

