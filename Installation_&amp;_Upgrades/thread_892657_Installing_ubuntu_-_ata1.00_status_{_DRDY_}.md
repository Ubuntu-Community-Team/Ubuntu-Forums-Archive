---
title: "Installing ubuntu - ata1.00: status { DRDY }"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by carandraug on 2008-08-17
I'm trying to install Ubuntu 8.04 in this computer but this strange error appears and I have no idea what to do

```
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) [61.306417] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 61.306483] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 61.306599] ata1.00: status { DRDY }
[ 91.444103] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 91.444163] ata1.00: cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 dma 4096 in
[ 91.444219] ata1.00: status { DRDY }
```
The 3 lines just keep in repeating and repeating and nothing happens, not even after 10 minutes.

When the computer was given to me it was running Windows XP which took forever to boot. I didn't care nor found it strange and installed PCLinuxOS (which looks like a fine distro by the way). I had no problem during installation but boot also took a lot of time so I took a look at dmesg where I noticed some problem with the hard disk. I attached the dmesg and here's the lines where errors happens and the boot takes a lot of time
```
hda: max request size: 128KiB
hda: 117231408 sectors (60022 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
hda: cache flushes not supported
 hda:<4>hda: dma_timer_expiry: dma status == 0x21
hda: DMA timeout error
hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
 hda1 hda2 <<4>hda: dma_timer_expiry: dma status == 0x21
hda: DMA timeout error
hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
 hda5<4>hda: dma_timer_expiry: dma status == 0x21
hda: DMA timeout error
hda: dma timeout error: status=0x58 { DriveReady SeekComplete DataRequest }
ide: failed opcode was: unknown
 hda6 >
```
I ran badblocks and it reported nothing. I tried to switch the PATA cables. I also tried connecting the HD to the motherboard connector where the CD-rom was previously connected. In both cases, the error persisted.

It may have something to do with the reason why Ubuntu or maybe not. For that reason I was unsure wheter it belongs in the installation or hardware section of the forum.
I'm aware this is not a PCLinuxOS support forum but what I want is to install Ubuntu. If the only problem I get in the end is a long time of boot that's okay with me (although it would be better to know the reason of it and maybe fix it).

---

### Post by carandraug on 2008-08-18
*bump

---

### Post by kayvee on 2008-08-29
I have the exact same problem. Is there any solution?

---

### Post by carandraug on 2008-08-29
I believe the problem is hardware related. If I remove the hard drive I have no problem (but then have nowhere to install it). I'm trying to get another hardrive on that computer to check if the problem is really on the HD an not on some connection to it or in the motherboard.
Also, I'll try the alternate CD.
However I'll only be able to try this in two weeks from now. I'll post something whether I success or not. Try it yourself in the mean time if you can.

---

### Post by robhynes on 2008-09-09
Did anyone come up with a workaround for this?

I've just experienced this problem. I have a IDE drive connected to IDE0 which is unpartitioned and 2 SATA drives which are connected via a PCI card.

Thanks

RobH

---

### Post by PhilG6AKK on 2008-09-11
Hi Guys,

I've not got a fix but I think I know what it might be.

Ive been playing around with two PC one Ubuntu and the other Windows and for variaous reason I have gone back to one machine for both.

To cut a long story short I needed different sizes of hard drive so I used a 120Gb ATA drive on the same computer that I'd used previously with a 40gGb drive for the Ubuntu OS. Reformated it ntfs not fat and reloaded windows no problem. But when I tried to load Heron I got the errors you are getting.

I thought it was me burning the disk from Iso wrongly, when I tried to load Dapper which I used no trouble at all before it just took ages to load. Like go down stairs make a mug of tea and some tost, phone my mum to see how she was then go up stairs and check if it was ready, and it nearly was.

When I then upgraded it to Heron using the update program then when it resbooted I got all your errors.

So maybe the fix is IDE drives and fat32 any way I'll stick to windows for a bit then perhaps look on ebay for a cheap Ide drive and reload windows etc.

Mind you I now have a 4GB Assus Eee pc running Xandros perhaps in a few months time I'll be brave and try EeeBuntu

Hope this helps 

Phil

---

### Post by BiGBeN_87 on 2008-09-28
Hello,

Sorry for digging this up again without having an solution or at least a workaround, but perhaps this helps someone if not me.

I have got the same problem here with 2.6.24-19-generic. The device causing the trouble seems to be an CompactFlash-Card attached via an adapter to an IDE-Controller (on-board).

Following your suggestion, PhilG6AKK, I tried to boot my Ubuntu with the CF-Card installed and waited a little. I can report, that it takes about 3 minutes for me to boot Linux with that defective subsystem. Also the message continues occurring in /var/log/kern.log every 1:30 minutes. The "gnome-device-manager" reads correct data.

Using an USB-cardreader, I managed to create partitions as demanded, but only linux-swap and FAT16/FAT32 worked properly. Formatting to ext2 and ext3 failed repeatedly. (Reiser not tested yet.)

