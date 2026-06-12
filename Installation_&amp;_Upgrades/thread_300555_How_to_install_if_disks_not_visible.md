---
title: "How to install if disks not visible?"
date: 2006-11-15
forum: Installation &amp; Upgrades
---

### Post by boortz on 2006-11-15
I have put together a new machine with three SATA
drives, two WD raptors and one Samsung Spinpoint.
The motherboard is using the chipset
ATI RADEON XPRESS 1150 (RS485+SB600)

  [http://tinyurl.com/yewsxt](http://tinyurl.com/yewsxt)

I tried install from the 6.10 AMD64 installation ISO.
Beside some glitches with video solved by resyncing
the Viewsonic VX2000 a couple of times I do get to the
booted live environment and can start the installer.
But no disks are found by the installer. They are visible
in BIOS, I can see them assigned master/slave on the
second and third (virtual?) controller. I can't find any
obvious "compatibility" setting I can change in BIOS.

So how do I get the installer to recognize these SATA
drives? I read something about this hardware being
supported in 2.6.17-something, are there installation
ISO images with newer kernels? Or is there a way to
load a driver from a CD or floppy in the installation
process? Should I then use the "alternate" image?

I can put in an IDE disk temporarely, would that help?
Install Ubuntu there first, rebuild a new kernel, and
do some sort of install from that running Ubuntu to
the new disk, with this new kernel? Is this documented
somewhere?

Thankful for any help or pointers, I was so looking
forward to run Ubuntu,

kent

---

### Post by boortz on 2006-11-25
Just a followup status. This motherboard, Sapphire
Pure Elements PE-AM2RS485M-2 is just not for Linux.
Support was not very helful, I asked for hints, asked
what Linux distribution and version they have
successfully installed, but only got "it works with
Linux", and when asking for BIOS upgrades the answer
"you can try upgrade the BIOS". They did suggest to set
SATA in IDE compatibility mode, but it already was.

I tried Ubuntu 6.10, tried Fedora Core 6 and SuSE 10.2
beta. Ubuntu could not see the SATA disks, independent
on BIOS setting in IDE mode or AHCI, with and without
nolapic and noapic. Both FC6 and SuSE faled to install,
one with a kernel panic about spinlocks, the other with
the problem that no disks are found.

I could actually install FreeBSD 6.1, installer could
see disks just fine. But when rebooting with a SMP
kernel it would not let me use both CPUs :-(

I now have given up and replaced this motherboard with
a ASUS M2NPV-VM. Just installed Ubuntu and so far no
other problem than that I had to give the "nolapic and
noapic" as suggested in this forum, else it would hang
during boot of the live CD. Boot after install is fine,

kent

---

### Post by vikesh on 2006-12-11
Hi there

I also have a Sapphire motherboard with the same chipset ATI® RADEON XPRESS 1150 ATI RS485+SB600. The serial ATA drive is not detected with Ubuntu 6.06.1 or Ubuntu 6.10. Debian ETCH, and 64Studio have similar problems. The interesting thing is that knoppix 5, Gentoo and WinXP :(  detect the SATA drive. 

Loading/unloading various modules as described on some other forums as welll as playing around with the BIOS SATA driver identification (IDE, RAID etc) did not help

Anybody know how to get ubuntu to detect the SATA drive ?

What does knoppix and gentoo do differently to detect the drive?

I'm actually helping out a "new linux user" with this one and wouldn't want her to get put off in the installation phase.

Thanx for any help
Vicki

---

### Post by atconsul on 2007-01-13
This is not an answer, I'm afraid, as much as it is more data and more questions.

 I've played with a Sapphire Pure Elements PE-AM2RS485M-2 board as well. I confirm that it hates FC6. It will install FC5 32 bit from iso's but I needed to pin the kernel at 2.6.15-1.2054 when upgrading things to avoid getting the spinlock barf already reported here, and the kernel doesn't support ide dma as far as I can see (it refuses to accept hdparm -d1). I'm not using SATA, just plain old IDE so no, IDE won't help much (well, you can boot from it). I didn't risk a 64bit disti on the grounds that it was likely to be more difficult to get a full set of function together. Not sure if that's such good judgement after all.

 No DMA is about as handy as a button on a shoe. We're talking mid-1980's I/O throughput so,  yes, it does look like it's no good for Linux at the moment.

But again I confirm that it can happily run XP Pro like a good modern machine. So let's not point too many fingers at the Sapphire design (although from what's reported here their after-sales support is no better than you might expect). I have this down to problems with Linux kernel support for the ATI SB460 and SB600 chipsets. My lspci listing confirms that Linux doesn't know what's attached. Anyone agree my diagnosis? Anyone know any Radeon Express motherboard that runs Linux properly? Ironically I've got the actual display working just fine for me (TV out, PAL frame rates to RGB etc) I've no idea frankly what's in the ATI South Bridge that isn't compatible with the Intel set enough to offer DMA at least. I'm just not plugged into the right sources. There's no source data from AMD/ATI in the end user domain at all about their chipset products AFAIK. What does lspci reveal with gentoo, knoppix etc?

 Vikesh cites "Loading/unloading various modules as described on some other forums."  I haven't got that far in my information trawl. What else is being suggested? I see ( from kernel make menuconfig etc ) that there are choices for SATA, but nothing that looked like it really knows what an SB460 might be.

---

### Post by atconsul on 2007-01-17
OK THIS is answer.

It turn out I was only a few lines of typing (but hours of research and machine time) away from a solution, which was probably working some time in Dec.  

From reading the driver source I doubt if anything prior to 2.6.19.rcsomething cuts it to make the disks work properly for most people.

The ATI chipset looks as if it's supported OK in late versions of the kernel. There's still quite a lot of fiddling about going on, I detect, but I got lucky with 2.6.20rc5 by doing:

git clone git://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux-2.6.git linux-2.6

(allow to cook for several hours)

make menuconfig

(a couple of options for ati and sata if you have it)

make

(could also be a slow cooker)

make modules_install

(deep frying time)

make install

(have a cup of something)

That's it. Everything I want works now, including alsa sound right off the install, except that for me at least there seems to be some problem at the make install stage with building the initrd image: it doesn't deal with swap properly if it uses a label in fstab, which needed a hand edit. I expect I'd still need the ati fgrlrx driver for TV out but I see someone's working on that, too.

It turns out the lspci test isn't a reliable guide to whether the kernel knows about your devices, because lspci isn't connected to the kernel, it's just looking up a disti table of known pci stuff. So after all this lspci still doesn't know about the ATI chips. It doesn't matter. 

Also at early boot I still get 
PCI: Cannot allocate resources region 1 of device 0000.00.14.0 
but that doesn't seem to matter either. I think it must get dealt with later in the boot.

So there is a route forward. Sooner or later this code is going to turn up in an iso disti. Until then you can get yourself running this way using ide to boot an available disti, or make your own iso if you know how. Sure I don't. 

Oh, yes. Amongst other jewels I uncovered on my trawls. Apparently I was right about information in the public domain about the ATI chipset: there isn't any, by intention. They don't publish data sheets, it seems, unless you want to convince them that you're a credible business partner making a commitment to buy shedloads of chips. In my day if you didn't publish data sheets you wouldn't sell any chips. It's a brave new world, innit? Still at least we've got the Linux kernel heroes out there doing it for us.

---

