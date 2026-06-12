---
title: "pendrive multiboot UEFI ? MBR? how to tell when system running?"
date: 2016-09-16
forum: Installation &amp; Upgrades
---

### Post by vidtek on 2016-09-16
I have a multiboot pendrive partitioned with GPT and (I thought) set up to only boot EFI.  It will boot to an efi system, but when choosing one item from the menu it then goes off into a submenu which looks suspiciously like a legacy boot menu to me.

Is there a command I can give or a utility available which tells you definitively how a system which is now actually up and running booted in the first place, EFI or legacy?

I have googled until I'm blue in the face, read and re-read the documentation on UEFI and grub2 and even asked oldfred on here, but I haven't found anything which comes close.  I surely can't be the only wally who has come across this?

---

### Post by sudodus on 2016-09-16
See [FromUSBStick#UEFI](https://help.ubuntu.com/community/Installation/FromUSBStick#UEFI)

Use this command line (you can copy and paste it)

```
test -d /sys/firmware/efi && echo efi || echo bios
```

You can make live and persistent live pendrives, that boot in both UEFI and BIOS mode depending on the [settings of] the boot system of the computer. See the following links

[One pendrive for all PC (Intel/AMD) computers](http://ubuntuforums.org/showthread.php?t=2259682)

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[Portable installed system booting from UEFI & BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by howefield on 2016-09-16
Another useful link for you.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by vidtek on 2016-09-16
Thanks to you, I thought there must be something out there.  I don't know how I missed this.
Cheers, Tony.

---

### Post by vidtek on 2016-09-16
Thanks to you too, sometimes I just feel an old numpty

Tony

---

### Post by sudodus on 2016-09-16
There is nothing wrong with asking questions. It is often the easiest way to learn something new, and we are here to help :-)

Please let us know, which mode (UEFI or BIOS) you found, and, if you feel that this problem is solved, click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by vidtek on 2016-09-16
Seems it was EFI all along, weird though how the menu looked legacy-like.

Thanks to you both, Tony

---

### Post by sudodus on 2016-09-16
Once booted in UEFI mode, you can start other (and originally non-UEFI) systems via the grub menu.

But those systems might not (will probably not) run with secure boot, because they might lack a signed kernel and maybe also some other bits and pieces for secure boot.

---

