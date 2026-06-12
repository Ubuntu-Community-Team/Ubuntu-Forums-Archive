---
title: "Dual Boot: No Ubuntu in Grub"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by pradeep5383 on 2013-03-06
Hi, I have Acer Aspire 5560G model with AMD A6 Processor. I have created bootable USB stick with latest Ubuntu 12.10 available as of today.
My Laptop has pre installed Windows 7. Using bootable USB stick, I installed "Ubuntu alongside windows". But on reboot I do not see an option to boot in Ubuntu.
I googled and read many issues with EFI and other problems people see, but still not clear what exactly will solve the issue.
Not sure if my laptop has EFI or BIOS, but there is no option of choosing between two. I also do not see any option of secure-boot in my firmware settings. Its a new model and I think my laptop has EFI and no option to use BIOS.
I have tried boot-repair from "Try Ubuntu", but still I do not see Ubuntu option in Grub. 

Boot-repair url:    [http://paste.ubuntu.com/5592163/](http://paste.ubuntu.com/5592163/)

I also tried EasyBCD and added entry for Ubuntu. This shows ubuntu option at boot time, but when I select this option, it does not boot, and gives me a "grub>" prompt. I do not know how to proceed from there.
Windows boots fine though.

Is EasyBCD really required? I expected boot-repair to add required entry in grub.

I also noticed, when I start the laptop, it says "Windows Boot Manager" where I expect it to display Grub options. 
When I boot from Ubuntu USB stick, it says GRUB version 2.0. 
Do I need to change something to have GRUB and not "Windows Boot Manager" for normal boot of system ?

I really need Ubuntu on my machine. Any Idea what might be missing or what else can I try.
Has any one successfully done dual boot on "Acer Aspire 5560G".

Also it will be a great help if some one can give pointers to identify EFI/BIOS firmware, and also to identify Grub/Grub2 on the machine.

Earlier I did ubuntu 10.04 dual boot with Windiws Vista on my old vaio, and it was so simple with just following the steps given on Ubuntu website, but with new firmwares it is not same anymore.

---

### Post by pradeep5383 on 2013-03-07
**SOLVED**
Figured it out, Its working now finally.
boot-repair again solved the issue.
I guess, in my first try of boot-repair, I did not finished the Grub Installation part completely.
I can now happily use Ubuntu on my new laptop :)

---

