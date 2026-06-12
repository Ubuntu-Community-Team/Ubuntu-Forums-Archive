---
title: "Ubuntu 14.04 doesnt boot after installation"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by kuehn.marcel on 2014-04-21
Hi,

I decided to get rid of my dual boot system and do a fresh installation of ubuntu 14.04 only. But somehow I cant get it to boot. I did a UEFI installation, 4 partitions - efi, root, home, swap - and I have secure boot on in my UEFI. Also tried to run boot repair, no success.. What am I doing wrong? Thanks in advance!

Here's the link from boot-repair: [http://paste.ubuntu.com/7303096/](http://paste.ubuntu.com/7303096/)

---

### Post by oldfred on 2014-04-21
Moved to install sub-forum since 14.04 released.

It looks like you originally installed in BIOS boot mode as you have grub installed to protective MBR.

But it now looks like an UEFI boot as the efi partition mount is in fstab.

Not sure what error is.

But since you only have one install you will not get grub menu and may be booting, but having video issues?

I would have secure boot off, but you do show signed versions of kernel installed which should work with secure boot on.

From UEFI/BIOS hold shift key to see if grub menu appears. Some UEFI need escape key instead, so try that.

If you still cannot get to grub, download and try Supergrub.
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

    
What system and what video chip/card do you have?

---

### Post by kuehn.marcel on 2014-04-21
> **oldfred said:**
> Moved to install sub-forum since 14.04 released.

It looks like you originally installed in BIOS boot mode as you have grub installed to protective MBR.

But it now looks like an UEFI boot as the efi partition mount is in fstab.

Not sure what error is.[QUOTE]

I'm pretty sure I booted the live USB in UEFI mode (afaik you can distinguish them by the booting screens?!)

[QUOTE=oldfred;12996952]Moved to install sub-forum since 14.04 released.

But since you only have one install you will not get grub menu and may be booting, but having video issues?

I would have secure boot off, but you do show signed versions of kernel installed which should work with secure boot on.

From UEFI/BIOS hold shift key to see if grub menu appears. Some UEFI need escape key instead, so try that.



Tried that, nothing happened.

> **oldfred said:**
> Moved to install sub-forum since 14.04 released.

If you still cannot get to grub, download and try Supergrub.
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

    
What system and what video chip/card do you have?

Here are some system informations:
```

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
01:00.0 Network controller: Intel Corporation Wireless 7260 (rev 6b)

ubuntu@ubuntu:~$ sudo dmidecode -t0 -t1 
# dmidecode 2.12
# SMBIOS entry point at 0xdbf50498
SMBIOS 2.7 present.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
    Vendor: American Megatrends Inc.
    Version: R1041V7
    Release Date: 11/05/2013
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 4096 kB
    Characteristics:
        PCI is supported
        PNP is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        ESCD support is available
        Boot from CD is supported
        Selectable boot is supported
        BIOS ROM is socketed
        EDD is supported
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        AGP is supported
        Smart battery is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
        UEFI is supported
    BIOS Revision: 10.41
    Firmware Revision: 10.41

Handle 0x0001, DMI type 1, 27 bytes
System Information
    Manufacturer: Sony Corporation
    Product Name: SVP1321L1EBI
    Version: C60C1PHE
    Serial Number: 54594786-0002884
    UUID: 94ADC2E7-017E-4857-A7EB-8182DAE2A4D1
    Wake-up Type: Power Switch
    SKU Number: 54594786
    Family: SVP1321

ubuntu@ubuntu:~$ sudo dmidecode | grep -A3 'BIOS Information' 
BIOS Information
    Vendor: American Megatrends Inc.
    Version: R1041V7
    Release Date: 11/05/2013

```

let me know if you need any further information.

Thanks!

---

### Post by kuehn.marcel on 2014-04-21
Just wanted to let you know that I found a solution. I followed this guide (I actually stopped before "Lear grub to cope with the SSD" because I was getting some errors there):
[http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/](http://steffankarger.nl/2013/12/10/ubuntu-13-10-on-the-sony-vaio-pro-13/)

---

