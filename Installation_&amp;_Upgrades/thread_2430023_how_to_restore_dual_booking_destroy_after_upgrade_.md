---
title: "how to restore dual booking destroy after upgrade to 19.10 ??"
date: 2019-10-26
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2019-10-26
I have just upgrade to 19.10 it has override my dual booting windows.
does any one know how to restore this ?
Cheers

---

### Post by Impavidus on 2019-10-26
Which version of Windows? Do you use legacy booting or UEFI?

My guess is that some Windows upgrade enabled FastStartup. This means that the os-prober can no longer detect Windows, which means that it's dropped from the grub menu the next time that grub is updated. That happened when you ran your release upgrade. It could have happened at any normal kernel upgrade too.

Can you boot Windows from the UEFI menu? If you can, make sure FastStartup is disabled. Use the UEFI menu to get back to Ubuntu, update grub and hopefully it will detect Windows.

---

### Post by hoboy on 2019-10-26
I can't boot windows

---

### Post by hoboy on 2019-10-26
I usw windows 10

---

### Post by hoboy on 2019-10-26
when ubuntu startup is launched 
I see Windows 8 ( on /dev/sta5)
when I select then enter
error:
can find command drivemap.
invalid EFI file path
Cheers

---

### Post by Impavidus on 2019-10-27
Use [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) to create a boot info summary and post the link. That may give us some useful information.

---

