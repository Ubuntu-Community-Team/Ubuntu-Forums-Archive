---
title: "Ubuntu/Win10 dual boot, LUKS encrypted. Windows stops booting after update."
date: 2022-07-02
forum: Installation &amp; Upgrades
---

### Post by elpeque2 on 2022-07-02
Here is the output from boot-info: [URL="https://paste.ubuntu.com/p/BSbG92jRkW/"]https://paste.ubuntu.com/p/BSbG92jRkW/

[/URL]
I got a win10 laptop. I installed ubuntu as a dual boot and with LUKS encryption on root and swap partition. For a few months I could boot into both windows and ubuntu just fine from the grub menu. It seems after some windows update I'm still being booted into the grub menu, there is still a windows boot manager entry but if I select it I'm just immediately sent back to the grub menu.

I'd just try boot-repair, but I'm not sure if it will work (and not break things even more, I need to boot into ubuntu to be able to work) given I'm using the LUKS encryption as mentioned above.

When starting the program, encryption is detected and I'm suggested to open the fs with: sudo cryptsetup luksOpen /dev/nvme0n1p6 myvolume

Such command runs fine. I'm prompted for the encryption password and it is accepted with no errors.

But then I run boot-repair again I'm I still get the same message:

[I]You may want to retry after mounting your encrypted partitions so that the tool can verify their contents. (sudo cryptsetup luksOpen /dev/nvme0n1p6 myvolume)
Are you sure you want to continue anyway?[/I]

So I'm afraid to continue.

Please advice.

Ale

---

### Post by elpeque2 on 2022-07-02
by the way, if I try to boot into windows from the bios menu, i'm also sent back to the bios boot menu immediately

---

### Post by yancek on 2022-07-02
>   if I try to boot into windows from the bios menu, i'm also sent back to the bios boot menu immediately 				

If you can't boot windows from the EFI boot menu in the BIOS firmware, your problem is not with Grub or Ubuntu but with windows and you will need to repair the windows boot with windows software. The boot repair software will do no more than create a chainload entry for windows and if its boot files are corrupted, it can't be repaired with boot repair.  

Did you have any problems with the windows update, warning or error messages?  Is your windows install the standard UEFI install?

If I understand correctly, you can still boot Ubuntu but not windows, is that correct?  If so, I would post at a windows forum or go to the microsoft support site.  You could try the suggestion at the site below.  If you try different methods, please make notes on exactly what you did.

[https://www.itechguides.com/windows-10-not-booting-after-update/](https://www.itechguides.com/windows-10-not-booting-after-update/)

The link below has some suggestions.

[https://answers.microsoft.com/en-us/windows/forum/all/pc-wont-boot-after-lastest-windows-10-update/7362b408-f998-4aef-97b1-8cfdf4bf715c](https://answers.microsoft.com/en-us/windows/forum/all/pc-wont-boot-after-lastest-windows-10-update/7362b408-f998-4aef-97b1-8cfdf4bf715c)

---

### Post by elpeque2 on 2022-07-02
Yes. Windows was installed from factory (X1 Thinkpad).

I don't  remember any errors during updating. I don't use windows very  often. I  only noticed the problem after several weeks of not booting  into  windows.

My worry with a windows software based repair is that it  will probably screw up my linux boot which is currently working fine.  Setting up the  dual boot with encrypted volumes was hard enough, lol. I  don't want to  get locked out of booting linux :razz:.

Thank you for the guidance, I will study the links you provided and try it.

---

