---
title: "Grub2 Boot Windows directly"
date: 2016-06-20
forum: Installation &amp; Upgrades
---

### Post by masfur on 2016-06-20
Good morning.
I have installed Ubuntu 16.04 on my pc. There is a tri-boot with Win8.1 and Win10.
In the grub menu, I have two options: Ubuntu and Windows Boot Manager.
When I click on WIndows Boot Manager, after I could choose Win8.1 or Win10.
There is a way to set grub menu for boot Windows directly from single partition?
Thanks.

---

### Post by grahammechanical on 2016-06-20
> In the grub menu, I have two options: Ubuntu and Windows Boot Manager.

Are you sure that is the Grub boot menu and not the UEFI utility? Load Ubuntu and run this command and watch the printout,

```
sudo update-grub
```

The printout will list all the operating systems detected and that will be listed in the Grub boot menu. It should include 2 boot loaders for Windows. One each for Windows 8 & Windows 10.

Did you install Ubuntu in EFI mode or BIOS/Legacy/CSM mode? 

Regards.

---

### Post by oldfred on 2016-06-20
Many UEFI systems will not work with two ESP - efi system partitions:

 Dual boot two Windows UEFI from grub, two efi partitions.
[http://askubuntu.com/questions/653101/boot-repair-windows-not-listed](http://askubuntu.com/questions/653101/boot-repair-windows-not-listed)

---

### Post by masfur on 2016-06-20
> Are you sure that is the Grub boot menu and not the UEFI utility?
Yes I'm sure. Ubuntu is the last OS that I installed, and I know the grub menu.
Now I try with a new file in grub.d directory with "chainloader+1" option.
Thanks to all for your replies.

---

