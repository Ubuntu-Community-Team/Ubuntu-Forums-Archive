---
title: "problem booting ubuntu"
date: 2016-03-13
forum: Installation &amp; Upgrades
---

### Post by ilia_avramov on 2016-03-13
I've been a long time Ubuntu user (8 years)
I just bought a brand new laptop ACER ASPIRE V5-591G-588D. It came with no OS (just basic linpus with no GUI, instead of freedos). I want to have 2 OS - Windows 10 (just in case) and Ubuntu. First I installed Windows 10. During the install process I created 4 partitions. 2 for windows (1 for data and one for the windows himself) and 2 for ubuntu (1 for root and 1 for home). There was already 1 partition, which I'm pretty sure was the EFI. After creating the main windows partition it created one small (16 mb) MBR partition. The installation went well. After that I installed ubuntu (14.04.4). The installation went just fine, but it turned out that I can't boot into ubuntu. Every time it booted windows. I tried fixing the boot menus with easybcd, but it wasn't successful. I tried using boot-repair, efibootmgr reinstalling ubuntu several times but nothing worked. Then I wiped everything from the HDD and created a new partition table - GPT using gparted. It consists of:
1. Boot partition (500 mb). I putted the boot flag on it. Filesystem FAT32
2. unnallocated (reserved for windows)
3. ubuntu root (30 gb)
4. ubuntu home (~400 gb)
5. linux-swap (8 gb)
Then I proceeded with ubuntu installation, but it was still not booting. It says there is no boot media. 
My BIOS configuration is:
UEFI: ON
Secure boot: Disabled (tried both)
Boot order: 1. Windows boot manager (even though there is no windows on the computer), 2.HDD0, 3.HDD1, 4.USB-HDD and so on. When I tried to lower the priority of windows boot manager, it still tries to boot in windows and continues to not see ubuntu at all. I can't erase this windows boot manager and I am starting to think that this option is part of the uefi firmware of the computer. In any case It just wants to boot windows and nothing else.
I wonder why it shows windows boot manager if there is no windows at all. I expect to see ubuntu there (in the boot menu), but there is nothing and through all my reinstalls it never showed up.
What's wrong with my installation? Is it the EFI partition or something in the BIOS config? If I use legacy bios instead of uefi the windows boot manager disappears. Then I might be able to install ubuntu, but no windows. The computer also does not support any older versions of windows.

---

### Post by grahammechanical on 2016-03-13
> I wonder why it shows windows boot manager if there is no windows at all.

I think that is caused by the UEFI boot system having old information and not being updated in some way. You may need to edit UEFI to remove that Windows label.

Are you aware that if Windows 10 is installed in EFI mode then Ubuntu has to be installed in EFI mode as well? Otherwise we get a situation like this.

UEFI also comes with GPT partitioning for the hard disk. I think that Windows 10 needs GPT. With GPT there is a need for a efi boot partition in which the efi boot files go. The Ubuntu installer if loaded in EFI mode will install Ubuntu in EFI mode and put Ubuntu efi boot files in the efi boot partition by default & alongside the Windows efi boot files.

I would suggest to install Windows 10 first and then Ubuntu after referencing this guide

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

And then if it is not successful to use Boot Repair and get the BootInfo summary report and post the URL in this thread so that we can see the situation.

Regards.

---

### Post by fantab on 2016-03-13
Please post your [Boot Info]("https://help.ubuntu.com/community/Boot-Info") as described in the link.

---

### Post by ilia_avramov on 2016-03-14
PROBLEM SOLVED!
It turned out the problem was in the bios settings. I switched "secure boot" on which unlocked few more options. One of them was "Select an UEFI file as trusted for executing" that's in the "security" tab. After that it showed me HDD0, I hitted enter and "EFI" showed up. After another ENTER it showed 3 folders "ubuntu", "microsoft" and "boot". The ubuntu folder contained "shimx64.efi", "grubx64.efi" and "MokManager.efi" I'm not very familiar what all of them were, but I chosed "shimx64.efi" which was then added as "trusted for executing". I went back to the boot tab and found "EFI boot0: ubuntu" or something like it. That's because I named the "trusted" UEFI file "ubuntu". I moved it up to first priority and everything worked like a charm.
Thanks for the advices, they made me search for my own mistakes in the bios configuration.

---

