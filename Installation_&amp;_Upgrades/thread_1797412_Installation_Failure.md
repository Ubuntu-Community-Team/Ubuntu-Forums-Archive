---
title: "Installation Failure"
date: 2011-07-05
forum: Installation &amp; Upgrades
---

### Post by ecbw on 2011-07-05
First attempt to install Ubuntu, not going well so far.  

Booting from a 11.04 CD hangs.  I tried 10.04, same result.  The following list of error messages is from 10.04:

panic
forget_original_parent
exit_notify
do_exit
print_oops_end_marker
oops_end
no_context
__bad_area_nosemaphore
bad_area_nosemaphore
do_page_fault
do_page_fault
error_code+0x73/0x80
check_pcibios
pci_mmcfg_check_hostbridge
cmp_mmcfg
pci_pcbios_init
__pci_mmcfg_init
pci_arch_init
do_one_initcall
pci_arch_init
do_basic_setup
kernel_init
kernel_init
kernel_thread_helper

This is what I've tried so far:
1. Booting the CD on another machine, worked ok, so assume CD is fine.
2. Tried all of the various boot options from the menu (eg. acpi=off, etc).  Same error.
3. Memory test was ok.
4. Check Disc for defects - This results in the same error as above.  It's not clear to me whether this is checking the CD or the HDD, but both should be ok.  As mentioned, the CD boots in a different machine.  The HDD was usable in windows, so I believe it's ok.
5. I was originally attempting to install dual boot with a pre-existing win7 partition, but I've removed that HDD and swapped in a different one with no existing partitions.  Same error.

Hardware (all new except HDD):

CPU: AMD Phenom II X4 955 
MB: MSI 890GXM-G65 Chipset AMD® 890GX+SB850 USB 3.0 SATA 6GB/s
Graphics:  Integrated ATI Radeon HD4290 GPU
Memory: 2 X G.SKILL PC3-12800 2GB DDR3-1600 CL9-9-9-24 Core i5 1.5V
HDD: Maxtor DiamondMax Plus 9 200 GB ATA/133
USB mouse and keyboard

I was able to install and run Win7 on the above hardware.

I'd appreciate any suggestions as to what to try next to either make it work, or narrow down why it's not working.

thanks,
Ed

---

### Post by mikkboss23 on 2011-07-05
hello

---

### Post by mastablasta on 2011-07-05
title should be boot failure.
 
 
can you try to boot from USB key? 
 
hard disk has nothing to do with live system boot. you should be able to boot even without the hard disk. could it be that CD drive is faulty?

---

### Post by ecbw on 2011-07-20
For what it's worth to anyone else having this problem, here's the follow up...

Tried Ubuntu USB install, which also hung, but in a different way (syslinux copyright message, then hung at command prompt).

Then I tried using unetbootin to create the USB install stick, which got me back to the original boot hang.

The advantage of the USB drive is that it's much easier to try different installations.  I tried a few older versions of Ubuntu (same result), then the latest 64 for bit version, which worked!

---

