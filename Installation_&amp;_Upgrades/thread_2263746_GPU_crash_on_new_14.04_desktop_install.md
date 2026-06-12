---
title: "GPU crash on new 14.04 desktop install"
date: 2015-02-02
forum: Installation &amp; Upgrades
---

### Post by dbclin2 on 2015-02-02
Hi,
I recently tried to install 14.04 on an old Dell (1GB RAM). The install (from the mini.iso) went fine, but when I tried to boot for the first time the desktop failed to load. I get the same result loading both Unity and Gnome-Classic. I can ssh in and the system itself is fully up and running, there's just no desktop (wallpaper, but no icons).
Here's my syslog output:

> Jan 16 12:49:22 ubuntu blueman-mechanism: Exiting 
Jan 16 12:49:43 ubuntu kernel: [  156.849111] [drm] GPU crash dump saved to /sys/class/drm/card0/error
Jan 16 12:49:43 ubuntu kernel: [  156.849122] [drm] GPU hangs can indicate a bug anywhere in the entire gfx stack, including userspace.
Jan 16 12:49:43 ubuntu kernel: [  156.849125] [drm] Please file a _new_ bug report on bugs.freedesktop.org against DRI -> DRM/Intel
Jan 16 12:49:43 ubuntu kernel: [  156.849128] [drm] drm/i915 developers can then reassign to the right component if it's not a kernel issue.
Jan 16 12:49:43 ubuntu kernel: [  156.849131] [drm] The gpu crash dump is required to analyze gpu hangs, so please always attach it.
Jan 16 12:49:43 ubuntu kernel: [  156.852020] i915: render error detected, EIR: 0x00000010
Jan 16 12:49:43 ubuntu kernel: [  156.852020] [drm:i915_report_and_clear_eir] *ERROR* EIR stuck: 0x00000010, masking
Jan 16 12:49:43 ubuntu kernel: [  156.852020] i915: render error detected, EIR: 0x00000010
Jan 16 12:50:05 ubuntu kernel: [  179.045809] gnome-shell[1991]: segfault at 1 ip 00000001 sp bfdaa17c error 4 in gnome-shell[8048000+3000]
Jan 16 12:50:09 ubuntu kernel: [  182.379511] tracker-miner-f[2110]: segfault at 5 ip b736e48b sp bff739f0 error 6 in libglib-2.0.so.0.4002.0[b730b000+10a000]
Jan 16 12:52:39 ubuntu gnome-session[1894]: WARNING: Application 'gnome-shell-classic.desktop' killed by signal 11
Jan 16 12:53:59 ubuntu kernel: [  413.004026] [drm] stuck on render ring
Jan 16 12:53:59 ubuntu kernel: [  413.004476] [drm:i915_reset] *ERROR* Failed to reset chip.
Jan 16 12:54:01 ubuntu gnome-session[1894]: WARNING: App 'gnome-shell-classic.desktop' exited with code 1
Jan 16 12:54:40 ubuntu gnome-session[1894]: WARNING: App 'gnome-shell-classic.desktop' exited with code 1
Jan 16 12:54:40 ubuntu gnome-session[1894]: WARNING: App 'gnome-shell-classic.desktop' respawning too quickly
Jan 16 12:54:41 ubuntu gnome-session[1894]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Jan 16 12:57:00 ubuntu kernel: [  594.163720] perf samples too long (2529 > 2500), lowering kernel.perf_event_max_sample_rate to 50000

And this, if I remember correctly, is from /usr/lib/i386-linux-gnu/libcogl.so.15

