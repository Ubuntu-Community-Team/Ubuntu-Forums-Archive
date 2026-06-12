---
title: "SCSI tape drive troubleshooting"
date: 2007-09-26
forum: Installation &amp; Upgrades
---

### Post by damir123 on 2007-09-26
Hi,

I'm posting this here, hoping it is appropriate forum.


I have a problem with my scsi device on one computer. It has been working normally before server's motherboard failed, after the motherboard has been replaced external tape device stopped working.

Here is the config and symptoms, please direct me to the docs if there are some relevant, i couldn't find anything useful...

The computer is breezy installation on HP 380DL, it will probably be upgraded to gutsy in a few months but it has worked very nice for the past two years. It has HP 488 ultirium II external tape device connected to the external scsi port.

Server has Smart Array 6i controller, and it usess cciss module in linux.

The system boots from raid array connected to this scsi controller. So linux can access hard disk array via scsi, but it doesnt see the tape device? In scsi controllers bios menu tape drive is recognized, so i assume it is working.


> cat /proc/scsi/scsi
Attached devices:

> this is empty, most docs suggest device shoukd be seen here?



>lsmod
ipv6 264000 37
floppy 60564 0
pcspkr 3880 0
tpm_nsc 6912 0
tpm_atmel 5792 0
tpm 10464 2 tpm_nsc,tpm_atmel
hw_random 5588 0
pci_hotplug 28412 0
dm_mod 59232 1
tsdev 8000 0
evdev 9920 0
psmouse 30628 0
mousedev 12132 0
parport_pc 36356 0
lp 12548 0
parport 37384 2 parport_pc,lp
md 47536 0
reiserfs 265712 1
thermal 13320 0
processor 23816 1 thermal
fan 4708 0
usbhid 36096 0
cciss 54052 3
scsi_mod 137896 2 st,cciss
tg3 100388 0
ehci_hcd 35816 0
uhci_hcd 32720 0
usbcore 121308 4 usbhid,ehci_hcd,uhci_hcd
ide_cd 42148 0
cdrom 40096 1 ide_cd
ide_generic 1600 0
piix 10980 1
ide_core 140628 3 ide_cd,ide_generic,piix
unix 29392 100
vesafb 8216 0
capability 4936 0
commoncap 7040 1 capability
vga16fb 12840 1
vgastate 9888 1 vga16fb
softcursor 2496 2 vesafb,vga16fb
cfbimgblt 3168 2 vesafb,vga16fb
cfbfillrect 4096 2 vesafb,vga16fb
cfbcopyarea 4832 2 vesafb,vga16fb
fbcon 38880 71
tileblit 2592 1 fbcon
font 8448 1 fbcon
bitblit 5856 1 fbcon


In /dev/cciss/ folder there is no entry for the tape (it used to be visible under /dev/st0)


Please help or point me to the relevant docs or drivers so i can get the tape drive running again...


Thanks,
Damir
__________________

---

