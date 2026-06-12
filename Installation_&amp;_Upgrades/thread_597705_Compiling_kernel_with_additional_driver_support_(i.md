---
title: "Compiling kernel with additional driver support (inic162x)"
date: 2007-10-30
forum: Installation &amp; Upgrades
---

### Post by beaver86 on 2007-10-30
Hello!

I want to compile 2.6.23. or 2.6.23.1. kernel on Ubuntu 7.10 - but driver for my Initio INIC162x SATA card isn't listed there (make menuconfig >> Device Drivers >> SCSI device support >> SCSI low-level drivers)!

I found sata_inic162x.c on [http://www.linuxhq.com/kernel/v2.6/23/drivers/ata/sata_inic162x.c](http://www.linuxhq.com/kernel/v2.6/23/drivers/ata/sata_inic162x.c) but that's only the "patch" version! Where can i find the "full" version of that file ?

Thanks a lot

---

### Post by beaver86 on 2007-10-30
It was a stupid question....

I apologize for the inconvenience...

I'm a n00b... I hope i'll fix my problem when i compile that kernel.

---

### Post by beaver86 on 2007-10-30
I guess i dindn't succeeded ... I'm getting error when trying to build the kernel..
```

make[3]: *** No rule to make target `drivers/scsi/sata_initio162x.o', needed by `drivers/scsi/built-in.o'.  Stop.
make[2]: *** [drivers/scsi] Error 2
make[1]: *** [drivers] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.23.1'
make: *** [debian/stamp-build-kernel] Error 2
```

:(

Can anybody help me with that ?

Please

---

### Post by colgate on 2007-11-14
Hi,
I'm trying to get this (stupid) card working too. We can share efforts. I'm trying to make it work on big disk, capacity > 137 Gb.

First I downloaded the latest driver from the sunix website. It says that it should work on FC5, kernel 2.6.15. So I got dapper, which has 2.6.15 and I did compile it (I just followed the standard instruction, so I copied the file to the linux-source/drivers/scsi, set up Kconfig, Makefile and updated pci_ids.h as said). So I did run make menuconfig to select the module and then started a "make modules" so I got the .ko (you need the ko, not the .o!).
Everything did run smooth. No compile errors! 

So I started my system from my old pata disk and then
modprobe libata (it contains various symbols needed by the studid module) and then I did cd to the linux-source/drivers/scsi and then
insmod sata_initio162x.ko
the module went up! :-)

BUT it froze my system :-( EVERYTIME! 
thanks to another shell doing a tail -f /var/log/messages  (and a dmesgh right after inserting the module and right before the freeze, yes, you have to be realllllly quick ;-) ) I could see what did happen:

[42949921.610000] SCSI subsystem initialized
[42949921.630000] ACPI: bus type scsi registered
[42949921.630000] libata version 1.20 loaded.
[42949999.560000] sata_initio162x: no version for "struct_module" found: kernel tainted.
[42949999.570000] inix module init 
[42949999.570000] sata_initio162x 0000:00:0d.0: version 0.3
[42949999.570000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [LNKD] -> GSI 12 (level, low) -> IRQ 12
[42949999.630000] ata1: SATA max UDMA/133 cmd 0x1A000 ctl 0x19802 bmdma 0x0 irq 12
[42949999.630000] ata2: SATA max UDMA/133 cmd 0x19400 ctl 0x19002 bmdma 0x0 irq 12

Does anyone knows how can I know where it freezes??? I don't....

Then I found that there's an effort of getting this card working on newer kernel. I tried to port this module for 2.6.15 on Gutsy kernel, 2.6.22 (on hardy there is the same kernel, now... and I didn't want to compile a new kernel from scratch!). It wasn't really easy because last April a lot of stuff changed in the way how sata stuff works, so I had to change all that stuff. That's bad but I think I got it right.
BUT some methods where removed from libata in particular everything related to "struct ata_probe_ent". So I couldn't work around from them because I'm no expert in libata. This stuff was needed in the init function. I tried the stupidest thing to do: i deleted the init function from the sunix driver and i did replace it with the latest one from kernel 2.6.23 (without the patches from 2.6.24) and I tried to compile it on a 2.6.22 kernel. Ok, that's absolutely no good, but it DID COMPILE and I could get the .ko.

So I started a install cd from gutsy (server ed), and I got a shell. I tried to insmod the modules (compiled on another system with the same kernel) and it WORKED! cool. No freeze. The kernel did recognize the card, no more LBA complaining and it recognized the 2 disks.
But It didn't create the devices under /dev. Why? I don't know. Does anyone knows how?
So I couldn't move forward with the installer. 

In the attachment there is the modified version and the original one from Sunix-crap. And the .ko.
if it can be of any use for anyone.


Does anyone know how to go further?

   Federico

---

### Post by colgate on 2007-11-14
I was forgetting....
I did use the sunix module beacuse the module in 2.6.24 still miss the LBA8 (hd bigger than 137Gb) support! Or, this is what I understood.

Federico

---

### Post by taz@northernbloke.co.uk on 2008-05-10
Has anyone had any luck get this SATA controller working in Ubuntu yet? I have PCMCIA SATA card in my IBM ThinkPad T23, which I bought new from an eBay seller. When I do an lspci the card shows up as:

   Initio Corporation INI-1623 PCI SATA-II Controller (rev 02)

I went to the Initio web site ([http://www.initio.com/index.html]("http://www.initio.com/index.html")) and found a link for a Linux driver ([http://www.initio.com/drivers/Linux.SATA.drvr.2.6.15.zip]("http://www.initio.com/drivers/Linux.SATA.drvr.2.6.15.zip")).

Its great that they've provided the source code, however, it would have been nice if they had provided some binaries for various distros.

I am running Ubuntu Hardy and was really hoping the card would just work once plugged in.

They've provided ZIP file they've provided contains a single C source file, a few sample files and a readme. The readme covers an example from a Fedora perspective.

Please excuse my inexperience. But when compiled against the Kernel source, will it produce:

1) a new Kernel i.e. I will I have to replace the Kernel binary shipped with Ubuntu and recompile every time I wanted to use an updated Kernel

 OR

2) does it produce a Kernel module i.e. still have to recompile for new Kernels but don't have to replace anything shipped with ubuntu.

If anyone could help, it would be greatly appreciated by myself and all the others who seem to be having problems with this (relatively new???) controller.

Thanks.

P.S. I've attached the driver from Initio, as it is only a 46K ZIP file.

---