> No symbol table info available.
 #17 0xb63839f0 in cogl_pipeline_set_color () from /usr/lib/i386-linux-gnu/libcogl.so.15
 No symbol table info available.
 #18 0xb6383a90 in cogl_pipeline_set_color4ub () from /usr/lib/i386-linux-gnu/libcogl.so.15
 No symbol table info available.
 #19 0xb638948f in cogl_material_set_color4ub () from /usr/lib/i386-linux-gnu/libcogl.so.15
 No symbol table info available.
 #20 0xb7787908 in st_theme_node_paint () from /usr/lib/gnome-shell/libgnome-shell.so
 No symbol table info available.
 #21 0xb7793fb3 in st_widget_paint_background () from /usr/lib/gnome-shell/libgnome-shell.so
 No symbol table info available.
 #22 0xb776c4d7 in ?? () from /usr/lib/gnome-shell/libgnome-shell.so
 No symbol table info available.
 #23 0xb6ab1709 in g_cclosure_marshal_VOID__VOIDv () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #24 0xb6aae457 in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #25 0xb6aafc3a in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #26 0xb6ac9080 in g_signal_emit_valist () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #27 0xb6ac9bf3 in g_signal_emit () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #28 0xb6cc7415 in clutter_actor_continue_paint () from /usr/lib/i386-linux-gnu/libclutter-1.0.so.0
 No symbol table info available.
 #29 0xb6cce149 in clutter_actor_paint () from /usr/lib/i386-linux-gnu/libclutter-1.0.so.0
 No symbol table info available.
 #30 0xb77604b8 in ?? () from /usr/lib/gnome-shell/libgnome-shell.so
 No symbol table info available.
 #31 0xb6ab1709 in g_cclosure_marshal_VOID__VOIDv () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #32 0xb6aae457 in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #33 0xb6aafc3a in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #34 0xb6ac9080 in g_signal_emit_valist () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #35 0xb6ac9bf3 in g_signal_emit () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #36 0xb6cc7415 in clutter_actor_continue_paint () from /usr/lib/i386-linux-gnu/libclutter-1.0.so.0
 No symbol table info available.
 #37 0xb6cce149 in clutter_actor_paint () from /usr/lib/i386-linux-gnu/libclutter-1.0.so.0
 No symbol table info available.
 #38 0xb69d9558 in g_list_foreach () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #39 0xb6d5af92 in ?? () from /usr/lib/i386-linux-gnu/libclutter-1.0.so.0
 No symbol table info available.
 #40 0xb6ab1709 in g_cclosure_marshal_VOID__VOIDv () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #41 0xb6aae457 in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #42 0xb6aafcce in ?? () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #43 0xb6ac9080 in g_signal_emit_valist () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #44 0xb6ac9bf3 in g_signal_emit () from /usr/lib/i386-linux-gnu/libgobject-2.0.so.0
 No symbol table info available.
 #45 0xb6cc7415 in clutter_actor_continue_paint () from /usr/lib/i386-linux-gnu/libclutter-1.0.so.0
 No symbol table info available.
 #46 0xb6cce149 in clutter_actor_paint () from /usr/lib/i386-linux-gnu/libclutter-1.0.so.0
 No symbol table info available.
 #47 0xb6d2ce72 in ?? () from /usr/lib/i386-linux-gnu/libclutter-1.0.so.0
 No symbol table info available.
 #48 0xb6cbc9b1 in ?? () from /usr/lib/i386-linux-gnu/libclutter-1.0.so.0
 No symbol table info available.
 #49 0xb6d2f0b0 in ?? () from /usr/lib/i386-linux-gnu/libclutter-1.0.so.0
 No symbol table info available.
 #50 0xb6d2b335 in ?? () from /usr/lib/i386-linux-gnu/libclutter-1.0.so.0
 No symbol table info available.
 #51 0xb6d0eb8a in ?? () from /usr/lib/i386-linux-gnu/libclutter-1.0.so.0
 No symbol table info available.
 #52 0xb69dd1e3 in g_main_context_dispatch () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #53 0xb69dd468 in ?? () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #54 0xb69dd76b in g_main_loop_run () from /lib/i386-linux-gnu/libglib-2.0.so.0
 No symbol table info available.
 #55 0xb7378855 in meta_run () from /usr/lib/libmutter.so.0
 No symbol table info available.
 #56 0x08049746 in ?? ()
 No symbol table info available.
 #57 0xb67dca83 in __libc_start_main (main=0x80493b0, argc=2, argv=0xbfdab8d4, init=0x8049ce0, fini=0x8049d50, rtld_fini=0xb77e3180 <_dl_fini>, stack_end=0xbfdab8cc) at libc-start.c:287
         result = <optimized out>
         unwind_buf = {cancel_jmp_buf = {{jmp_buf = {-1231626240, 0, 0, 0, 1799723629, 631348862}, mask_was_saved = 0}}, priv = {pad = {0x0, 0x0, 0x2, 0x804982f}, data = {prev = 0x0, cleanup = 0x0, canceltype = 2}}}
         not_first_call = <optimized out>
 #58 0x08049850 in ?? ()
 No symbol table info available.
Title: gnome-shell crashed with SIGSEGV
UpgradeStatus: No upgrade log present (probably fresh install)
_MarkForUpload: True



Any ideas?
Thanks

---

### Post by mörgæs on 2015-02-03
Please use CODE and not QUOTE tags for terminal output.

Would be nice if you run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by dbclin2 on 2015-02-04
Thanks. 
I haven't actually booted this machine for a couple of weeks (it's been sitting in a corner collecting dust), so when I booted it this morning, it got a bit further. This time, using Gnome Classic, I got the Applications and Places menus on top, but no mouse. There were also some menu items missing: System Tools and System Settings had no sub menu items to the right. 
Memory does seem to be an issue: 
```
$ free -h
             total       used       free     shared    buffers     cached
Mem:          1.0G       927M        73M        98M        47M       437M
-/+ buffers/cache:       442M       558M
Swap:         1.0G       116K       1.0G

```
But there should be some way to run 14.04 with 1GB of RAM, shouldn't there?

