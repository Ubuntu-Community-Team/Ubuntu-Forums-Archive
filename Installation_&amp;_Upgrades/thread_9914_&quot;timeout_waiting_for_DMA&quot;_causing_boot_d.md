---
title: "&quot;timeout waiting for DMA&quot; causing boot delay"
date: 2005-01-02
forum: Installation &amp; Upgrades
---

### Post by x66221 on 2005-01-02
I am a newbie and have just installed Ubuntu.  It is running great except for a problem which causes a DELAY DURING THE BOOT.  When I boot up, it gets to the "Starting Ubuntu..." and then pauses about 10-15 seconds, then says:

"hde: timeout waiting for DMA" ... then pauses for another 15 seconds or so ... then
"hde: timeout waiting for DMA" ... then pauses for another 15 seconds or so ... then
"hde: timeout waiting for DMA" ... then pauses for another 15 seconds or so ... then
"hde: timeout waiting for DMA" ... then pauses for another 15 seconds or so ... then

it does this four times then the boot continues uneventfully.

hde is my linux boot drive (on a dual-boot system).  It (hde) is an IBM IC35L040AVVA07-0 that is about two years old.  It is on the primary master channel of an Adaptec ATA RAID 1200A PCI card.  I'm using the card not for RAID functionality, but because I've used up the other ATA channels for the Windows XP part of my system.

"dmesg | grep hde" outputs:

>     ide2: BM-DMA at 0xd400-0xd407, BIOS settings: hde: pio, hdf: pio
hde: IC35L040AVVA07-0, ATA DISK drive
hde: max request size: 128KiB
hde: 80418240 sectors (41174 MB) w/1863KiB Cache, CHS=65535/16/63, UDMA(100)
 /dev/ide/host2/bus0/target0/lun0:<4>hde: dma_timer_expiry: dma status == 0x21
hde: DMA timeout error
hde: 0 bytes in FIFO
hde: timeout waiting for DMA
hde: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
 p1 p2 <<4>hde: dma_timer_expiry: dma status == 0x21
hde: DMA timeout error
hde: 0 bytes in FIFO
hde: timeout waiting for DMA
hde: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
hde: dma_timer_expiry: dma status == 0x21
hde: DMA timeout error
hde: 0 bytes in FIFO
hde: timeout waiting for DMA
hde: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
hde: dma_timer_expiry: dma status == 0x21
hde: DMA timeout error
hde: 0 bytes in FIFO
hde: timeout waiting for DMA
hde: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
EXT3-fs: hde1: orphan cleanup on readonly fs
EXT3-fs: hde1: 1 orphan inode deleted
Adding 499928k swap on /dev/hde5.  Priority:-1 extents:1
EXT3 FS on hde1, internal journal 

