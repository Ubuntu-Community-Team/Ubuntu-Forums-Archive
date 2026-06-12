---
title: "Kernel panic on  xen-amd64"
date: 2006-11-19
forum: Installation &amp; Upgrades
---

### Post by costinc on 2006-11-19
Hi

On Ubuntu Edgy, having installed following xen packages :
ii  libxen3.0                            3.0.3-0ubuntu1 library interface for Xen, a Virtual Machine
ii  libxen3.0-dev                        3.0.3-0ubuntu1 headers for Xen, a Virtual Machine Monitor
ii  python-xen3.0                        3.0.3-0ubuntu1 python bindings for Xen, a Virtual Machine M
ii  xen-headers-2.6.17-6                 2.6.17-6       Header files related to Linux kernel, specif
ii  xen-headers-2.6.17-6-generic-xen0    2.6.17-6       Linux kernel headers 2.6.17 on xen
ii  xen-hypervisor-3.0-amd64             3.0.3-0ubuntu1 The Xen Hypervisor for amd64
ii  xen-image-xen0-2.6.17-6-generic-xen0 2.6.17-6       Linux xen kernel binary image for version 2.
ii  xen-ioemu-3.0                        3.0.3-0ubuntu1 XEN administrative tools
ii  xen-tools                            2.1-4ubuntu2   Tools to manage debian XEN virtual servers
ii  xen-utils-3.0                        3.0.3-0ubuntu1 XEN administrative tools

cpu: AMD Athlon(tm) 64 Processor 3500+
in menu.lst 
[...........]
title xen-AMD64
root            (hd0,8)
kernel          /boot/xen-3.0-amd64.gz
module          /boot/xen0-linux-2.6.17-6-generic-xen0 root=/dev/hda9
module          /boot/xen0-linux-2.6.17-6-generic-xen0.initrd.img
savedefault
boot
[...........]
xen0-linux-2.6.17-6-generic-xen0.initrd.img was generated using 
mkinitramfs -o /boot/xen0-linux-2.6.17-6-generic-xen0.initrd.img 2.6.17-6-generic-xen0

I got following error messages on boot:


 __  __            _____  ___   _____     ___
 \ \/ /___ _ __   |___ / / _ \ |___ /    / _ \
  \  // _ \ '_ \    |_ \| | | |  |_ \ __| | | |
  /  \  __/ | | |  ___) | |_| | ___) |__| |_| |
 /_/\_\___|_| |_| |____(_)___(_)____/    \___/

 [http://www.cl.cam.ac.uk/netos/xen](http://www.cl.cam.ac.uk/netos/xen)
 University of Cambridge Computer Laboratory

 Xen version 3.0.3-0 (buildd@buildd) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) Thu Oct 19 02:32:20 6 Latest ChangeSet: unavailable

