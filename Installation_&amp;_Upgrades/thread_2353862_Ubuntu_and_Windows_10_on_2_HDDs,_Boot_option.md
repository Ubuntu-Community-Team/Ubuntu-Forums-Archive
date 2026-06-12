---
title: "Ubuntu and Windows 10 on 2 HDDs, Boot option?"
date: 2017-02-25
forum: Installation &amp; Upgrades
---

### Post by DB4711 on 2017-02-25
Hello,

on my new Laptop I installed on my first HDD Ubuntu in UEFI mode. Then Windows 10 on my second HDD also in UEFI mode. I can now start my computer and slect via BIOS what to boot. But is there any chance to geht automatically a boot menu on startup where I can choose what to boot? I am not sure if this is an BIOS feature or deals with the EFI partition on both HDDs...

Thanks for your help!

---

### Post by oldfred on 2017-02-25
I do not think UEFI auto presents a boot menu, you have to use the boot menu key.

But if Windows fast start up is off, you can boot Windows from grub menu.

---

### Post by Bashing-om on 2017-02-25
DB4711; Hey ...

While to Windows there is no other operating system in the world ; ubuntu will happily boot up windows .

Boot the ubuntu install and in terminal execute
```

sudo update-grub

```
this will chainload Windows to ubuntu's boot loading ; now when you boot the ubuntu drive you should have the option to select windows also .


[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by DB4711 on 2017-02-25
Guys... thank you very much for your help! I'll try that as soon as I am again in Linux World :)

---

