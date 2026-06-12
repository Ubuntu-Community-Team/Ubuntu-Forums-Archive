---
title: "No Root file system"
date: 2009-02-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MickeA59 on 2009-02-25
AFter yesterdays update , when booting system cant find root files ?? // Fully functional kubuntu , updated every day before
Any tips what to do ?? //Mikael

---

### Post by OliW on 2009-02-25
There was a grub update yesterday... You might do well to check your grub's menu.lst is pointing at the right devices and that your fstab is set up correctly.

---

### Post by deepclutch on 2009-02-25
seems uuid thingy is messed up.

---

### Post by plun on 2009-02-25
I think we have a severe breakage, also discussed within the nVidia thread.

Maybe its the Hal update.

udev is nevertheless left unconfigured and the root file system cannot be mounted.

We need more clues.   -RC6 boots for me but not Ubuntus kernel.

---

### Post by yelo3 on 2009-02-25
No. I had the same problem of you and I fixed it regenerating the initrd files.
You must have a boot cd or usb key.

you should mount your root filesystem in the following way:
sudo mkdir /recovery
sudo mount /dev/sda??? /recovery
sudo mount -t proc none /recovery/proc
sudo mount -o bind /dev /recovery/dev
sudo chroot /recovery
update-initramfs -u -k all

and now reboot

---

### Post by yelo3 on 2009-02-25
(Anyway now I've lost both the mouse and the keyboard and I don't know how to re-enable them!)

---

### Post by OliW on 2009-02-25
Christ. Well I'm not rebooting for as long as possible!

---

