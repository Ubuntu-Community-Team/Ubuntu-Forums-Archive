---
title: "Error message with Feisty LiveCD &quot;unable to find a medium containg a live file system"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by wildzer0 on 2007-10-13
I just purchased a new laptop and am trying to install Feisty on it. The CD gets to the first menu (Install, Check CD For Defects, etc). Anything I select loads the linux kernel and then gives me an error that says "Can't access tty: Job control turned off". I looked in casper.log and it gives me this:

Mount: mounting /dev/sda1 on /cdrom failed: no such device
Mount: mounting /dev/sda2 on /cdrom failed: no such device

/init: /init: 1: cannot open /dev/sdb no medium found
/init: /init: 1: cannot open /dev/sdb no medium found

Unable to find a medium containing a live file system

It's a brand new gateway MA8 laptop with the following specs:
Processor: Intel Pentium Dual-Core Processor 1.46 ghz. 
1 gb DDR2 Memory
Serial ATA 120gb hd
Double-layer DVD+RW/CD-RW Optical Drive

It's got Vista basic installed by default. It's kind of an emergency as I need to finish a project - I have no desire to keep Vista so whatever will get me up and running quickly with Linux would be awesome. I tried Feisty and the RC for Gutsy. Any help is greatly appreciated.

---

### Post by wildzer0 on 2007-10-13
OK, I found a post from a couple of months back with someone having a similar problem. I tried one thing he recommended which got me a bit further (but not all the way). 

Select "other options" with F6 at the first ubuntu screen. Remove "splash quiet --" Add "all_generic_ide". It gets me pretty far, and then gives an x server failed message and gives me a command prompt. Not sure what to do from there. 

I shoudl also mention, the md5sum checked out fine for the original download. I can't check the disk for defects at this point however.

---

### Post by wildzer0 on 2007-10-13
At the advice of another post, I added break=top and ran modprobe piix at the command line. This was the output. 

[7.203073] ICH8M: IDE Controller at PCI slot 0000:00:1f.1
[7.203149] ACPI: PCI Interrupt 0000:00:1f.1[A] -> GSI 19 (level, low) -> IRQ19
[7.203298] ICH8M: Chipset revision 3
[7.203364] ICH8M: Not 100% native mod: will probe IRQs later
[7.203444] ide0: BM-DMA at 0x1810-0x1817, BIOS Settings: hda:DMA hdb:pio
[7.941676] hda: Optiarc DVD-RW AD-7563A, ATAP: CD/DVD-ROM Drive
[88.617019] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14

Don't know if this is completely unecessary or whatever, but I'm desperate for a solution at the moment, so if this helps here it is.

---

### Post by aBitLater on 2008-07-03
I get the same message with hardy install to toshiba portege 3500.  I don't think the installer can see my DVD drive when it gets to a certain point

---

