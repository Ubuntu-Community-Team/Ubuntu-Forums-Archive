---
title: "kernel_thread_helper message in Maverick"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by gamx on 2010-10-14
Hi,
I have upgraded my desktop to Maverick (from Lucid) and I have problems with the kernel. With the standard kernel (2.6.35.22) the booting process gets stuck with a message "kernel_thread-helper +0X0/0x10". Somehow, it seems to be related to acpi and, in fact, if I turn off acpi in grub the system boots. Still, this is a problem in itself, since now the boot process is text only, etc but I can live with that, I guess.
However, I have encountered a second (and worse) problem. Audio does not work properly and all sounds get interrupted (or alternated with other sounds), as if we were trying to play the same sound twice with half a second of delay. It is difficult to explain... I have no idea whether this is due to the kernel or the acpi option I have used.
The only additional piece of information I have is that, fortunately, the upgrade process left behind one of the old 2.6.32-25 kernels. With that kernel everything works perfectly (including acpi). I guess this means that it cannot be a hardware problem or related to other parts of ubuntu. It must be somehow related to the kernel.
Can you help please? Thanks!

My hardware configuration is the following:

sudo lshw -short
H/W path        Device      Class       Description
===================================================
                            system      APL00
/0                          bus         APL00
/0/0                        memory      128KiB BIOS
/0/4                        processor   Pentium(R) Dual-Core  CPU      E5200  @ 2.50G
/0/4/8                      memory      32KiB L1 cache
/0/4/9                      memory      1MiB L2 cache
/0/17                       memory      4GiB System Memory
/0/17/0                     memory      2GiB DIMM DRAM 667 MHz (1.5 ns)
/0/17/1                     memory      2GiB DIMM DRAM 667 MHz (1.5 ns)
/0/100                      bridge      MCP73 Host Bridge
/0/100/0.1                  memory      RAM memory
/0/100/1                    memory      RAM memory
/0/100/1.1                  memory      RAM memory
/0/100/1.2                  memory      RAM memory
/0/100/1.3                  memory      RAM memory
/0/100/1.4                  memory      RAM memory
/0/100/1.5                  memory      RAM memory
/0/100/1.6                  memory      RAM memory
/0/100/2                    memory      RAM memory
/0/100/3                    bridge      MCP73 LPC Bridge
/0/100/3.1                  bus         MCP73 SMBus
/0/100/3.2                  memory      RAM memory
/0/100/3.4                  memory      RAM memory
/0/100/4                    bus         GeForce 7100/nForce 630i USB
/0/100/4.1                  bus         MCP73 [nForce 630i] USB 2.0 Controller (EHCI)
/0/100/8                    storage     MCP73 IDE
/0/100/9                    multimedia  MCP73 High Definition Audio
/0/100/a                    bridge      MCP73 PCI Express bridge
/0/100/a/8                  bus         FW322/323
/0/100/b                    bridge      MCP73 PCI Express bridge
/0/100/b/0                  display     G98 [GeForce 9300 GE]
/0/100/c                    bridge      MCP73 PCI Express bridge
/0/100/d                    bridge      MCP73 PCI Express bridge
/0/100/e        scsi2       storage     GeForce 7100/nForce 630i SATA
/0/100/e/0      /dev/sda    disk        640GB WDC WD6400AAKS-2
/0/100/e/0/1    /dev/sda1   volume      12GiB Windows NTFS volume
/0/100/e/0/2    /dev/sda2   volume      74GiB Windows NTFS volume
/0/100/e/0/3    /dev/sda3   volume      93GiB EXT4 volume
/0/100/e/0/4    /dev/sda4   volume      416GiB Extended partition
/0/100/e/0/4/5  /dev/sda5   volume      3812MiB Linux swap / Solaris partition
/0/100/e/0/4/6  /dev/sda6   volume      412GiB Linux filesystem partition
/0/100/e/1      /dev/cdrom  disk        DVD A  DH16A6S
/0/100/f        eth0        network     MCP73 Ethernet
/0/1            scsi6       storage     
/0/1/0.0.0      /dev/sdb    disk        SCSI Disk
/0/1/0.0.1      /dev/sdc    disk        SCSI Disk
/0/1/0.0.2      /dev/sdd    disk        SCSI Disk
/0/1/0.0.3      /dev/sde    disk        SCSI Disk
/0/2            scsi7       storage     
/0/2/0.0.0      /dev/sdf    disk        32GB SCSI Disk
/0/2/0.0.0/1    /dev/sdf1   volume      29GiB Windows FAT volume
/0/2/0.0.1      /dev/sdg    disk        2032MB SCSI Disk

---