### Post by MickeA59 on 2009-02-25
And yes , they KB and mouse are not responding as well 
Guess il have to do a complete re-installation :(//Mikael

---

### Post by yelo3 on 2009-02-25
Well, it's better to try to dist-upgrade since alpha 5 is released. at least we can hope to obtain a fix

---

### Post by RaZoR1394 on 2009-02-25
Same problem here. I'm stuck in CLI. No root filesystem, the marker is blinking but  keyboard and mouse have no power and don't work. Luckily I burnt out the 20090224 DVD yesterday. Connecting to both the USB hub and directly to the motherboard gives the same result.

There is something about a BIOS firmware bug.

I attached a photo I made with my cell.

---

### Post by RaZoR1394 on 2009-02-25
Old kernel boots up for me. X doesn't work because I haven't installed the nvidia driver for that kernel yet.

---

### Post by RaZoR1394 on 2009-02-25
The latest updates makes the latest kernel work.

---

### Post by plun on 2009-02-25
> **RaZoR1394 said:**
> The latest updates makes the latest kernel work.

Yup, boots just fine but my soundcards are still missing....

---

### Post by yelo3 on 2009-02-25
I managed to fix my problem: I had to remove initramfs-tools, then reinstall ubuntu-desktop and linux-image-2.6.28-8-generic. Now it works for me!

---

### Post by Gourgi on 2009-02-26
> **RaZoR1394 said:**
> Same problem here. I'm stuck in CLI. No root filesystem, the marker is blinking but  keyboard and mouse have no power and don't work. Luckily I burnt out the 20090224 DVD yesterday. Connecting to both the USB hub and directly to the motherboard gives the same result.

There is something about a BIOS firmware bug.

I attached a photo I made with my cell.

i've faced the same 'bug' warning recently.
i had to enable qool'n'quiet from my bios settings.
i hope it helps you with this.

/offtopic who the hell are the "[COLOR="Red"]Linux ACPI maintainers[/COLOR]" ???" i asked over #ubuntu-kernel , noone anwered that. i;ve search google for hours, nothing usefull came up :(

---

### Post by RaZoR1394 on 2009-02-26
No idea about ACPI maintainer either...


Disabling K8 powernow probably is the correct workaround for now.

> 
razor1394@leonis:~$ dmesg | grep ACPI
[    0.000000]  BIOS-e820: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000]  modified: 000000007fee0000 - 000000007fee3000 (ACPI NVS)
[    0.000000]  modified: 000000007fee3000 - 000000007fef0000 (ACPI data)
[    0.000000] ACPI: RSDP 000F8160, 0014 (r0 Nvidia)
[    0.000000] ACPI: RSDT 7FEE3040, 0030 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: FACP 7FEE30C0, 0074 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: DSDT 7FEE3180, 6027 (r1 NVIDIA AWRDACPI     1000 MSFT  100000E)
[    0.000000] ACPI: FACS 7FEE0000, 0040
[    0.000000] ACPI: MCFG 7FEE92C0, 003C (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: APIC 7FEE9200, 0072 (r1 Nvidia AWRDACPI 42302E31 AWRD        0)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] Nvidia board detected. Ignoring ACPI timer override.
[    0.000000] ACPI: PM-Timer IO Port: 0x1008
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[    0.000000] ACPI: LAPIC_NMI (acpi_id[0x01] high edge lint[0x1])
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] ACPI: IRQ14 used by override.
[    0.000000] ACPI: IRQ15 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.021551] ACPI: Core revision 20080926
[    0.023543] ACPI: Checking initramfs for custom DSDT
[    0.384333] ACPI: bus type pci registered
[    0.388801] ACPI: EC: Look up EC in DSDT
[    0.395232] ACPI: Interpreter enabled
[    0.395235] ACPI: (supports S0 S1 S3 S4 S5)
[    0.395253] ACPI: Using IOAPIC for interrupt routing
[    0.400774] ACPI: No dock devices found.
[    0.400774] ACPI: PCI Root Bridge [PCI0] (0000:00)
[    0.400930] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.401181] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[    0.452116] ACPI: PCI Interrupt Link [LNK1] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.452257] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.452398] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 *4 5 7 9 10 11 12 14 15)
[    0.452538] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.452678] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.452819] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 *4 5 7 9 10 11 12 14 15)
[    0.452958] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.453100] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.453240] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.453380] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.453527] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 5 7 9 10 *11 12 14 15)
[    0.453670] ACPI: PCI Interrupt Link [LUB2] (IRQs *3 4 5 7 9 10 11 12 14 15)
[    0.453810] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.453968] ACPI: PCI Interrupt Link [LSID] (IRQs 3 4 5 7 9 *10 11 12 14 15)
[    0.454116] ACPI: PCI Interrupt Link [LFID] (IRQs 3 4 *5 7 9 10 11 12 14 15)
[    0.454262] ACPI: PCI Interrupt Link [LPCA] (IRQs 3 4 5 7 9 10 11 12 14 15) *0, disabled.
[    0.454419] ACPI: PCI Interrupt Link [APC1] (IRQs 16) *0
[    0.454571] ACPI: PCI Interrupt Link [APC2] (IRQs 17) *0
[    0.454723] ACPI: PCI Interrupt Link [APC3] (IRQs 18) *0
[    0.454876] ACPI: PCI Interrupt Link [APC4] (IRQs 19) *0
[    0.454975] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[    0.455132] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22 23) *0
[    0.455290] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22 23) *0, disabled.
[    0.455448] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22 23) *0
[    0.455604] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22 23) *0
[    0.455761] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22 23) *0, disabled.
[    0.455919] ACPI: PCI Interrupt Link [APCS] (IRQs 20 21 22 23) *0
[    0.456094] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22 23) *0
[    0.456251] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22 23) *0, disabled.
[    0.456415] ACPI: PCI Interrupt Link [APSI] (IRQs 20 21 22 23) *0
[    0.456579] ACPI: PCI Interrupt Link [APSJ] (IRQs 20 21 22 23) *0
[    0.456743] ACPI: PCI Interrupt Link [APCP] (IRQs 20 21 22 23) *0, disabled.
[    0.456791] ACPI: WMI: Mapper loaded
[    0.456791] PCI: Using ACPI for IRQ routing
[    0.472006] pnp: PnP ACPI init
[    0.472011] ACPI: bus type pnp registered
[    0.476029] pnp: PnP ACPI: found 10 devices
[    0.476029] ACPI: ACPI bus type pnp unregistered
[    0.476029] PnPBIOS: Disabled by ACPI PNP
[    9.037436] ACPI: Power Button (FF) [PWRF]
[    9.037501] ACPI: Power Button (CM) [PWRB]
[    9.037610] ACPI: Fan [FAN] (on)
[    9.038103] processor ACPI_CPU:00: registered as cooling_device1
[    9.038158] processor ACPI_CPU:01: registered as cooling_device2
[    9.041679] ACPI: Thermal Zone [THRM] (40 C)
[    9.404988] ACPI: PCI Interrupt Link [APC1] enabled at IRQ 16
[   14.029234] ACPI: PCI Interrupt Link [APSI] enabled at IRQ 23
[   15.920475] ACPI: PCI Interrupt Link [APSJ] enabled at IRQ 22
[   17.787074] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[   17.787149] [Firmware Bug]: powernow-k8: Your BIOS does not provide ACPI _PSS objects in a way that Linux understands. Please report this to the Linux ACPI maintainers and complain to your BIOS vendor.
[   17.958392] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 21
[   18.018585] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[   18.020176] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   18.029563] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 23
[   18.031675] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[   18.195963] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[   25.083820] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 22


---

### Post by MickeA59 on 2009-02-28
> **yelo3 said:**
> No. I had the same problem of you and I fixed it regenerating the initrd files.
You must have a boot cd or usb key.

you should mount your root filesystem in the following way:
sudo mkdir /recovery
sudo mount /dev/sda??? /recovery
sudo mount -t proc none /recovery/proc
sudo mount -o bind /dev /recovery/dev
sudo chroot /recovery
update-initramfs -u -k all

and now reboot

Worked like a charm // Thank you

---

