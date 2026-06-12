---
title: "Ubuntu 12.10 cannot boot Windows 8"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by ibn5100 on 2013-02-14
I receive an error about an invalid efi file. Here's a boot info log that I picked up in my attempts to fix this issue using boot repair.  My laptop is a Lenovo Ideapad y580.

[http://paste.ubuntu.com/1654176/](http://paste.ubuntu.com/1654176/)


As for how I installed Ubuntu, I just put 12.10 x64 on a bootable DVD and installed from there.

---

### Post by oldfred on 2013-02-14
It looks like Boot-Repair added the correct entries.

```
menuentry "Windows UEFI recovery bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root 58DE-4058
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI recovery" {
search --fs-uuid --no-floppy --set=root 58DE-4058
chainloader (${root})/EFI/Boot/bootx64.efi
}

```grub2's os-prober still has bug and creates BIOS entries that will not work:
> 
'Windows Recovery Environment (loader) (on /dev/sda3)'

'Windows 8 (loader) (on /dev/sda5)'

Other Lenovo's and what they did.
       Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)

---

### Post by ibn5100 on 2013-02-14
I don't quite understand what's going on in those threads.

---

### Post by oldfred on 2013-02-14
When you try to boot Windows with the new entries by Boot-Repair what does happen?

---

