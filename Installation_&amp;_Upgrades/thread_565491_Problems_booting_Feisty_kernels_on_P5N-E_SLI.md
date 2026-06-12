---
title: "Problems booting Feisty kernels on P5N-E SLI"
date: 2007-10-02
forum: Installation &amp; Upgrades
---

### Post by Craig Prevallet on 2007-10-02
Hi, 

I just installed a new P5N-E SLI motherboard in my PC.  I've reinstalled Edgy from CD to the second partition of my IDE drive.  I then upgraded to Feisty (via the internet).  I retained the old kernel (2.6.17-10-generic #2 SMP) which boots fine from grub.

The problem is that I can't seem to boot *any* Feisty kernel (I've tried both the 32 and 64 bit versions).  After selecting on of these kernels from grub, I get a message "Starting Up" and then it hangs.  I can't get past this.

I've tried passing a zillion different parameters to the kernel but nothing seems to work (but I'm ready for any advice).  I'm running the lastest version of the Phoenix BIOS (703).  I've seen other posts indicating success with this MB and Feisty kernel which makes me wonder what I've done wrong.

Here's /boot/grub/menu.lst:

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		2

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e167384e-7e61-49c2-b8a2-7fa727531032 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e167384e-7e61-49c2-b8a2-7fa727531032 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=e167384e-7e61-49c2-b8a2-7fa727531032 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e167384e-7e61-49c2-b8a2-7fa727531032 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=e167384e-7e61-49c2-b8a2-7fa727531032 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=e167384e-7e61-49c2-b8a2-7fa727531032 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=e167384e-7e61-49c2-b8a2-7fa727531032 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Here's /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=e167384e-7e61-49c2-b8a2-7fa727531032 /               ext3    defaults,error
s=remount-ro 0       1
# /dev/hda1
UUID=ae2cdc51-0c4c-487e-b2ea-a4092250c20e /media/hda1     ext3    defaults
  0       2
# /dev/hda4
UUID=467A-56F7  /media/hda4     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda3
UUID=4db06c19-8694-44ef-8ae2-749a74308c89 none            swap    sw
  0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

And here's lspci from within 2.6.17:

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [40] HyperTransport: Host or Secondary Interface

00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:02.1 RAM memory: nVidia Corporation Unknown device 03bc (rev a1)
        Flags: bus master, 66MHz, fast devsel, latency 0

00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
        Flags: 66MHz, fast devsel

00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fdf00000-fdffffff
        Prefetchable memory behind bridge: 00000000fde00000-00000000fdefffff
        Capabilities: [40] Subsystem: nVidia Corporation Unknown device 0c55
        Capabilities: [48] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+
        Capabilities: [60] HyperTransport: MSI Mapping
        Capabilities: [80] Express Root Port (Slot+) IRQ 0
        Capabilities: [100] Virtual Channel

00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81bc
        Flags: bus master, 66MHz, fast devsel, latency 0
        Capabilities: [44] HyperTransport: Slave or Primary Interface
        Capabilities: [e0] HyperTransport: MSI Mapping

00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81bc
        Flags: bus master, 66MHz, fast devsel, latency 0

00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81bc
        Flags: 66MHz, fast devsel, IRQ 10
        I/O ports at 1c00 [size=64]
        I/O ports at 1c80 [size=64]
        Capabilities: [44] Power Management version 2

00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81bc
        Flags: 66MHz, fast devsel

00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81bc
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        Memory at fe02f000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2

00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81bc
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        Memory at fe02e000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [44] Debug port
        Capabilities: [80] Power Management version 2

00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1) (prog-if 8a [Master SecP PriP])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81bc
        Flags: bus master, 66MHz, fast devsel, latency 0
        I/O ports at fd00 [size=16]
        Capabilities: [44] Power Management version 2

00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81bc
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 217
        I/O ports at 09f0 [size=8]
        I/O ports at 0bf0 [size=4]
        I/O ports at 0970 [size=8]
        I/O ports at 0b70 [size=4]
        I/O ports at f800 [size=16]
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1) (prog-if 85 [Master SecO PriO])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81bc
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 185
        I/O ports at 09e0 [size=8]
        I/O ports at 0be0 [size=4]
        I/O ports at 0960 [size=8]
        I/O ports at 0b60 [size=4]
        I/O ports at f300 [size=16]
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: [44] Power Management version 2
        Capabilities: [b0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/2 Enable-
        Capabilities: [cc] HyperTransport: MSI Mapping

00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
        Flags: bus master, 66MHz, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=03, sec-latency=128
        I/O behind bridge: 0000d000-0000efff
        Memory behind bridge: fc000000-fd7fffff
        Prefetchable memory behind bridge: fa000000-fbffffff
        Capabilities: [b8] Subsystem: nVidia Corporation Unknown device cb84
        Capabilities: [8c] HyperTransport: MSI Mapping

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8249
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 193
        Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: [44] Power Management version 2
        Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
        Capabilities: [6c] HyperTransport: MSI Mapping

00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8221
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 201
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at f200 [size=8]
        Capabilities: [44] Power Management version 2

01:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02) (prog-if 01 [AHCI 1.0])
        Subsystem: ASUSTeK Computer Inc. Unknown device 8208
        Flags: bus master, fast devsel, latency 0, IRQ 209
        I/O ports at cf00 [size=8]
        I/O ports at ce00 [size=4]
        I/O ports at cd00 [size=8]
        I/O ports at cc00 [size=4]
        I/O ports at cb00 [size=16]
        Memory at fdffe000 (32-bit, non-prefetchable) [size=8K]
        Capabilities: [68] Power Management version 2
        Capabilities: [50] Express Legacy Endpoint IRQ 1

02:06.0 PCI bridge: Hint Corp HB6 Universal PCI-PCI bridge (non-transparent mode) (rev 12) (prog-if 00 [Normal decode])
        Flags: bus master, medium devsel, latency 32
        Bus: primary=02, secondary=03, subordinate=03, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fc000000-fcffffff
        Prefetchable memory behind bridge: 00000000fa000000-00000000fbffffff
        Capabilities: [80] Power Management version 2
        Capabilities: [90] #06 [0000]
        Capabilities: [a0] Vital Product Data

02:08.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81fe
        Flags: bus master, medium devsel, latency 32, IRQ 225
        Memory at fd7ff000 (32-bit, non-prefetchable) [size=2K]
        I/O ports at ef00 [size=128]
        Capabilities: [50] Power Management version 2

03:00.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 82) (prog-if 00 [VGA])
        Subsystem: Matrox Graphics, Inc. Millennium G450 Dual Head PCI
        Flags: bus master, medium devsel, latency 32, IRQ 10
        Memory at fa000000 (32-bit, prefetchable) [size=32M]
        Memory at fcffc000 (32-bit, non-prefetchable) [size=16K]
        Memory at fc000000 (32-bit, non-prefetchable) [size=8M]
        Expansion ROM at fcfc0000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 2
        Capabilities: [f0] AGP version 2.0

Any help would be most appreciated!

---

### Post by Craig Prevallet on 2007-10-02
Was a kernel bug in 2.6.20 -- upgraded to Gutsy and can now boot.

---

