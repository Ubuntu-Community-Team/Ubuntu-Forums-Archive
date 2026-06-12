---
title: "Won't install from USB"
date: 2014-12-04
forum: Installation &amp; Upgrades
---

### Post by Blakeo on 2014-12-04
Hi guys, I have a custom built windows 7-64bit system.
I have downloaded 14.04 Ubuntu 64-bit onto a 8gb usb. It is bootable using a program called:"Pendrive Linux".
The USB does work, I have tried it on another 64-bit system. It however doesn't work on this system running a gigabyte z77 board + amd 280x graphics card.
The steps I take: 
1) Turn off computer 
2) Insert usb into a usb2 slot (have also tried 3 just in case)
3) start up computer and press f key to select bootable devices
4) selected: "UEFI: Lexar drive 8gb"
5) Computer starts to read usb drive (red light flickers) and then blackscreens
6) Light on usb goes out but computer is on, but black screened

Can anyone help me please?
Thank you.

---

### Post by ajgreeny on 2014-12-04
Windows 7 is not normally installed with a UEFI system but using lagacy BIOS, even if the motherboard is UEFI capable.

Check how Windows is installed, and go into the BIOS/UEFI screen at bootup to see how it is set at present.  I suspect it is not set to UEFI.

---

### Post by Blakeo on 2014-12-04
> **ajgreeny said:**
> Windows 7 is not normally installed with a UEFI system but using lagacy BIOS, even if the motherboard is UEFI capable.

Check how Windows is installed, and go into the BIOS/UEFI screen at bootup to see how it is set at present.  I suspect it is not set to UEFI.
Ok it says it is using UEFI mode.

---

### Post by ajgreeny on 2014-12-04
OK, look at the Boot-Repair link in my signature and see if running that helps.  Copy the pastebin link back here for us to look at the report.

---

### Post by amenex on 2014-12-04
My system is a Dell Inspiron 1545 with 4GB RAM with a similar problem, but with more to look at.

I made a bootable 32GB USB stick and installed Ubuntu 14.04.1 on it using Universal USB Installer.
Then I edited the BIOS to make a suitable boot order (USB first, then CD/DVD, then floppy, last HDD.

On bootup, I select MemTest, which runs OK (I'm familiar with MemTest from long, long ago).

If I select "Try Ubuntu" I get the following text on screen, followed by no more activity:
(This was OCR'ed from a picture of the screen ... I proofread and corrected it)

    1.097440]    [<ffffffff810bf78e>]    handle_irq_event_percpu+0x3e/0x1d0
    1.097488]    [<ffffffff810bf95d>]    handle_irq_event+0x3d/0x60
    1.097535]    [<ffffffff810c2347>]    handle edge_irq+0x77/0x130
    1.097582]    [<ffffffff81015cde>]    handle_irq+0x1e/0x30
    1.097629]    [<ffffffff8172e98d>]    do_IRQ+0x4d/0xc0
    1.097676]    [<ffffffff8172412d>]    common_interrupt+0x6d/0x6d
    1.097723]    [<ffffffff8109d883>]    ? account_system_time+0x93/0x170
    1.097771]    [<ffffffff8106caa0>]    ? _do_softirq+0x90/0x2c0
    1.097819]    [<ffffffff8106cc45>]    ? _do_softirq+0x235/0x2c0
    1.097866]    [<ffffffff8106d045>]    irq_exit+0x105/0x110
    1.097913]    [<ffffffff8172ea45>]    smp_apic_timer_interrupt+0x45/0x60
    1.097962]    [<ffffffff8172d3dd>]    apic_timer_interrupt+0x6d/0x80
    1.098008]    <EOI> [<ffffffff81714f80>] ? panic+0x193/0x1d7
    1.098112]    [<ffffffff817159d6>] ? printk+0x67/0x69
    1.098159]    [<ffffffff81d3646a>]    mount_block_root+0x225/0x2b0
    1.098206]    [<ffffffff81d36692>]    mount_root+0x53/0x56
    1.098252]    [<ffffffff81d36801>]    prepare_namespace+0x16c/0x1a4
    1.098300]    [<ffffffff81d3616e>]    kernel_init_freeable+0x1f3/0x200
    1.098347]    [<ffffffff81d358e5>]    ? do_early_param+0x88/0x88
    1.098394]    [<ffffffff8170a190>]    ? rest_init+0x80/0x80
    1.098441]    [<ffffffff8170a19e>]    kernel_init+0xe/0x130
    1.098487]    [<ffffffff8172c5bc>]    ret_from_fork+0x7c/0xb0
    1.098534]    [<ffffffff8170a190>]    ? rest_init+0x80/0x80
    1.098580]    ---[ end trace 4eb81820a318a744 ]—

