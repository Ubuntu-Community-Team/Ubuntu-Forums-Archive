---
title: "How to create PciRoot UEFI boot entry?"
date: 2017-10-24
forum: Installation &amp; Upgrades
---

### Post by Amunhateb on 2017-10-24
Hi. Could someone plz help me understand how to create entries in EFI boot manager with PciRoot format instead of format started with HD(...
As you can see Ubuntu after installation creates two entries:
```
Boot0001* Ubuntu    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,0,0)/HD(4,GPT,43ac8691-7b16-4ee1-b04c-d808d26fb0c3,0x6a0e800,0x32000)/File(\EFI\ubuntu\grubx64.efi)RC
Boot0002* ubuntu    HD(4,GPT,43ac8691-7b16-4ee1-b04c-d808d26fb0c3,0x6a0e800,0x32000)/File(\EFI\ubuntu\shimx64.efi)
```
When I manually creating a boot entry using efibootmgr. E.g. like that:
```
sudo efibootmgr -c -d /dev/sda -p 4 -L "UEFI Generic Boot" -l "\EFI\BOOT\BOOTX64.EFI"
```
I see:
```
Boot0004* UEFI Generic Boot    HD(4,GPT,43ac8691-7b16-4ee1-b04c-d808d26fb0c3,0x6a0e800,0x32000)/File(\EFI\BOOT\BOOTX64.EFI)
```
But I want to be able to create entries based on PciRoot. Can anybody help me achieve this..

---

### Post by oldfred on 2017-10-24
It looks like those type of entries are either from Windows or UEFI shell.
Have not seen much recent use of UEFI shell.

More info on UEFI Shell:
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)
But see note:
> Try bcfg only if efibootmgr fails to create working boot entries on your system.

---

### Post by Amunhateb on 2017-10-25
Yes. I see now, pciroot entries could be created with bcfg. But ubuntu installer does this without bcfg. I wonder how.

---

### Post by oldfred on 2017-10-25
Yours is the first ubuntu entry I have seen with PciRoot entry. 
And I have seen a lot of Boot-Repair summary reports. Have seen other types of entries, but assume they may be defaults created by UEFI itself.

What brand/model system? It may have to do with what UEFI you have?

---

### Post by Amunhateb on 2017-10-25
I have lenovo b550 aio system.

---

### Post by oldfred on 2017-10-25
Have not seem many Lenovo's Boot-Repair summary reports recently, so not much to compare to.

Do you have entries that work from efibootmgr?
Or do you just prefer a different type of entry that we do not know as much about?

---

