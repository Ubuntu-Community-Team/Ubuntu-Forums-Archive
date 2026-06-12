---
title: "boot error on fresh install"
date: 2012-01-30
forum: Installation &amp; Upgrades
---

### Post by dark2099 on 2012-01-30
So I installed 11.10 after I installed Win 7, partitioned the HDD in Win (left blank), and Ubuntu automatically selected everything from the side by side option.  Once I restarted and selected Ubuntu from the Grub bootloader, I get a blinking cursor for about 10-15 seconds then the following message pops up:  
```
BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

Unfortunetaly, either due to my wireless keyboard, or another issues, I cannot enter anything in.  Any suggestions.

Thanks

---

### Post by BC59 on 2012-01-30
Pressing ALT+F2 is working?

---

### Post by dark2099 on 2012-01-30
> **BC59 said:**
> Pressing ALT+F2 is working?

Tried the whole time the cursor was blinking, nothing happened.  Should I try it at a different time?

---

### Post by BC59 on 2012-01-30
Try while boot to press SHIFT key after the bios logo to enter grub menu. If you see it press "E" to edit.

---

### Post by BC59 on 2012-01-30
If you reach the edit screen for Grub-Menu, find the line (usually is the 6th) with “quiet splash” in it and convert it to “quiet splash nomodeset”.
Then press CTRL+X to boot again.

---

### Post by dark2099 on 2012-01-30
> **BC59 said:**
> If you reach the edit screen for Grub-Menu, find the line (usually is the 6th) with “quiet splash” in it and convert it to “quiet splash nomodeset”.
Then press CTRL+X to boot again.

The grub menu comes up fine, and I can move between the options just fine, my error happens after I select ubuntu to start from the grub screen.

---

### Post by BC59 on 2012-01-30
When you see the Grub-Menu with the kernel options just press E to enter to the edit menu.

---

### Post by dark2099 on 2012-01-30
I tried doing the recovery mode option from GRUB.  It output the following lines after going through all the boot process, this time though I do have a blinking cursor after the "(initramfs)" but I think my wireless keyboard is not recognized: 

```
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system wait long enough?)
    - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/dbaec13d-e78e-488c-9f54-52bcd540d71b does not exist.
Dropping to shell!

BusyBox v1.18.4 (Ubuntu 1:1.18.4-2ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)
```

Also, tried changing what you said, same results.

---

### Post by BC59 on 2012-01-30
Then try the option:

> quiet splash nomodeset acpi_osi=

and if not the option

> quiet splash nomodeset acpi=off

---

### Post by dark2099 on 2012-01-30
Figured I would post this in here too, when I select "e" from the grub menu to edit the boot parameters, this is what is says:

```
recordfail
set gfxpayload=$linux_gfx_mode
insmod gzio
insmod part_msdos
insmod ext2
set root='(hd3,msdos5)'
search --no-floppy --fs-uuid --set=root bdaec13d-e78e-488c-9f54-52bcd540d71b
linux /boot/vmlinuz-3.0.0-15-generic root=UUID=bdaec13d-e78e-488c-9f54-52bcd540d71b ro  quiet splash vt.handoff=7
initrd /boot/initrd.img-3.0.0-15-generic
```

---

### Post by BC59 on 2012-01-31
You should change
> linux /boot/vmlinuz-3.0.0-15-generic root=UUID=bdaec13d-e78e-488c-9f54-52bcd540d71b ro  quiet splash vt.handoff=7
to
> linux /boot/vmlinuz-3.0.0-15-generic root=UUID=bdaec13d-e78e-488c-9f54-52bcd540d71b ro  quiet splash nomodeset

---

