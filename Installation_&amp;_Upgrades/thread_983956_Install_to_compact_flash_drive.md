---
title: "Install to compact flash drive?"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by gilgongo on 2008-11-16
Hi,

I'm trying to install Ubuntu Hardy 8.04 to a CF drive using an IDE connector:

[http://www.digitalera.co.uk/products/CF_to_IDE_adapter_Direct-654-53.html](http://www.digitalera.co.uk/products/CF_to_IDE_adapter_Direct-654-53.html)

I'm using the alternate installation CD to choose "Command line install." I can get to the bit where I'm partitioning the disk, which I set up (without any swap) as follows:

sda 2Gig root / ext2 noatime bootable

The installer then formats the drive, but when it's about 50% through setting up the file system ("Creating Ext2 file system..."), it stops, and then I see this error:

"Installer cannot figure out how to install the base system. No installable CD ROM was found, and no valid mirror was configured."

Bringing up a console to look at the syslog, I see:

kernel: end_request: i/o error, dev sr0, sector 1808

Further back in the log I also see "Driver 'sr' needs updating" - dunno if that's related.

Is this some hardware or kernel config thing? I'm using a recent Asus motherboard, the CD is configured as master (as is the CF card adapter).

Does anyone know what I should try?

---

### Post by gilgongo on 2008-11-16
After some further playing about, I decided to see if I could make it work on a (very) old machine I have. I booted off a floppy, formatted the card as FAT32, and put DOS on it. Seemed to boot just fine. 

So, I moved the card to the machine I'm trying to make it work on, and it won't boot. The BIOS just seems to come up with an "invalid drive" message. The BIOS setup sees the card OK though.

Anyone any ideas? I'm using an Asus M2N-CM DVI motherboard if that's any help. I've even tried it with two IDE cables: the one that came with the mobo and one that I had spare. Sometimes I can install Ubuntu OK, but after a reboot, it comes up with ATA errors which indicate a bad cable or something. Ubuntu then tries to fix the disk, which then refuses to boot after that.

I've even switched the CF card for an identical one, and I still get the same errors.

---

### Post by djm-uk on 2008-11-16
The CD and CF adapter ARE on seperate IDE cables aren't they...?

David

---

### Post by Neostar on 2008-11-16
Try reseting the CMOS on the ASUS motherboard.

---

### Post by gilgongo on 2008-11-16
> **djm-uk said:**
> The CD and CF adapter ARE on seperate IDE cables aren't they...?

Er, no. Should they be? The motherboard only has one IDE socket, so they have to be on the same cable. At least, the standard HD that was in the machine was working fine on the single cable.

---

### Post by gilgongo on 2008-11-16
> **Neostar said:**
> Try reseting the CMOS on the ASUS motherboard.

OK, thanks I'll give that a go (run out of time until tomorrow).

---

### Post by djm-uk on 2008-11-17
OK so you have the CF and CD on the same cable & both set to 'master' - that isn't going to work....  One needs to be set to slave (or use cable select if the cable & devices support it - the cable connectors will be labelled master & slave if it a CS cable)...  'Conventionally' the CD is set to slave....

David

---

### Post by gilgongo on 2008-11-17
> **djm-uk said:**
> OK so you have the CF and CD on the same cable & both set to 'master' - that isn't going to work....  One needs to be set to slave (or use cable select if the cable & devices support it - the cable connectors will be labelled master & slave if it a CS cable)...  'Conventionally' the CD is set to slave....

I've tried all the combinations of master/slave/cs on both the CF connector and the CD connector. I've even tried a different CD. 

The strange thing is that sometimes when I change a combination (eg setting the CD to CS), I am able to install and boot the OS, but with errors that eventually make the disc unbootable. Other times the installer gives up. 

The only pattern I can find (I think) is that if I delete the partition first, then proceed, I get to the end of the install, but if I simply re-format the existing partition, it gives up on creating the file system.

I've yet to try re-setting the CMOS though, but if that doesn't work I'll have to get the whole thing on eBay. I suppose I could try installing Windows first though just to see if it's an Ubuntu thing. Having Windows actually *running* in the same room as I am fills me with nausea though.

---

### Post by djm-uk on 2008-11-17
It is possible there are multiple problems...

Certainly the CF & CD should be set to 1 master & 1 slave, otherwise they will conflict - The error you showed first suggested that the system had lost touch with the CD after the format of the CF drive....  

Is it possible install either off a USB CD drive or set up a live USB stick so you can boot & install off that?

David

PS just looked at the CF adapter on the link above - it is a female connector on the CF adapter so how are you getting that to plug into an IDE cable which is also a female connector, also I see no master/slave setting on the picture...?

---

### Post by gilgongo on 2008-11-18
Hi - thanks David.

I'll see if I can boot from a USB stick and install off that (does Ubuntu Live have a command line install option though I wonder?). Seems like the best explanation is that there's some issue with the IDE connection chain.

As to he adapter - I think I may have linked to the wrong model by mistake, the one I have is:

[http://www.digitalera.co.uk/products/CF_to_IDE_adapter_HDD-657-53.html](http://www.digitalera.co.uk/products/CF_to_IDE_adapter_HDD-657-53.html)

Although you'd have to *try* to produce a worse photo than that, the connector is male. The master/slave jumper is barely visible, but it's there.

I've still not been able to get time to test all these possible remedies out yet, but it's good to have them. I can't believe I can't install this.

---

### Post by gilgongo on 2008-11-19
OK it looks like I can install from a USB stick. I did this by dowloading the net install:

wget [http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/boot.img.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/boot.img.gz)

And wirting that to the stick like this:

zcat boot.img.gz > /dev/sdb

I then installed to the CF card from there.

The trouble now is that the machine won't boot unless I have the USB stick in!

AAARGH!!

---

### Post by gilgongo on 2008-11-20
(that's odd - thought I replied to this yesterday)

It looks like I've installed the OS OK onto the CF drive using a USB memory stick. I did this by making the stick bootable using the net installer:

[http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/boot.img.gz](http://archive.ubuntu.com/ubuntu/dists/hardy/main/installer-i386/current/images/netboot/boot.img.gz)

The trouble is that now the CF disk won't boot without the memory stick! It just says "no operating system found". 

Why is the machine picking up grub from the memory stick, but then booting the rest from the CF disk?

:confused:

---

### Post by Neostar on 2008-11-20
I think your Bios settings are screwed up, just reset your CMOS and then start by setting the dvdrom to boot up first then hard drive then others depending on what you want.

---

### Post by djm-uk on 2008-11-20
How about making the CF bootable like you did the memory stick...???

I would expect that if you make a 'live CD' USB stick & boot off that then it should install to the CF exactly as though from the CD (including writing MBR Etc). I think there is an option to do this on the 81.0 Live CD...

David

---

### Post by gilgongo on 2008-11-20
Ah - forgot to try re-setting the CMOS. Will try that.

If I make CF bootable like I did the memory stick - will I be able to install Ubuntu onto itself? I would have expected you need to install from one media to another, no?

When you say you would expect that if you make a 'live CD' USB stick to boot from it should install to the CF exactly as though from the CD - that's what I thought as well! When I tried it though, it seems not to write the MBR to the right device.

---

### Post by gilgongo on 2008-11-21
Re-setting the CMOS didn't make any difference.

I feel there's something to do with the USB stick that I installed it from that may be a clue though - if only I could find out what.

---

### Post by igel on 2008-11-21
Sory for deverting the thread to another question.

I have a mb with a intel 430TX chipset and PIIX4. The compact flash is with adapter directly inserted into primary ide. The secondary channel is occupied by CDRW. The CF card has support for UDMA mode 4 (that is 66).

The trouble is I cannot even start installing. It seems like the kernel tries to initializie PIIX, seed the CF (as sda) and the I see dma frozen messages. I tried setting to PIO only from BIOS and giving ide=nodma but this does not help.

Just for the test I tried w2k3 which installs fine on the card and runs from it in UDMA4. 

So I guess the above may come from the kernel trying to use MDMA which I suppose is not supported by the card. 

Any ideas will be much appreciated.

---

### Post by Neostar on 2008-11-21
Sorry to hear it didn't work :(

---

### Post by gilgongo on 2008-11-22
> **igel said:**
> Sory for deverting the thread to another question.

I have a mb with a intel 430TX chipset and PIIX4. The compact flash is with adapter directly inserted into primary ide. The secondary channel is occupied by CDRW. The CF card has support for UDMA mode 4 (that is 66).

The trouble is I cannot even start installing. It seems like the kernel tries to initializie PIIX, seed the CF (as sda) and the I see dma frozen messages. I tried setting to PIO only from BIOS and giving ide=nodma but this does not help.

Interesting. I'm not seeing dma frozen messages, but I am seeing the other stuff that you describe, and my setup is very similar.

I've not yet tried installing Windows to see if that works. I suppose if both of us can install Windows but not Ubuntu, then that would isolate the issue to Linux. 

I only get the chance to experiment on my machine once every few days, but I'll try the Windows test next and let you know.

---

### Post by igel on 2008-11-24
Hi gilgongo,

since I wanted to use my box for router/firewall i went ahead and installed m0n0wall ([http://m0n0.ch](http://m0n0.ch)). Is is freeBSD based and works for me (well, kindof, I need two WAN ports so I will try pfSence). I just wanted to let you know, if you need the box for a router that m0n0wall may be worth trying.

---

### Post by gilgongo on 2008-11-24
OK thanks - looks like Ubuntu is bootable from a CF card (according to some folks over at xbmc.org), so I'll keep trying.

---

### Post by kaq on 2009-02-21
did you make it work???

---

### Post by gilgongo on 2009-02-23
> **kaq said:**
> did you make it work???

Sadly, no. The best I've got it to do is boot to a command prompt once after a fresh install onto the card. Subsequent reboots just fail with what look like driver errors of some kind, or the mobo comes up with "not a bootable device" and leaves it dead.

:(

---

