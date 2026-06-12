---
title: "ubuntu mint run from a flash drive"
date: 2017-08-09
forum: MINT
---

### Post by teslar2 on 2017-08-09
Hi guys, dont know if this is the right place to post

I tried the Mint forum on this topic but the post was dated 2012 and clearly not latest info particularly as 64G thumb drives are easily available

So may I ask for the latest opinion on the best way to run linux (and some of its regular apps like ?office) on a thumb drive.  Can I go up to another Windows PC, plug in and run from usb?  Say somewhere like a library (though there may be other restrictions preventing this. Clearly I need "persistance" to store my data and configurations.  I read that you can partition a thumb drive?

if this has already been addressed pls give me links - it seems an obvious question:o

Robin

---

### Post by yancek on 2017-08-09
With a 64GB flash drive, you should be able to do a full install of both, maybe 20GB for each system and the rest for a shared data partition.  You would use a DVD or different flash drive to create a bootable medium for the install and then select the drive/partition on the flash drive to install.  Install the Grub bootloader to the MBR of the flash drive and be careful you do not install to an internal drive.  This should enable you to boot it from multiple computers.  That's about as specific as I can get with the information you posted.

---

### Post by Bucky Ball on 2017-08-09
Welcome. There are a few caveats to what yancek has posted above. It's not quite as simple as that. What if you install in UEFI mode on the USB and the machine you're trying to boot the USB on is set up in BIOS mode, doesn't use UEFI? Or vice versa? The USB will not boot without some considerable stuffing about in the BIOS, and possibly beyond.

You can get around this by installing using a method that can pick up either BIOS or UEFI mode, as far as I know, but that's about all I know about that. No experience and no idea. Just seen other people talking about such a setup here for situations like yours.

Then there's video drivers. You install to USB, install the drivers for your video card, move to another machine that has a different vid set up and you don't have the drivers for it. This will lead to further stuffing around which may achieve success, may not. May take five minutes, may take three hours.

Wireless? Same thing. You will have the drivers for your wireless card installed in your USB OS. What about when you don't have the wireless drivers for another machine? No wireless. This one is more difficult as the wireless card in the other computer may not even work in Linux, let alone have a driver.

So, it is not as easy as installing persistence to a USB and away you go on any machine. There are certainly other things to consider. Someone with experience doing what you are trying to do will hopefully jump in and lend a hand, but just thought I'd mention these things.

Good luck with it. ;)

---