(XEN) Command line: /boot/xen-3.0-amd64.gz com1=115200,8n1
(XEN) Physical RAM map:
(XEN)  0000000000000000 - 000000000009f800 (usable)
(XEN)  000000000009f800 - 00000000000a0000 (reserved)
(XEN)  00000000000f0000 - 0000000000100000 (reserved)
(XEN)  0000000000100000 - 000000001eff0000 (usable)
(XEN)  000000001eff0000 - 000000001eff3000 (ACPI NVS)
(XEN)  000000001eff3000 - 000000001f000000 (ACPI data)
(XEN)  000000001f000000 - 0000000020000000 (reserved)
(XEN)  00000000f0000000 - 00000000f2000000 (reserved)
(XEN)  00000000fec00000 - 0000000100000000 (reserved)
(XEN) System RAM: 495MB (507452kB)
(XEN) Xen heap: 14MB (14468kB)
(XEN) found SMP MP-table at 000f51e0
(XEN) DMI 2.3 present.
(XEN) Using APIC driver default
(XEN) ACPI: RSDP (v000 GBT                                   ) @ 0x00000000000f6b90
(XEN) ACPI: RSDT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x000000001eff3000
(XEN) ACPI: FADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x000000001eff3040
(XEN) ACPI: SSDT (v001 PTLTD  POWERNOW 0x00000001  LTP 0x00000001) @ 0x000000001eff7a40
(XEN) ACPI: MCFG (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x000000001eff7b80
(XEN) ACPI: MADT (v001 GBT    AWRDACPI 0x42302e31 AWRD 0x01010101) @ 0x000000001eff79c0
(XEN) ACPI: DSDT (v001 GBT    AWRDACPI 0x00001000 MSFT 0x0100000c) @ 0x0000000000000000
(XEN) ACPI: Local APIC address 0xfee00000
(XEN) ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
(XEN) Processor #0 15:15 APIC version 16
(XEN) ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
(XEN) ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
(XEN) ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
(XEN) ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
(XEN) IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
(XEN) ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
(XEN) ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
(XEN) ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
(XEN) ACPI: IRQ9 used by override.
(XEN) ACPI: IRQ14 used by override.
(XEN) ACPI: IRQ15 used by override.
(XEN) Enabling APIC mode:  Flat.  Using 1 I/O APICs
(XEN) Using ACPI (MADT) for SMP configuration information
(XEN) Using scheduler: SMP Credit Scheduler (credit)
(XEN) Initializing CPU#0
(XEN) Detected 2210.123 MHz processor.
(XEN) CPU0: AMD Flush Filter disabled
(XEN) CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
(XEN) CPU: L2 Cache: 512K (64 bytes/line)
(XEN) AMD SVM Extension is enabled for cpu 0.
(XEN) Intel machine check architecture supported.
(XEN) Intel machine check reporting enabled on CPU#0.
(XEN) CPU0: AMD Athlon(tm) 64 Processor 3500+ stepping 02
(XEN) Total of 1 processors activated.
(XEN) ENABLING IO-APIC IRQs
(XEN)  -> Using new ACK method
(XEN) ..TIMER: vector=0xF0 apic1=0 pin1=0 apic2=-1 pin2=-1
(XEN) Platform timer is 1.193MHz PIT
(XEN) Brought up 1 CPUs
(XEN) Machine check exception polling timer started.
(XEN) *** LOADING DOMAIN 0 ***
(XEN) Domain 0 kernel supports features = { 0000000f }.
(XEN) Domain 0 kernel requires features = { 00000000 }.
(XEN) PHYSICAL MEMORY ARRANGEMENT:
(XEN)  Dom0 alloc.:   000000001c000000->000000001e000000 (105346 pages to be allocated)
(XEN) VIRTUAL MEMORY ARRANGEMENT:
(XEN)  Loaded kernel: ffffffff80200000->ffffffff8059f008
(XEN)  Init. ramdisk: ffffffff805a0000->ffffffff814fb000
(XEN)  Phys-Mach map: ffffffff814fb000->ffffffff815d8c10
(XEN)  Start info:    ffffffff815d9000->ffffffff815d949c
(XEN)  Page tables:   ffffffff815da000->ffffffff815e9000
(XEN)  Boot stack:    ffffffff815e9000->ffffffff815ea000
(XEN)  TOTAL:         ffffffff80000000->ffffffff81800000
(XEN)  ENTRY ADDRESS: ffffffff80200000
(XEN) Dom0 has maximum 1 VCPUs
(XEN) Initrd len 0xf5b000, start at 0xffffffff805a0000
(XEN) Scrubbing Free RAM: .....done.
(XEN) Xen trace buffers: disabled
(XEN) Xen is relinquishing VGA console.
(XEN) *** Serial input -> DOM0 (type 'CTRL-a' three times to switch input to Xen).
kernel direct mapping tables up to 1c382000 @ 15e9000-16cd000
Bootdata ok (command line is root=/dev/hda9 console=ttyS0,115200)
Linux version 2.6.17-6-generic-xen0 (root@crested) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #3 SMP)BIOS-provided physical RAM map:
 Xen: 0000000000000000 - 000000001c382000 (usable)
DMI 2.3 present.
ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
ACPI: LAPIC (acpi_id[0x01] lapic_id[0x01] disabled)
ACPI: LAPIC_NMI (acpi_id[0x00] dfl dfl lint[0x1])
ACPI: LAPIC_NMI (acpi_id[0x01] dfl dfl lint[0x1])
ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
Setting APIC routing to xen
Using ACPI (MADT) for SMP configuration information
Allocating PCI resources starting at 30000000 (gap: 20000000:d0000000)
Built 1 zonelists
Kernel command line: root=/dev/hda9 console=ttyS0,115200
Initializing CPU#0
PID hash table entries: 2048 (order: 11, 16384 bytes)
Xen reported: 2210.122 MHz processor.
Console: colour VGA+ 80x25
Dentry cache hash table entries: 65536 (order: 7, 524288 bytes)
Inode-cache hash table entries: 32768 (order: 6, 262144 bytes)
Software IO TLB enabled:
 Aperture:     2 megabytes
 Kernel range: 0xffff880001e26000 - 0xffff880002026000
PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
Memory: 421888k/462344k available (2025k kernel code, 31716k reserved, 879k data, 156k init)
Calibrating delay using timer specific routine.. 5530.55 BogoMIPS (lpj=11061107)
Security Framework v1.0.0 initialized
SELinux:  Initializing.
SELinux:  Starting in permissive mode
selinux_register_security:  Registering secondary module capability
Capability LSM initialized as secondary
Mount-cache hash table entries: 256
CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
CPU: L2 Cache: 512K (64 bytes/line)
SMP alternatives: switching to UP code
Freeing SMP alternatives: 20k freed
Unable to handle kernel paging request at ffff880000573020 RIP:
<ffffffff8025fd75>{cache_alloc_refill+836}
PGD 15e9067 PUD 15ea067 PMD 15ed067 PTE 573165
Oops: 0003 [1] SMP
CPU 0
Modules linked in:
Pid: 0, comm: swapper Not tainted 2.6.17-6-generic-xen0 #3
RIP: e030:[<ffffffff8025fd75>] <ffffffff8025fd75>{cache_alloc_refill+836}
RSP: e02b:ffffffff8056dd90  EFLAGS: 00010202
RAX: 0000000000000120 RBX: 0000000000000120 RCX: 0000000000000000
RDX: ffffffffff578000 RSI: 0000000000000001 RDI: 0000000000000028
RBP: ffff880000573000 R08: 0000000000000000 R09: 0000000000019c00
R10: 0000000000000000 R11: 0000000000000000 R12: ffff880000573000
R13: ffff8800016cdf00 R14: 0000000000000000 R15: ffff88001bb81c40
FS:  0000000000000000(0000) GS:ffffffff80556000(0000) knlGS:0000000000000000
CS:  e033 DS: 0000 ES: 0000
Process swapper (pid: 0, threadinfo ffffffff8056c000, task ffffffff8045ffe0)
Stack: 00000000ffffffff 00000040000000d0 000000d000000010 0000000000000001
       0000000000000000 00000000000000d0 ffff8800016cdf00 0000000000000000
       0000000000000000 fffffffffffffff5
Call Trace: <ffffffff8020aad7>{kmem_cache_alloc+105}
       <ffffffff80292116>{alloc_pid+31} <ffffffff8028568c>{vprintk+655}
       <ffffffff80233b0b>{do_fork+50} <ffffffff80574000>{_sinittext+0}
       <ffffffff8028571d>{printk+78} <ffffffff80261425>{kernel_thread+129}
       <ffffffff80268325>{init+0} <ffffffff80261482>{child_rip+0}
       <ffffffff8026869b>{rest_init+23} <ffffffff8057476f>{start_kernel+524}
       <ffffffff8057420d>{_sinittext+525}

Code: c7 45 20 00 00 00 00 66 c7 45 28 00 00 48 89 45 10 49 8d 04
RIP <ffffffff8025fd75>{cache_alloc_refill+836} RSP <ffffffff8056dd90>
CR2: ffff880000573020
 <0>Kernel panic - not syncing: Attempted to kill the idle task!
 (XEN) Domain 0 crashed: rebooting machine in 5 seconds.
(XEN) AMD SVM Extension is disabled.

Any ideea ?

---