Here's the lshw output:
```
computer
    description: Desktop Computer
    product: Dimension 2350
    vendor: Dell Computer Corporation
    version: A00
    serial: [REMOVED]
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3 smp-1.4 smp
    configuration: boot=normal chassis=desktop cpus=1 uuid=[REMOVED]
  *-core
       description: Motherboard
       vendor: Dell Computer Corporation
       physical id: 0
     *-firmware
          description: BIOS
          physical id: 1
          version: A00
          date: 10/28/2002
          size: 128KiB
          capacity: 192KiB
          capabilities: pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Pentium(R) 4 CPU 1.80GHz
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 15.2.7
          slot: Socket 478
          size: 1800MHz
          capacity: 2800MHz
          width: 32 bits
          clock: 400MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid
          configuration: id=0
        *-cache:0
             description: L1 cache
             physical id: 9
             slot: Internal Cache
             size: 8KiB
             capacity: 8KiB
             capabilities: synchronous internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: a
             slot: External Cache
             size: 512KiB
             capacity: 512KiB
             capabilities: synchronous external write-back unified
     *-memory
          description: System Memory
          physical id: 20
          slot: System board or motherboard
          size: 1GiB
          capacity: 2GiB
        *-bank:0
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             product: None
             vendor: None
             physical id: 0
             serial: [REMOVED]
             slot: A0
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM SDRAM Synchronous 266 MHz (3.8 ns)
             product: None
             vendor: None
             physical id: 1
             serial: [REMOVED]
             slot: A1
             size: 512MiB
             width: 64 bits
             clock: 266MHz (3.8ns)
     *-pci
          description: Host bridge
          product: 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 03
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0 memory:e8000000-ebffffff
        *-display
             description: VGA compatible controller
             product: 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e0000000-e7ffffff memory:ee000000-ee07ffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:d800(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:d000(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:d400(size=32)
        *-usb:3
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:23 memory:ee080000-ee0803ff
        *-pci
             description: PCI bridge
             product: 82801 PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 82
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:c000(size=4096) memory:ec000000-edffffff memory:40000000-400fffff
           *-communication
                description: Modem
                product: BCM4212 v.90 56k modem
                vendor: Broadcom Corporation
                physical id: 4
                bus info: pci@0000:01:04.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pm generic bus_master cap_list
                configuration: driver=serial latency=32
                resources: irq:16 memory:ed002000-ed002fff ioport:c000(size=16)
           *-network
                description: Ethernet interface
                product: BCM4401 100Base-T
                vendor: Broadcom Corporation
                physical id: 9
                bus info: pci@0000:01:09.0
                logical name: eth0
                version: 01
                serial: [REMOVED]
                size: 100Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list rom ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=[REMOVED] latency=32 link=yes multicast=yes port=twisted pair speed=100Mbit/s
                resources: irq:17 memory:ed000000-ed001fff memory:40000000-40003fff
        *-isa
             description: ISA bridge
             product: 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801DB (ICH4) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:f000(size=16) memory:40100000-401003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:500(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:17 ioport:e000(size=256) ioport:e400(size=64) memory:ee081000-ee0811ff memory:ee082000-ee0820ff
     *-scsi:0
          physical id: 0
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1600AAJB-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: 01.0
             serial: [REMOVED]
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000cfb88
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: [REMOVED]
                size: 148GiB
                capacity: 148GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-01-16 09:40:35 filesystem=ext4 lastmountpoint=/ modified=2015-02-04 09:30:48 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-02-04 09:30:49 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 1021MiB
                capacity: 1021MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1021MiB
                   capabilities: nofs
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD-RAM writer
             product: DVD-RAM GH22NP20
             vendor: HL-DT-ST
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/sr0
             version: 1.04
             capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
             configuration: ansiversion=5 status=nodisc
```

Any ideas?
Thanks!

---

### Post by dbclin2 on 2015-02-04
Update: I think it was a memory problem. I booted again using the Xfce desktop and everything seemed to work (even if it was a bit slow). 
The mouse problem was actually a hardware issue: one of the USB ports seems to be dead.
Thanks,

---

### Post by mörgæs on 2015-02-04
Good, but this is very old stuff so maybe Lubuntu is faster.
The Intel graphics processor sometimes is better off with some tweaks. See the link in my signature for details.

---

### Post by dbclin2 on 2015-02-04
That's a good idea. This machine will probably only be used for a short while until its owner becomes familiar with Ubuntu in general and feels comfortable moving it up to his regular PC. Now I've got it running (along with the files I rescued from his XP partition before I blew it away), It's not worth starting over.
Thanks,

---

