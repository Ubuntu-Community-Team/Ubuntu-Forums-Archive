---
title: "Grub entries after dual boot and boot repair"
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by khaos1 on 2013-01-17
Hello,
I have succesfully installed Ubuntu 12.10 x64 in my new Asus laptop ( with Windows 8 preinstalled. After the boot I can't boot in Windows 8 and I run Boot Repair. Now I can boot in Windows 8 but there are many entries in my grub. I want to clear the unused grub entries with a safe way.

My Grub entries:

Ubuntu -> Boots ok!
Windows 8 (loader) ---> Still gives error
2 Entries for System/Windows Recovery -> I didn't tried them :p
Windows UEFI bootmgfw.efi (/EFI/Microsoft/Boot/bootmgfw.efi) -> Boots Ok
Windows Boot UEFI loader (/EFI/Boot/bootx64.efi) -> Boots Ok But Which of them I must keep and which I must delete?

This is my Boot Repair Output:
[http://paste.ubuntu.com/1538249/](http://paste.ubuntu.com/1538249/)

Thanks in advance ;)

---

### Post by oldfred on 2013-01-17
Boot-Repair added the correct efi chain load entries to 25_custom. Grub2's os-prober has a bug and all its entries will not currently work. You can turn off os-prober.

       Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
#In /etc/default/grub I added this line:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
#or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober


#Then 

sudo update-grub

---

### Post by khaos1 on 2013-01-20
Thanks for your reply. I have turned off and now I have Ubuntu and 2 Windows Entries. Why the grub detected 2 windows loaders?

Windows UEFI bootmgfw.efi (/EFI/Microsoft/Boot/bootmgfw.efi) -> Boots Ok
Windows Boot UEFI loader (/EFI/Boot/bootx64.efi) -> Boots Ok

Are the same ?? (they have some differences in the files that point) And which of the two I must use to login?

---

### Post by oldfred on 2013-01-20
Not sure of exact differences.

Both Windows & Ubuntu have bootx64.efi so I think that must be related to the UEFI shell? Just found reference that says this file is the UEFI shell.

The Windows boot file in BIOS was bootmgr so the Windows efi boot file is  bootmgfw.efi.

I would keep both of those.

---

### Post by khaos1 on 2013-01-20
> **oldfred said:**
> Not sure of exact differences.

Both Windows & Ubuntu have bootx64.efi so I think that must be related to the UEFI shell? Just found reference that says this file is the UEFI shell.

The Windows boot file in BIOS was bootmgr so the Windows efi boot file is  bootmgfw.efi.

I would keep both of those.

Ok thanks both of them boot Windows 8 so I will keep them. Thanks again

---

### Post by YannBuntu on 2013-01-20
Hello

> **khaos1 said:**
> Windows UEFI bootmgfw.efi (/EFI/Microsoft/Boot/bootmgfw.efi) -> Boots Ok
Windows Boot UEFI loader (/EFI/Boot/bootx64.efi) -> Boots Ok

Are the same ??

No difference. You can remove one in your /etc/grub.d/25_custom file if you want.

---

### Post by khaos1 on 2013-01-21
> **YannBuntu said:**
> Hello



No difference. You can remove one in your /etc/grub.d/25_custom file if you want.

Thank you :)

---

### Post by YannBuntu on 2013-01-21
you're welcome :) if your problem is solved, please use the Thread Tools to mark it [SOLVED]

---

