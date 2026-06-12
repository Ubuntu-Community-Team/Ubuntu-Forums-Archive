---
title: "Ubuntu 18 install failed, MSI B350 main board, Couldn't get UEFI db list"
date: 2018-05-22
forum: Installation &amp; Upgrades
---

### Post by ascii1011 on 2018-05-22
Hi all,

I have a similar issue.

Trying to install Ubuntu 18.04 with a MSI Tomahawk b350 board + Geforce CTX 1050 video card and getting something like this:

Couldn't get size: ...
MODSIGN: Couldn't get UEFI db list
Couldn't get size: ...

ubuntu splash screen comes up, goes through changing 7 of the dots under the ubuntu logo to white... then freezes and keyboard stops working...

I have tried all combinations for boot sequence and have no "secure boot" options... and the manual seems to be fairly useless as usual

I was previously able to install Ubuntu 16.04... can't remember what previous incantation I performed to get it to install... these companies are driving me crazy with the complexity of os installs now...


Thank you and Any help would be greatly appreciated

---

### Post by oldfred on 2018-05-23
With nVidia you need nomodeset boot parameter.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) 
            [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710) 
    
Have you updated UEFI from MSI for your motherboard?

       MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)
ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)
ryzen acpi=off only 1 cpu, needs nomodeset & then nVidia driver instead
[https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu](https://askubuntu.com/questions/951630/fix-ubuntu-16-04-issue-with-gigabyte-ga-ab350-motherboard-and-amd-ryzen-cpu)

---

