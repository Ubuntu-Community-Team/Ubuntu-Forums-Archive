---
title: "Dual boot with W8 and 12.10 with UEFI"
date: 2012-12-06
forum: Installation &amp; Upgrades
---

### Post by MichelT on 2012-12-06
Hello,

This tread is the following of #654 at [http://ubuntuforums.org/showthread.php?t=1769482&page=66](http://ubuntuforums.org/showthread.php?t=1769482&page=66)

Trying to install Ubuntu 12.10 beside W8 Pro on a Lenovo X230 with EFI and Secure Boot.

No problem with Ubuntu, but W8 did not start. I used Boot-Repair and I got this boot info here [http://paste.ubuntu.com/1414662/](http://paste.ubuntu.com/1414662/)

Ubuntu start whithout problem, but when I  choose the "Windows UEFI loader" in the boot menu, I got :
     Code:
     /EndEntire file path:  /ACPI(a031d0,0)/PCI(2,1f)/Unknownmessaging(12)/HD(2,1f4800,82000,b3f9756612b95345,bd,d4)/File(\\EFI\Microsoft\Boot)/File(bootmgfw.efi.bkp)/EndEntire error: cannot load image 
Boot-Repair created a second line for Windows in the boot menu :  "Windows Boot UEFI bootx64.efi.bkp" but I got quite the same thing:
     Code:
     /EndEntire file path: /ACPI(a031d0,0)/PCI(2,1f)/Unknownmessaging(12)/HD(2,1f4800,82000,b3f9756612b95345,bd,d4)/File(\\EFI\Boot)/File(bootx64.efi.bkp)/EndEntire error: cannot load image 
Any idea ?

Thanks in advance

---

### Post by YannBuntu on 2012-12-06
Please: run Boot-Repair --> Advanced options --> untick "Backup and rename EFI files" --> tick "Restore EFI backups" --> Apply , indicate the new URL that will appear. Reboot and tell us if the Windows UEFI entry works or not.

---

### Post by MichelT on 2012-12-07
I did what you said but during applying, linux crashed. I got a dump page begining with 
BUG: unable to handle kernel NULL pointer dereference at 00000000000000f8
...

I retried another boot-repair, but the  "Restore EFI backups" option was no more visible, so I canceled.

Despite  this, I tried (with computers,  I sometimes believe in miracles) to  start windows, but it's always the same error message.
Ubuntu is still ok.

I  have a question : in my situation now, do I have to run boot-repair  changes from an usb key sesion or is it possible directly from the hard disk ?
(Previous try and this one were made from usb key)

Here is the last BootInfo [http://paste.ubuntu.com/1416512/](http://paste.ubuntu.com/1416512/)

---

### Post by MichelT on 2012-12-07
I found a workaround. I discovered that in the boot priority order of the setup, there is a "windows boot manager" line. If I put it on the first line, W8 start normaly.
When I put again ubuntu first, the boot menu show normaly ubuntu and windows lines (which still crashe).
But anyway, I have a dual boot possibility even it's a bit special. And it's not very anoying because I'm 95% on ubuntu.

Un grand merci for your help and your work.
But I'm still interested if you have an idea...

---

### Post by oldfred on 2012-12-07
Either bootscript has a bug or efi files are missing from latest BootInfo report???

So both Windows & Ubuntu boot ok directly from UEFI menu. Do you also have a one time boot key? My old BIOS uses f12 to select a boot device just once, but that varies by Vendor and I do not know if UEFI offers that or not.

So the issue is the chain entry from grub to Windows efi entry. Yann will have to comment.

---

### Post by YannBuntu on 2012-12-07
> **oldfred said:**
> Either bootscript has a bug or efi files are missing from latest BootInfo report???

[https://sourceforge.net/apps/trac/bootinfoscript/ticket/16](https://sourceforge.net/apps/trac/bootinfoscript/ticket/16)
EFI files are detected by Boot-Repair (line 648), but not by Bootinfoscript.

> **oldfred said:**
> So the issue is the chain entry from grub to Windows efi entry. Yann will have to comment.

Unfortunately, the UEFI entries look correct, so i don't know why they fail:

```
### BEGIN /etc/grub.d/25_custom ###

menuentry "Windows UEFI loader" {
search --fs-uuid --no-floppy --set=root D400-81BC
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

menuentry "Windows Boot UEFI bootx64.efi" {
search --fs-uuid --no-floppy --set=root D400-81BC
chainloader (${root})/EFI/Boot/bootx64.efi
}
```

---

### Post by oldfred on 2012-12-08
I moved this post from matejuh as I thought he wanted help, but he had the comment of changing BIOS or UEFI entry to boot as a work around.

[http://ubuntuforums.org/showthread.php?t=2092620](http://ubuntuforums.org/showthread.php?t=2092620)

---

### Post by MichelT on 2012-12-09
@oldfred
Yes, my bios has an F12 key to select a boot device just once and it's pretty handy.
Looking the post of matejuh let me think that may be lenovo and dell could have the same bios manufacturer ??
Thanks to all.

---

