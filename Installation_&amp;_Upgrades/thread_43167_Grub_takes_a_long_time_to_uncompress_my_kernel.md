---
title: "Grub takes a long time to uncompress my kernel"
date: 2005-06-21
forum: Installation &amp; Upgrades
---

### Post by steven_ellis on 2005-06-21
Now I've had this problem since I performed my initial install of Ubuntu, and i've tried changing both kernels and initrds without fixing things. Also note that I still have my old RH9 and win98 installs on the box and they boot very quickly.


Ok the details
[list=1]
[*]Machine powers on to Bios
[*]Bios inits Promise oboard IDE raid controller in ide mode
[*]Grub selection screen
[*]Select Ubuntu
[*]Grub finds kernel and initrd
[*]Wait 2-3 minutes for kernel to actually load
[*]Normal Linux boot process proceedes on screen after this 2 minute wait.
[*]Machine boots and ubuntu runs fine
[/list]

So some details on my hw

[list=1]
[*]5 Hard drives, two for Linux install (hda/b), remaining on Promise controller for video editing (hde,g,h)
[*]Pioneer DVD driver on hdc
[*]AMD Athlon 2800+ CPU
[*]2x512MB DDR 400 RAM
[*]Gigabyte 7vaxp Motherboard
[/list]

And the patitions
[list=1]
[*]hda1 - Existing Windows 98 partition
[*]hda2 - Swap
[*]hdb1 - Swap
[*]md2 - Raid 1 /boot (hda3 + hdb2) - ext3
[*]md3 - Raid 1 /        (hda5 + hdb5) - ext3
[*]md4 - Raid 1 /home (hda6 + hdb6) - ext3
[*]hdb7 - Old RH9 install - ext3
[*]hdh1 - /video - ext3
[*]md0 - Raid 0 /video/capture (hde1 + hdg1) - reiserfs
[*]md1 - Raid 0 /video/capture1 (hde2+ hdg2) - reiserfs
[/list]

So I'd decided to go Raid 1 with my code ubuntu setup and I already had a couple of Raid0 partitions I use for video editing. With my current configuration I can boot Win98 to check driver hardware issues (about once a year), RH9 for my old video toolset, and ubuntu.

Ubuntu and RH9 only share the video related partitions.

Now as I mentioned the boot of both RH9 and Win98 are very quick, no delays in finding the OS and initing the kernel. With Ubuntu Grub takes atleast 2 minutes to properly init the kernel.

So here is the offending grub config file

```
default         0
timeout         10
color cyan/blue white/blue

title           Ubuntu, kernel 2.6.10-5-k7 Custom init
root            (hd1,1)
kernel          /vmlinuz-2.6.10-5-k7 root=/dev/md3 ro quiet splash
initrd          /initrd.img-2.6.10-5-k7.new2
boot

title           Ubuntu, kernel 2.6.10-5-k7
root            (hd1,1)
kernel          /vmlinuz-2.6.10-5-k7 root=/dev/md3 ro quiet splash
initrd          /initrd.img-2.6.10-5-k7
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-k7 (recovery mode)
root            (hd1,1)
kernel          /vmlinuz-2.6.10-5-k7 root=/dev/md3 ro single
initrd          /initrd.img-2.6.10-5-k7
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386
root            (hd1,1)
kernel          /vmlinuz-2.6.10-5-386 root=/dev/md3 ro quiet splash
initrd          /initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd1,1)
kernel          /vmlinuz-2.6.10-5-386 root=/dev/md3 ro single
initrd          /initrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd1,1)
kernel          /memtest86+.bin
savedefault
boot

title           Other operating systems:
root

title           RH9 single
root            (hd1,6)
kernel          /boot/vmlinuz-2.4.26 root=/dev/hdb7 ro single
initrd          /boot/initrd-2.4.26.img

title           RH9 full
root            (hd1,6)
kernel          /boot/vmlinuz-2.4.26 root=/dev/hdb7 ro
initrd          /boot/initrd-2.4.26.img

title           Windows 95/98/Me
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

Note that I have also tried with a root of (hd0,3) to use the /boot area on hda3, but this made no difference with my timings.

Now any tips on what is going on, or how I can debug the grub process. Really miss my previously quick boot times.

---

### Post by blind0wl on 2005-06-21
If your used to seeing linux boot, you'll notice that Ubuntu doesnt show the initial kernel boot up sequence....if you want to see that process, edit your grub.conf with no quiet option of your kernel boot line, ie:

```

title           Ubuntu, kernel 2.6.10-5-k7 Custom init
root            (hd1,1)
kernel          /vmlinuz-2.6.10-5-k7 root=/dev/md3 ro splash
initrd          /initrd.img-2.6.10-5-k7.new2
boot