Soon after starting to format the volume, die cardreader stopped blinking (and so stopped indicating read/write-activity). CPU-load instead remained on a high level. Stopping the progress and returning to format let the load drop and seemed to carry on for a while, but again activity dropped out. I could repeat and recreate this. I can not find any information on CF-cards not working with filesystems other than FAT and swap in general or ext2/3 specifically.

Grub installed flawlessly, but using it failed with "Please insert bootdevice and press enter." - Or so, you know. ^^ ... The BIOS could read all information correctly though.

Because it worked in cardreaders (with Vista and nautilus on FAT32 and grub on its MBR) I assume the card itself is not defective. Failures occur, when attached to IDE via adapter and also with more complex and/or journaling filesystems.

Thanks for your patience,
bigben_87

---

### Post by emagister on 2008-11-05
> **carandraug said:**
> I believe the problem is hardware related. If I remove the hard drive I have no problem (but then have nowhere to install it). I'm trying to get another hardrive on that computer to check if the problem is really on the HD an not on some connection to it or in the motherboard.
Also, I'll try the alternate CD.
However I'll only be able to try this in two weeks from now. I'll post something whether I success or not. Try it yourself in the mean time if you can.

OK guys, I'm new here, also having my first cup of Ubuntu, ok? However, been almost 30 years in the business, started with Visicalc and floppies then, no hard drives; installed the first Xenix systems in my country, had my lessons in Unix and have survived all Windows versions. This problem in particular that you are referring: "ata1.00: status { DRDY }" or  ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen" and similarly related, that might come out of the blue or during installation of Ubuntu or Xubuntu and it takes ages to load, reload or won't even come up is related to a hardware problem. The harddisk is not good any more. Curiuosly, that same disk might run perfectly under Windows (FAT 16, FAT 32 and NTFS), but it simply won't start with Ubuntu's filesystem. Do yourselves a favor and don't waste your time. Change the disk and the faulty one use it for other non critical applications (never for backup).
The tricky question here is: What is there in the linux-Ubuntu (Reiser) filesystem that makes it impossible to load???
I'd like to hear the experts opinion!

In addition, currently I have the chance to work in a service area in a university campus with 20 some linux PC stations and servers and I do have to bring back to life faulty equipment. So these errors are consistent with hardisk failures. The tricky questions remains though!

---

### Post by MarshyTheKid on 2008-11-07
Hmm. So a few minutes ago my laptop started making terrible hard drive noises so I restarted and it sounds fine now. The only problem is that when I run firefox it takes about 5 minutes to start and when it does I have no settings. I can still use the hard drive other than that.
I wonder if I can reinstall firefox and have it work. Hmm.

---

### Post by Gyruss on 2008-11-07
Linux filesystems in general, not just ReiserFS, spread the data all over the disk much more efficiently than the linear-chunk nature of FAT and NTFS. It's why you never hear about defragmenters for Linux.
Unfortunately this means that they are also much more sensitive to disks going bad because a single bad sector can make much more of the filesystem invisible.
Btrfs will really help with this problem when it is hopefully released next year.
BTW, when you run badblocks, you should do a write test if you don't care about the data on the disk.

---

### Post by MarshyTheKid on 2008-11-07
So I ran bad blocks on both my root drive and my home drive. It found maybe 60-70 bad blocks, so I rebooted up.
This so far has only affected firefox. When I run firefox I get ata1.00: status { DRDY } and error { UNC }
I was hoping for it to work now since I ran badblocks, but I still get those errors.
Any help?

---

### Post by msknight on 2008-11-10
Another user with the same problem.  Running Gutsy quite happily (except that it needed the IRQPOLL in the start up) and then updated to Heron this morning and now all I get is the error as initially prescribed.

OS is on SATA drive.  Machine running perfectly happy for who knows how many months now, but this update has trashed it.  From my side, this is not appearing to be a hardware failure.

This error just keeps going, and going, and going.  I'm going to have to revert to GG if there isn't any solution.

---

### Post by vievie on 2008-12-10
I had the same problem with my Shuttle X27D mini PC and an eBay dual CF-IDE adapter. My finding so far is the secondary CF slot is the problem.

Once I remove the secondary CF, the ATA1.00 DRDY problem is gone.

Hope it help.

---

### Post by JerreCope on 2008-12-11
Here's the deal.  Your hard drives didn't coincidentally crash when you upgraded to Hardy.  What happened is that we stepped into a new kernel / sata controller problem.  

See:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204916]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/204916")

The simplest solution is to add irqpoll to the grub boot options.

[LIST=1]
[*]Edit /boot/grub/menu.lst kernel options (add irqpool at the end)
[*]update-grub
[/LIST]

Alternately boot from a kernel round 2.6.16 vintage.

---

### Post by RFXCasey on 2009-11-24
Having this same problem with a Compaq Presario sr1420nx and IDE drives. I need to know exactly what and how to enter it into the install options for 9.10. Thanks.

---

