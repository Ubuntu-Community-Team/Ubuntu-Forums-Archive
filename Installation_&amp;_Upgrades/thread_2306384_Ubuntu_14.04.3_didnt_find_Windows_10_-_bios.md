---
title: "Ubuntu 14.04.3 didnt find Windows 10 - bios"
date: 2015-12-15
forum: Installation &amp; Upgrades
---

### Post by tmschochola on 2015-12-15
Hi, i have problem with **installing Ubuntu 14.04.3 in dual boot with Windows 10**. Before that i had installed it correctly, but with Windows 7. I have **clean installed Windows 10**, than tried to install ubuntu, but it **didnt find windows**. I was looking up for it on forums. I turned **off fast startup** on windows, tried to turn **off uefi**, but my computer doesnt have it. Its **BIOS**. I clean reinstalled the Windows. Nothing works. Can you help me? My computer is **Acer Aspire M3802**. (only graphic card was changed to Radeon HD6450)
Thank you very much.

---

### Post by grahammechanical on 2015-12-15
Please explain what you mean by "didn't find Windows." Do you mean, when you ran the installer and came to the page to select an install option the installer did not offer to Install Alongside Windows. But to only Erase disk and install Ubuntu?

If you have a BIOS motherboard then you will have MBR partitioning. That means there is a 4 Primary partition limit. If Windows 10 & the manufacturer are using 4 primary partitions, then there is no place for Ubuntu to be installed. And so the installer cannot offer to install alongside. The installer needs at least one of the 4 allocated primary partitions to use as an Extended partition. In the extended partition the installer will then create 2 Logical partitions - one for Ubuntu and one for Swap.

Regards.

---

### Post by tmschochola on 2015-12-15
Yea, i mean, that it doesnt offer to install alongside Windows. I watched into gparted, windows has taken only 2 primary partitions. One 500mb system reserved, another-one 500gb disk C:. So there is 200gb left for ubuntu to install. So i dont know wheres the problem. I will try to create that extended partition if it helps or not. Thanks for your answer.

---

### Post by tmschochola on 2015-12-15
I pre-created the extended partition. It didnt help. It still says , no other operating systems detected. Erase whole disc and install ubuntu ... blah blah blah
Than i tried ubuntu 15.10 and it showed me that win 10 is installed. But the problem is that, internet connection or something like this doesnt work properly. Mozilla always says , no internet connection, when i hit F5 sometimes it loads a website, but most of the time not. So at least if you can help me how to solve this internet problem ill be happy. Thanks

---

### Post by sudodus on 2015-12-15
Welcome to the Ubuntu Forums :-)

You can try 14.04.3 LTS again, and at the partitioning window select **Something else**. It means manual partitioning and gives you better control of what is happening.

Select where to install the root partition (and the swap partition), and finally, at the bottom of the window, select where to install the bootloader. It should be at the head of the drive /dev/sda for the first drive (/dev/sdb for the second drive ...). Do not install the bootloader into a partition, so use no digit.

---

