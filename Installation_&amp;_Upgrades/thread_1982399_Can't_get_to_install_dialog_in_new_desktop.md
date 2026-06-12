---
title: "Can't get to install dialog in new desktop"
date: 2012-05-18
forum: Installation &amp; Upgrades
---

### Post by FinalAlias on 2012-05-18
I just built a new pc, and am trying to install ubuntu (non-dual-boot).  I can get to the live cd's initial boot-up screen just fine where it shows the options such as "Install Ubuntu", "Check Disk for Errors", "Test Memory", etc. but when I try to either test ubuntu from the live cd or install ubuntu, or even "Check Disk for Errors", the screen will go black and nothing happens.  I can get to the "Test Memory" screen, though, and did a successful pass with that.

Here's all the variations that I've tried so far, all with the same results:
-Ubuntu 12.04 amd64 from both cd and flash drive, with and without video card
-Lubuntu 12.04 amd64 from both cd and flash drive, with and without video card
-Ubuntu Minimal 12.04 amd64 from both cd and flash drive, trying both "Install Ubuntu", -"Expert Install", "Install from command line", and "Expert Install from command line".

I've doublechecked the hashmaps for these iso's too.

For the flash drive boots, I've tried both Universal USB installer and UNetBootin.
For UNetBootin, with Ubuntu and Lubuntu, instead of a black screen, I get the previous screen at 1/4 size in the upper left corner, and cursor blinking at the bottom and then freezing.
Sometimes with other conditions mentioned above, instead of an entirely black screen, I will also get a blinking cursor for a few seconds and then it will freeze.

Going back through my old cds, I tried and was able to successfully boot and install Ubuntu 10.04 32-bit on this pc.  Vista 32-bit also installs ok.  However, this is a new Ivy Bridge Corei5 pc with 8 GB of RAM, so I really want 64 bit.

Something else that was partially successful was installing Salix distro.  The install dialog went through ok, but after install, upon reboot, I get "LIL" on a black screen, then it starts printing a bunch of repeating characters, then freezes. I don't know if that provides any extra insight or not, so I figured I'd mention it.

Here's my pc specs in case that helps:
Ivy Bridge Core i5 3570K cpu
Kingston DDR3 8 GB RAM
EVGA GeForce GTX 550 Ti video card
ASROCK Z77 PRO4 1155 ATX motherboard
PCPOWER SILENCER MKIII 600W psu
CRUCIAL 128G SSD M4 2.5 SATA6G hard drive hooked up via sata3 port

I do have various other hard drives hooked up, but I tried the installs above with and without them hooked up too.

As you can see, I've been spending a lot of time trying to get this to work, and it would be a shame to have to give up and go with windows 7, so I'd really appreciate any help.

Thanks in advance.

**EDIT** Also I forgot to mention, I tried a few of the above cd/flashdrive "Try Ubuntu from Live cd" runs on my old laptop, and they ran fine.

---

### Post by 2F4U on 2012-05-18
Did you try using nomodeset as a grub kernel parameter?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by FinalAlias on 2012-05-18
Yes, I just tried that with ubuntu and lubuntu cds, and it's still going to a black screen with a blinking cursor.  The cd drive spins for a few seconds and then stops...

besides, I had already tried command-line install, which shouldn't use the video modes anyway, right?

**EDIT** Oh wait, now the check disk option works with the nomodeset.  I'm going to let it finish checking the disk and try installing again.  Not sure why nomodeset install didn't work when I tried it just now, but it's worth doublechecking

**EDIT2** Nope, still just a blinking cursor when I select Install Ubuntu while selecting nomodeset.  The disk check found no errors, though, which is nice, I suppose...

---

### Post by FinalAlias on 2012-05-18
Ok, I took out "quiet" from the boot options, and now it says something like:
usb2-1-8: new full-speed USB device number 6 using ehci_hcd
ata7.00 exception Emask 0x52 SAct 0x0 SErr 0xffffffff action 0xe
 frozen
ata7: SError: { RecovData RecovComm UnrecovData Persist Proto HostInt CommWake 10B8B Dispar BadCRC HandShk LinkSeq TrStaTrns UnrecFIS DevExch }
ata7.00: failed command: IDENTIFY PACKET DEVICE
ata7.00: cmd a1/00:01:00:00:00:00/00:00:00:00:00:00/00 tag 0 pio 512 in
res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x56 (ATA bus error)
ata7.00: status: { DRDY }
ata7.00: hard resetting link

Then it stops and nothing else.

---

### Post by FinalAlias on 2012-05-18
It must have been my cd player.  I've disconnected it, and now I can start the install dialog through usb.  
RESOLVED!
:)

...but how do I use my cd player now once it's installed? I know it works 'cause I have installed vista on this pc in the past, and it worked just fine...

---

