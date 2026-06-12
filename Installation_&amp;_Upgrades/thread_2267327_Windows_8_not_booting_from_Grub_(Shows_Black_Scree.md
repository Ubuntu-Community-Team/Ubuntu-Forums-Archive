---
title: "Windows 8 not booting from Grub (Shows Black Screen)"
date: 2015-02-28
forum: Installation &amp; Upgrades
---

### Post by andre39 on 2015-02-28
So I've recently installed the latest version of Ubuntu on my computer (as a dual boot) which loads fine from the Grub interface.
However, the rest of the Windows 8 options don't happen to load at all, upon selecting them and hitting enter, the windows 8 Logo appears, but then I just get a black screen that never disappears. I've run boot repair, with this being the result of the link created: p**aste.ubuntu.com/10478671**

The options which are windows related on my Grub are: 
[B]Windows UEFI bkpbootmgfw.efi
Windows Boot UEFI loader
Windows Boot Manager (on /dev/sda2) (this used to work)[/B]
I'm completely stumped on what else to do, any help would be much appreciated.

---

### Post by Bucky Ball on 2015-02-28
Welcome. Did you install Ubuntu in UEFI mode also? If Win is installed in UEFI, Ubuntu must be, too.

Just checking your boot repair output, you have these in the EFI partition:
```

/EFI/ubuntu/MokManager.efi /EFI/ubuntu/grubx64.efi 
/EFI/ubuntu/shimx64.efi
```

So looks like Ubuntu was installed in EFI.

---

### Post by oldfred on 2015-02-28
Old versions of Boot-Repair renamed the Windows efi file. That was because then grub would not find the Windows entry to boot in BIOS mode and it was a work around for many systems where vendors modify UEFI to only boot Windows.
If you have this file it probably is the original Windows boot file.
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

But bootmgfw.efi is what UEFI and now grub2 find to boot. But if renamed it really is then grub?

Also it says you left Windows hibernated. Grub cannot boot Windows if hibernated.
And then you have to boot it directly from UEFI.

 If you have previous used Boot-Repair and it reported this: "Buggy" UEFI (At least some HP & Sony) and you have this menu entry:
        menuentry "Windows UEFI bkpbootmgfw.efi" {
        With rename you cannot boot Windows directly from UEFI, but only the renamed file from grub menu.
    Best to undo this rename with Boot-Repair or manually and usually better to use other rename options.
    If unsure of which file is orginal Windows boot file - Windows UEFI install should  have backup of bootmgfw.efi here:
    C:\Windows\Boot\EFI\bootmgfw.efi from a working Windows x86_64 installation.

---