This is my first attempt to try Ubuntu - previously I used a debian desktop 
for several years until its video card died a couple of months ago. This 
USB-stick Ubuntu is destined to install itself onto a desktop previously used 
to house a Smoothwall hardware firewall that protected the debian system, 
so if you tell me that my Dell Inspiron laptop is hopeless, I won't take that
personally. I'd just like to back up the old debian HDD's onto a NAS, using
the USB-stick Ubuntu.

Thanks,
George Langford, amenex for short.

---

### Post by amenex on 2014-12-05
Solved: The USB stick was too big. First clue should have been that the installer
would not let the persistent file be larger than 4GB. I had formatted that 32 GB USB 
stick as NTFS. It and the present 8GB stick are of Centon make.

This morning I formatted an 8GB USB stick as FAT32 and tried the Ubuntu installation
again. I learned about the drive capacity when the installer would have let me set the
persistent file size as anything up to the full capacity of the USB stick. I chose 4GB.

The installation went much quicker this time...

On restarting, UBuntu came up right away and works fine. I was able to access my 
LAN, the Internet and my NAS on the LAN OK.

Lots to learn & re-learn, but Ubuntu works OK on this laptop. Whew.

Thanks for reading this.

George Langford, D.B.A. amenex

Here's what I found yesterday when Ubuntu would not boot from the NTFS-formatted 32GB USB
stick:

> **amenex said:**
> My system is a Dell Inspiron 1545 with 4GB RAM with a similar problem, but with more to look at.

I made a bootable 32GB USB stick and installed Ubuntu 14.04.1 on it using Universal USB Installer.
Then I edited the BIOS to make a suitable boot order (USB first, then CD/DVD, then floppy, last HDD.

On bootup, I select MemTest, which runs OK (I'm familiar with MemTest from long, long ago).

If I select "Try Ubuntu" I get the following text on screen, followed by no more activity:
(This was OCR'ed from a picture of the screen ... I proofread and corrected it)

    1.097440]    [<ffffffff810bf78e>]    handle_irq_event_percpu+0x3e/0x1d0
    1.097488]    [<ffffffff810bf95d>]    handle_irq_event+0x3d/0x60
    ... snippage ...
    1.097962]    [<ffffffff8172d3dd>]    apic_timer_interrupt+0x6d/0x80
    1.098008]    <EOI> [<ffffffff81714f80>] ? panic+0x193/0x1d7
    ... more snippage ...
    1.098534]    [<ffffffff8170a190>]    ? rest_init+0x80/0x80
    1.098580]    ---[ end trace 4eb81820a318a744 ]—

... yet more snippage ...

Thanks,
George Langford, amenex for short.

---

### Post by ajgreeny on 2014-12-06
For future reference, I think the format type for a live USB must be fat32, not ntfs, which probably explains why the 32GB USB did not work; I don't believe it was the size of it that caused the problem.

---

### Post by Blakeo on 2014-12-09
@ajgreeny I tried the boot-repair after it completing and I restarted my computer I got "GNU GRUB [ Minimal BASH-like line editing is supported. etc etc]
Grub> _ 

there was more in the brackets but that is all I can remember, so I did a complete reinstall of Linux Mint using: Lexar 8gb usb instead of UEFI:lexar 8gb usb and it worked. Does it matter that I installed linux mint in legacy instead of UEFI?
I complete overwritten windows and it got removed but IDC if anything I upgraded :)

---

### Post by oldfred on 2014-12-09
You may need a BIOS/UEFI update. The 4GB flash drive limit was fixed, supposedly.
And most Gigabyte versions seem to have iommu issues, which also cause issues on USB ports and other places.
Issues seem to be very common across all models.

 Gigabytes P67 & H67 hybrid efi -Hybrid EFI is a UEFI based on the open source TianoCore
[http://www](http://www).[rod]("http://www.rodsbooks.com/gb-hybrid-efi/")sbooks.com/gb-hybrid-efi/
[http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html](http://gigabytedaily.blogspot.com/2011/01/gigabyte-hybrid-efi-technology.html)
Gigabyte GA-X79-UD3 with I7-3820
Needed F6 (BIOS boot) to set ACPI=Off and nomodeset, add to grub if UEFI boot.
Gigabyte UEFI boot issues - The partition size of the created USB Installer device needs to be under that of 4GB. 
Others found UEFI/BIOS update solved issue of 4GB FAT limit.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)

---

