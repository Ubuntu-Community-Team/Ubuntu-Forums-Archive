---
title: "Where the uefi is booting grub from?"
date: 2013-02-03
forum: Installation &amp; Upgrades
---

### Post by mylvari on 2013-02-03
I've successfully installed ubuntu to dual boot with windows 8.

However i had to use boot-repair to get grub started instead of win8. I can't find any ways to change which file uefi is starting by default so it must be a fixed location.

Any easy ways to identify where grub starts from? There are a lot of files that boot-repair replaced with grub binary; replacing each of them after another and booting would be a tedious job.

---

### Post by oldfred on 2013-02-03
Welcome to the forums.

Best to see details:

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
    
You should be able to go into UEFI menu, not from Windows but direct boot into UEFI/BIOS.
With UEFI all systems install boot files into the efi partition in separate folders.

---

