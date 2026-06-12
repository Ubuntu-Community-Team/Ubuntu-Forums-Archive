---
title: "Dual boot UEFI"
date: 2019-06-17
forum: Installation &amp; Upgrades
---

### Post by danielsender on 2019-06-17
This will be the first time I will be installing Ubuntu in the UEFI boot mode. The machine is a Dell M6800 that has windows 10 already installed. When I browse the boot options in the BIOS page I don't see the boot order unless I set it in legacy mode, that I know from reading other articles that I shouldn't do that. I burnt 18.04.2 on a DVD, so what should I do to get the machine to boot the DVD and ensure that I'm doing UEFI?

Many thanks in advance

---

### Post by yancek on 2019-06-17
Start by reading the Ubuntu documentation at the link below and come back with any specific questions.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-06-17
Just about all Dell need UEFI update & if SSD firmware update.

My Dell SFF has a Haswell lower end processor - Intel Core i3-4160, I do not think I had to change UEFI setting to AHCI, from RAID or Intel RST, but your laptop may have that. But you may need several UEFI setting changes.

You should get two boot entries in your UEFI boot menu, f12. One clearly UEFI:flash and other flash which is BIOS boot. Not sure what DVD shows as I stopped using DVD years ago. I used to burn a lot of coasters (bad burns). Even have actually used as coaster. :) Microcenter is just down the road and its OEM flash drives have always worked for me.

You also will need nomodeset boot parameter, since you have nVidia.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

I recommend installing LTS versions, but I just installed 19.10 and when I checked include proprietary drivers, it now installed the nVidia driver to my desktop system. 
You will have to use nomodeset on first boot or until you install nVidia driver from Ubuntu repository.

More info on UEFI install in link in my signature.

---

### Post by danielsender on 2019-06-19
I did the "vanilla" install, not the "something else" and everything went well. What called my attention is that it didn't create a swap partition but a swap file. Just in case of going into sleep mode I created a swap partition.

Thank you very much guys.

---

