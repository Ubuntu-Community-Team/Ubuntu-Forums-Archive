---
title: "kernel boots OK w/passed params but not by lilo!"
date: 2006-04-17
forum: Installation &amp; Upgrades
---

### Post by johnpipe on 2006-04-17
Hi, I'm still troubleshooting a boot problem with the breezy kernel; I've compared all the kernel boot files with those on my son-in-law's computer and they check out same with 'diff'.  I've made some progress:

When I boot ubuntu breezy from lilo, ubuntu boots with the 2.6.10-5 kernel (breezy had upgrade error which didn't install the 2.6.12 kernel which I installed manually), which works OK. Trying to boot the breezy kernel (2.6.12-10) won't work correctly from lilo, as the kernel tries to boot root for /dev/hda9, which is redhat6.1, instead of /dev/hdb9, ubuntu. However, I can get ubuntu booted with 2.6.12 if I pass the parameter from the boot prompt:

ub2612 root=/dev/hdb9

However, I do find some kind of error (only pasting part of it), here is what happens during boot for the newer kernel ("[xxxxxxx.xxxxxx]" type errors on ANY boot of the newer kernel, straight from lilo or with passed boot paramter) :

johnpipe@linus:~$ dmesg | more
[4294667.296000] Linux version 2.6.12-10-386 (buildd@terranova) (gcc version 3.4.5 20050809 (prerelease) (Ubuntu 3.4.4-6ubuntu8.1)) #1 Sat Mar 11 16:13:17 UTC 2006
[4294667.296000] BIOS-provided physical RAM map:
[4294667.296000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[4294667.296000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[4294667.296000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[4294667.296000]  BIOS-e820: 0000000000100000 - 0000000010000000 (usable)
[4294667.296000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[4294667.296000] 0MB HIGHMEM available.
[4294667.296000] 256MB LOWMEM available.
[4294667.296000] On node 0 totalpages: 65536
[4294667.296000]   DMA zone: 4096 pages, LIFO batch:1
[4294667.296000]   Normal zone: 61440 pages, LIFO batch:31
[4294667.296000]   HighMem zone: 0 pages, LIFO batch:1
[4294667.296000] DMI 2.2 present.
[4294667.296000] ACPI: Unable to locate RSDP
[4294667.296000] Allocating PCI resources starting at 10000000 (gap: 10000000:efff0000)
[4294667.296000] Built 1 zonelists
[4294667.296000] Kernel command line: BOOT_IMAGE=ub2612 ro root=349 root=/dev/hdb9
[4294667.296000] No local APIC present or hardware disabled
--More--

When trying to boot by selecting the ub2612 without passing root, it tries to boot /dev/hda9.

Here is the pertinent part of lilo.conf, which lives on /dev/hda9, the bootable partition, where it's managed under redhat:

boot=/dev/hda
map=/boot/map
install=/boot/boot.b
prompt
timeout=50
default=linux

image=/boot/vmlinuz-2.2.24-7
        label=linux
        read-only
        root=/dev/hda9
        append="hdc=ide-scsi hdd=ide-scsi"

image=/lilo/ubuntu/boot/vmlinuz-2.6.10-5-386
        label=ubuntu
        initrd=/lilo/ubuntu/boot/initrd.img-2.6.10-5-386
        read-only
        root=/dev/hdb9
        append=irqpoll



#       Kernel problem -disable until fixed 6 Apr 2006
#       Trying again; re-installed w/'No' to prompts.
image=/lilo/ubuntu/boot/vmlinuz-2.6.12-10-386
        label=ub2612
        initrd=/lilo/ubuntu/boot/initrd.img-2.6.12-10-386
        read-only
        root=/dev/hdb9
#       append=irqpoll  # Should (MAY) not need for 12-10


Anyone know what may be causing the errors, and why the new kernel won't pick up the correct root from lilo? 

Thanks, Johnpipe

---

### Post by ranf on 2006-04-20
Don't you need to run `lilo' every time you changed something in lilo.conf?
(long time ago that I last used it)

---

### Post by johnpipe on 2006-04-20
[QUOTE=ranf]Don't you need to run `lilo' every time you changed something in lilo.conf?
(long time ago that I last used it)[/QUOTE]

Yes, it's done every time I update lilo, it is not the problem; wish I knew more about kernel issues and booting.  Everything else works just fine from lilo.

Thanks for your concern,

Johnpipe

---