Any ideas?  8-[

---

### Post by nemin on 2005-01-03
[QUOTE=x66221]I am a newbie and have just installed Ubuntu.  It is running great except for a problem which causes a DELAY DURING THE BOOT.  When I boot up, it gets to the "Starting Ubuntu..." and then pauses about 10-15 seconds, then says:

"hde: timeout waiting for DMA" ... then pauses for another 15 seconds or so ... then
"hde: timeout waiting for DMA" ... then pauses for another 15 seconds or so ... then
"hde: timeout waiting for DMA" ... then pauses for another 15 seconds or so ... then
"hde: timeout waiting for DMA" ... then pauses for another 15 seconds or so ... then

it does this four times then the boot continues uneventfully.
Any ideas?  8-[[/QUOTE]
You could try to (temporary) disable DMA for this harddisk:
> 
hdparm -d0 /dev/hde


---

### Post by x66221 on 2005-01-03
Thanks for your reply.

I tried ...

> hdparm -d0 /dev/hde

... and it outputed ...

> /dev/hde:
 setting using_dma to 0 (off)
 using_dma    =  0 (off)

... then I rebooted, but the problem continues (see below).  Any other ideas?  Do I need to put the "hdparm -d0 /dev/hde" command into some script that is executed at startup before the hde is loaded?  (I'm a newbie).   :confused: 

> 
ide2: BM-DMA at 0xd400-0xd407, BIOS settings: hde: pio, hdf: pio
hde: IC35L040AVVA07-0, ATA DISK drive
hde: max request size: 128KiB
hde: 80418240 sectors (41174 MB) w/1863KiB Cache, CHS=65535/16/63, UDMA(100)
 /dev/ide/host2/bus0/target0/lun0:<4>hde: dma_timer_expiry: dma status == 0x21
hde: DMA timeout error
hde: 0 bytes in FIFO
hde: timeout waiting for DMA
hde: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
 p1 p2 <<4>hde: dma_timer_expiry: dma status == 0x21
hde: DMA timeout error
hde: 0 bytes in FIFO
hde: timeout waiting for DMA
hde: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
hde: dma_timer_expiry: dma status == 0x21
hde: DMA timeout error
hde: 0 bytes in FIFO
hde: timeout waiting for DMA
hde: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
hde: dma_timer_expiry: dma status == 0x21
hde: DMA timeout error
hde: 0 bytes in FIFO
hde: timeout waiting for DMA
hde: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
Adding 499928k swap on /dev/hde5.  Priority:-1 extents:1
EXT3 FS on hde1, internal journal


---

### Post by mrosenlof on 2005-01-03
I am seeing this also (just posted a question to the hardware support forum).  This is coming up (for me also) right after the 'starting ubuntu' in the boot process.  This is long before the HD parameters are set in the init process.

I think what's needed is a kernel option at boot time to turn off the HD DMA, but I don't know what that option is, or if it exists.

Are you by any chance using some old hardware that might not support DMA?  In my case, I'm using a compact flash device in an IDE adapter.

---

### Post by x66221 on 2005-01-03
The one thing this is unusual about my setup is that this drive (hde) is plugged into one of the two IDE channels on an [Adaptec ATA RAID 1200A PCI card](http://adaptec.com/worldwide/product/proddetail.html?sess=no&language=English+US&prodkey=AAR-1200A&cat=%2fTechnology%2fRAID%2fATA+RAID).  This is because I have used up the other four channels with Windows-related drives.  However, this card does support (at least in the Windows environment) DMA.

---

### Post by nemin on 2005-01-04
[QUOTE=mrosenlof]
I think what's needed is a kernel option at boot time to turn off the HD DMA, but I don't know what that option is, or if it exists.[/QUOTE]
A little google search showed me this:
"Use DMA by default when available: CONFIG_IDEDMA_AUTO"

Good chance this will fix your problem I think, give it a try! :)

---

### Post by x66221 on 2005-01-04
[QUOTE=nemin]"Use DMA by default when available: CONFIG_IDEDMA_AUTO"[/QUOTE]

nemin,

Thank you.  How do I use this?  Where do I put it?  A configuration file?  An option during recompile of the kernel?  I'm just starting out on the linux learning curve.   :)

Rob

---

### Post by mrosenlof on 2005-01-04
Take a look at this link  [http://www.ubuntuforums.org/showthread.php?t=9988](http://www.ubuntuforums.org/showthread.php?t=9988)
using a kernel boot parameter of ide=nodma got me past this problem.

When grub starts, hit <escape> to get to the boot menu, select your kernel, type 'e' to edit the line, then 'e' to edit the boot line.  This line has some other options like 'ro quiet splash' (possibly) on it.  Add ide=nodma, then type 'b' to boot.

Most modern hardware _should_ support DMA.  My problem is with a Compact flash card and a CF<->IDE adapter, something that's not really a very high speed device.  You may have a driver issue with your Adaptec card.

---

### Post by x66221 on 2005-01-04
Success!

I modified

kernel  /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hde1 ro quiet splash

to

kernel  /boot/vmlinuz-2.6.8.1-3-386 root=/dev/hde1 ro quiet splash ide=nodma

... and it booted up just fine.  I tried to add hde=nodma (instead of ide=nodma), but it didn't like that and went through multiple iterations of the dma timeout error.

(added for other newbies ...)

Then, I did "sudo gedit /boot/grub/menu.lst" and made the above changes permanent.

---

### Post by nemin on 2005-01-05
[QUOTE=x66221]nemin,
Thank you.  How do I use this?  Where do I put it?  A configuration file?  An option during recompile of the kernel?[/QUOTE]
Hehe, this is absolutely not the easiest way to got this problem fixed, I'm sorry for that. [-X 
This is an option you can select when you're recompiling a kernel. You can compare it with a default "ide=nodma" option.
Of course, giving this "ide=nodma" option when booting the kernel it much easier and faster :)

---

### Post by darkaudit on 2005-03-23
I just had this happen for the first time this afternoon with the 2.6.10-i686-5 kernel. Just after hdparm ran, the boot would hang. After a couple of resets, it finally booted, and seems to run normally.

---

### Post by Cyorxamp on 2006-09-20
Hey,

I get this all the time, even on Mandriva and other distro's... I am sure that the nodma thing will work.

However I remember the booting up not taking so long (i.e. due to the delay discussed) on old Ubuntu 5.10.... is this a kernel issue that is waiting to be fixed and nodma is just the work around?

---

### Post by sylverpyro on 2006-10-15
Quick summary:
hdg: timeout waiting for DMA

During boot

Tried adding hdg=nodma to /boot/grub/menu.lst for that kernel image, did not help

Tried adding this to /etc/hdpram.conf
command_line {
     hdparm -d0 /dev/hdg
} 
again no luck

Tried turning off DMA on my controller in its BIOS settings, again no luck.

The only thing that seemed to work was giving grub ide=nodma and that seemed to fix the issue.  
Now, I would like to keep DMA on my other three devices, does anyone know why only the wholesale version of nodma works?

---

### Post by sylverpyro on 2006-10-15
Just to bring my last post some closure, I also added this to hdparm.conf
(I tried putting all of these into the same command_line {} block but it only executed the first hdparm -d1 command.  This syntax seemed to work better)

```

command_line {
     hdparm -d1 /dev/hda
}
command_line {
     hdparm -d1 /dev/hdc
}
command_line {
     hdparm -d1 /dev/hde
}

```

This along with ide=nodma in grub/menu.lst has all the devices that I want with DMA using DMA.  It would still be nice to know why hdg=nodma does not work in Grub now.

---

### Post by pablovp on 2007-01-01
Im using edgy, with kernel 2.6.17 and solved it disabling dma at boot time.

Anyone solved the problem without disabling dma?

---

### Post by terabaud on 2008-07-11
Hi there, I'm also booting linux from a 4GB Compact Flash Card with an IDE-to-CF connector. I've had the same boot delay caused by the DMA timeout.

hdparm didn't help. Boot parameters didn't help. I tried ide=nodma, hda=nodma, hda=noprobe, hda=####,##,## (cyls, heads, sectors) etc.

So I downloaded the current stable kernel sources from kernel.org (2.6.25) and looked for a CONFIG option to disable DMA on ide drives. Unfortunately, I haven't found any option to disable DMA searching.

But, after looking at the source code of the ide kernel driver, I've found a solution :

Open the file "drivers/ide/ide.c" in the kernel source directory.
In this file, there's a global variable defined. Look for

int noautodma = 0;

and set it to 1. That's it.

---

