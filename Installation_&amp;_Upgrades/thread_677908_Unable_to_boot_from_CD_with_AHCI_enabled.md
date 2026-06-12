---
title: "Unable to boot from CD with AHCI enabled"
date: 2008-01-25
forum: Installation &amp; Upgrades
---

### Post by Meson on 2008-01-25
I've got a Dell PC and when I leave AHCI enabled in the BIOS, it won't boot from the CD properly.

Well, actually the CD boots just fine, but when I select the first option on the CD - to load the livecd, it errors halfway through saying it can't find the filesystem.

This is not a problem with AHCI turned off, but I want it on.

Is AHCI not supported?  Is there a boot option to support it?

---

### Post by jeffus_il on 2008-01-25
I think this is your problem:
> **Common problems switching to AHCI under Linux**[LIST]
[*]AHCI controller does not work on AMD/ATI RS400-200 and RS480 HBA when [MSI]("http://en.wikipedia.org/wiki/Message_Signaled_Interrupts") is enabled due to a hardware error. In order for AHCI to work users must provide the "pci=nomsi" kernel boot parameter. With MSI disabled in this way, the PCIe bus can only act as a faster PCI bus with hotplug capabilities. This is also true of the Nvidia nForce 560 chipset.
[*]AHCI controller on AMD/ATI SB600 HBA can't do 64bit DMA transfers. 64-bit addressing is optional in AHCI 1.1 and the chip claims it can do them, but in reality it can't, so it is disabled. After that it will be forced to do 32bit DMA transfers. Thus DMA transfers will occur at the lower 4GB region of the memory, and bounce buffers must be used sometimes if there is more than 4GB of RAM.[/LIST]taken from:
[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface#Common_problems_switching_to_AHCI_under_Linux](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface#Common_problems_switching_to_AHCI_under_Linux)
Do you know how to boot with "pci=nomsi" ?

---

### Post by Meson on 2008-01-25
Yeah I came across that, but what would PCI have to do with my hard disk and cdrom drive?

---

### Post by jeffus_il on 2008-01-25
Interrupts.

---

### Post by Meson on 2008-01-25
Well it didn't work, here is what it says (and said before I tried pci=nomsi as well):

```
Loading, please wait...
[   52.782835] ata2.00: failed to set xfermode (err_mask=0x1)
[   67.830732] ata2: COMRESET failed (errno=-16)
[   68.687544] ata2.00: failed to set xfermode (err_mask=0x1)


BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [   83.735616] ata2: COMRESET failed (errno=-16)
[   84.592435] ata2.00: failed to set xfermode (err_mask=0x1)
```

This problem also doesn't seem to be specific to ubuntu.  I've tried to boot from Knoppix, Kubuntu-8.04alpha3, and PC Linux OS 2007.  I'm not sure about the error messages they gave, but they all sent me to a similar very limited shell...

---

### Post by Septh on 2008-01-25
hmmmm I got those errors when booting without ahci turned on, tbh you might as well leave it off unless you want it for a particular feature

---

### Post by Meson on 2008-01-25
Well, it's a pain to change it every time...

---

### Post by sml on 2008-02-02
Same problem for me. No luck troubleshooting so I can't really help trying to pinpoint the problem unfortunately.

---

### Post by matthewn on 2008-02-04
Same problem here. On boot, a Gutsy CD just arrives at a BusyBox prompt on my Dell Dimension 9200C.

If I switch the SATA controller's mode to ATA (instead of AHCI) then I can boot a Gutsy CD, but that makes Vista (preinstalled on this machine) unable to boot, so that's not really an option, as I need to dual-boot.

Does anyone have any ideas/workarounds?

---

