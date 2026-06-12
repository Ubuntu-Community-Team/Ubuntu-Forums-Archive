---
title: "Xen on a AMD64 X2 CPU"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by frspin on 2006-11-11
I have installed Xen on my new Asus M2NPV-VM MB using AMD Athlon 64 X2 CPU a Nvidia Chipset.

According to CPU spec and xm dmesg command my cpu is supporting SVM.

Dom0 is booting ok but, when I work for installing WinXP I get some problems.

If I use acpi=0 and apic=0 (default values) I am no able to format (from XP install) my partition.

If I use acpi=1 and apic=1 I am able to format my partition and copy files on it. When XP reboot I get a black screen and XP installation don't procede.
Same result if I use acpi=0 and apic=1

If I use acpio=1 and apic=0 DomU crash whith:

```
(XEN) sh error: sh_page_fault__shadow_2_guest_2(): disabled-APIC access: not sup
ported
(XEN) .domain_crash called from multi.c:3129

```

xm dmesg produce this log:

```
(XEN) (GUEST: 4) HVM Loader
(XEN) (GUEST: 4) Detected Xen v3.0.3-0
(XEN) (GUEST: 4) Writing SMBIOS tables ...
(XEN) (GUEST: 4) Loading ROMBIOS ...
(XEN) (GUEST: 4) Creating MP tables ...
(XEN) (GUEST: 4) Loading Cirrus VGABIOS ...
(XEN) (GUEST: 4) Loading ACPI ...
(XEN) (GUEST: 4) SVM go ...
(XEN) (GUEST: 4)  rombios.c,v 1.138 2005/05/07 15:55:26 vruppert Exp $
(XEN) (GUEST: 4) VGABios $Id: vgabios.c,v 1.61 2005/05/24 16:50:50 vruppert Exp 
$
(XEN) (GUEST: 4) HVMAssist BIOS, 1 cpu, $Revision: 1.138 $ $Date: 2005/05/07 15:
55:26 $
(XEN) (GUEST: 4) 
(XEN) (GUEST: 4) ata0-0: PCHS=8322/16/63 translation=lba LCHS=522/255/63
(XEN) (GUEST: 4) ata0 master: QEMU HARDDISK ATA-7 Hard-Disk (4096 MBytes)
(XEN) (GUEST: 4) ata0  slave: Unknown device
(XEN) (GUEST: 4) ata1 master: QEMU CD-ROM ATAPI-4 CD-Rom/DVD-Rom
(XEN) (GUEST: 4) ata1  slave: Unknown device
(XEN) (GUEST: 4) 
(XEN) (GUEST: 4) Booting from CD-Rom...
(XEN) (GUEST: 4) unsupported PCI BIOS function 0x0E
(XEN) (GUEST: 4) int13_harddisk: function 15, unmapped device for ELDL=81
(XEN) (GUEST: 4) *** int 15h function AX=E980, BX=00F2 not yet supported!
(XEN) hvm_vioapic_write_indirect: version register read only
(XEN) hvm_vioapic_write_indirect: version register read only
(XEN) hvm_vioapic_write_indirect: version register read only
(XEN) This hvm_vlapic is for P4, no work for De-assert init

```

My config file have:

```
# -*- mode: python; -*-
#============================================================================
# Python configuration setup for 'xm create'.
# This script sets the parameters used when a domain is created using 'xm create'. 
# You use a separate script for each domain you want to create, or
# you can set the parameters for the domain on the xm command line.
#============================================================================
import os, re
arch = os.uname()[4]
if re.search('64', arch):
    arch_libdir = 'lib64'
else:
    arch_libdir = 'lib'
#----------------------------------------------------------------------------
kernel = "/usr/lib/xen-ioemu-3.0/boot/hvmloader"
builder='hvm'
memory = 256
name = "winXP"
vif = [ 'type=ioemu, bridge=xenbr0' ]
netmask = "255.255.255.0"
ip = "192.168.0.139"
disk = [ 'file:/home/spin/xp.img,ioemu:hda,w' , 'phy:/dev/hdd,hdc:cdrom,r' ]
device_model = '/usr/' + arch_libdir + '/xen-ioemu-3.0/bin/qemu-dm'
boot="d"
sdl=1
vnc=0
acpi=1
apic=1
```

Is this my MB too new and unsupported in current XEN?

Regards

Franco

---

### Post by pikelner on 2006-11-17
Does your motherboard have an option in the BIOS to enable virtualization? On our Intel motherboard we had to do this to enable the hardware Hypervisor to run Windows.

[email]pikelner@rogers.com[/email]

---

### Post by frspin on 2006-11-18
No, no BIOS option for enabling virtualiation.
Running xm dmesg I get virtualization as enabled.

On a different machine, based on a Asus MB with Intel chipset and a Core 2 Duo CPU I have a BIOS option and Xen is correctly running in this Intel machine.

On my AMD CPU, at format & copy end, I have a correct ntfs disk image. I can mount it and see some files created by XP install.

If I boot directly this image file (boot="c") boot start and, after 2 screen resize, CPU usage is 0% and I see a blank screen.

This is same also with FC6 and Xen from FC6 repository.

Regards
Franco

---

### Post by proteusguy on 2006-12-09
I'm running into the exact same issue with same dmesg results. Got an AMD64 X2 running on a Gigabyte GA-M57SLI-S4 motherboard. I'm wondering if the note about the hvm_vlapic emulation being for the P4 is the hint of our trouble. Has anyone found a work around for this problem yet? I actually bought this machine specifically so I could take advantage of AMD's virtualization support and run Windows under my linux environment. :(

---