```

You'll see why it takes so long to get to the module loading screen  :smile: 

Cheers

Blindy

---

### Post by steven_ellis on 2005-06-22
Just tried removing quiet from the grub settings.

My machine still just sits there for about 2 minutes, and then the kernel kicks in and the machine boots fine. No change time wise or in terms of feedback during the boot process.

Any other ideas?

---

### Post by blind0wl on 2005-06-22
Did you notice any issues during the kernel running?  An output of dmesg would be good, otherwise its strange that its just sitting there.  Is the hard drive light actually doing anything?

---

### Post by steven_ellis on 2005-06-23
Ok i'll check on the HD light on next re-boot, meanwhile the start of dmesg is as follows

```
nk [ALKC] (IRQs 22) *0, disabled.
ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
Linux Plug and Play Support v0.97 (c) Adam Belay
pnp: PnP ACPI init
pnp: PnP ACPI: found 12 devices
PnPBIOS: Disabled by ACPI PNP
PCI: Using ACPI for IRQ routing
** PCI interrupts are no longer routed automatically.  If this
** causes a device to stop working, it is probably because the
** driver failed to call pci_enable_device().  As a temporary
** workaround, the "pci=routeirq" argument restores the old
** behavior.  If this argument makes the device work again,
** please email the output of "lspci" to bjorn.helgaas@hp.com
** so I can fix the driver.
audit: initializing netlink socket (disabled)
audit(1119517262.589:0): initialized
highmem bounce pool size: 64 pages
VFS: Disk quotas dquot_6.5.1
Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
devfs: 2004-01-31 Richard Gooch (rgooch@atnf.csiro.au)
devfs: boot_options: 0x0
Initializing Cryptographic API
isapnp: Scanning for PnP cards...
isapnp: No Plug & Play device found
serio: i8042 AUX port at 0x60,0x64 irq 12
serio: i8042 KBD port at 0x60,0x64 irq 1
Serial: 8250/16550 driver $Revision: 1.90 $ 48 ports, IRQ sharing enabled
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
io scheduler noop registered
io scheduler anticipatory registered
io scheduler deadline registered
io scheduler cfq registered
RAMDISK driver initialized: 16 RAM disks of 8192K size 1024 blocksize
input: AT Translated Set 2 keyboard on isa0060/serio0
NET: Registered protocol family 2
IP: routing cache hash table of 8192 buckets, 64Kbytes
TCP: Hash tables configured (established 262144 bind 65536)
NET: Registered protocol family 8
NET: Registered protocol family 20
Restarting tasks...<6> Strange, kswapd0 not stopped
 Strange, kseriod not stopped
 done
ACPI wakeup devices:
PCI0 USB0 USB1 USB2 USB6 USB7 USB8 USB9 UAR1 LPT1
ACPI: (supports S0 S1 S4 S5)
RAMDISK: cramfs filesystem found at block 0
RAMDISK: Loading 1632KiB [1 disk] into ram disk... /
one.
VFS: Mounted root (cramfs filesystem) readonly.
Freeing unused kernel memory: 164k freed
ACPI: Processor [CPU0] (supports 2 throttling states)
``` 

But I took a look at my kern.log around the reboot time and the top data might supply some extra clues

[HTML]Jun 23 08:58:19 localhost kernel: apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
Jun 23 08:58:19 localhost kernel: apm: disabled on user request.
Jun 23 08:58:23 localhost kernel: Kernel logging (proc) stopped.
Jun 23 08:58:23 localhost kernel: Kernel log daemon terminating.
Jun 23 09:06:49 localhost kernel: Inspecting /boot/System.map-2.6.10-5-k7
Jun 23 09:06:49 localhost kernel: Loaded 26825 symbols from /boot/System.map-2.6.10-5-k7.
Jun 23 09:06:49 localhost kernel: Symbols match kernel version 2.6.10.
Jun 23 09:06:49 localhost kernel: No module symbols loaded - kernel modules not enabled.
Jun 23 09:06:49 localhost kernel:  Root Bridge [PCI0] (00:00)
Jun 23 09:06:49 localhost kernel: PCI: Probing PCI hardware (bus 00)
Jun 23 09:06:49 localhost kernel: PCI: Via IRQ fixup
Jun 23 09:06:49 localhost kernel: ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
Jun 23 09:06:49 localhost kernel: ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 *5 6 7 10 11 12 14 15)
Jun 23 09:06:49 localhost kernel: ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
Jun 23 09:06:49 localhost kernel: ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 *10 11 12 14 15)
Jun 23 09:06:49 localhost kernel: ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 10 *11 12 14 15)
Jun 23 09:06:49 localhost kernel: ACPI: PCI Interrupt Link [ALKA] (IRQs 20) *0, disabled.
Jun 23 09:06:49 localhost kernel: ACPI: PCI Interrupt Link [ALKB] (IRQs 21) *0, disabled.
Jun 23 09:06:49 localhost kernel: ACPI: PCI Interrupt Link [ALKC] (IRQs 22) *0, disabled.
Jun 23 09:06:49 localhost kernel: ACPI: PCI Interrupt Link [ALKD] (IRQs 23) *0, disabled.
Jun 23 09:06:49 localhost kernel: Linux Plug and Play Support v0.97 (c) Adam Belay
Jun 23 09:06:49 localhost kernel: pnp: PnP ACPI init
Jun 23 09:06:49 localhost kernel: pnp: PnP ACPI: found 12 devices
Jun 23 09:06:49 localhost kernel: PnPBIOS: Disabled by ACPI PNP[/HTML] 

Now I did a reboot at 8:58, and it was 9:06 before anything came up in the logs. My bios portion of the reboot is about 30 seconds, and I selected the kernel immediately.


Steve

---

### Post by steven_ellis on 2005-06-23
Well i'm going to continue this discussion in the following thread [http://ubuntuforums.org/showthread.php?t=25281](http://ubuntuforums.org/showthread.php?t=25281)  as it looks like i've got a very similar problem

---

