---
title: "Boot Problems"
date: 2012-02-24
forum: Installation &amp; Upgrades
---

### Post by KalebZen on 2012-02-24
Hi All,

I've accidentally erased my Windows 7 boot loader. Oddly I've changed the order of my hardrives post Windows install and pre Ubuntu install.

Windows 7 boot loader was on my current sdc but Windows is installed to sda1. I switched the order of the drives in my BIOS after I realized I had them ordered incorrectly. Then, I setup Ubuntu and wiped the sdc partition which axed my Windows bootloader so the Grub chainloader step was broken. Update-grub2 doesn't repair the Windows bootloader and Boot-repair doesn't seem to help either.

Here is my boot-info from Boot-repair:
[http://paste.ubuntu.com/856136/](http://paste.ubuntu.com/856136/)

Thanks in advance if you can help. Is there some way to boot Windows directly from Grub2 or do I need to get a Windows bootloader onto the drive somehow? If I do, how can I recover the windows installation?

Also I think I have Grub2 installed on all drives via boot-repair. Does this matter and is it possible to remove them?


So now I have:

sda
    sda1 - windows 7 ntfs
    sda2 - extended
           sda5 - linux swap
           sda6 - ext4 ubuntu install
sdb1 - ntfs storage
sdc1 - ntfs storage

Yikes! Thanks.

- Kaleb

---

