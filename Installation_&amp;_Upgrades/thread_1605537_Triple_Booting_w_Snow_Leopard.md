---
title: "Triple Booting w/ Snow Leopard"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by xTLx on 2010-10-25
Hey there. Currently my Toshiba laptop is dual-booted with windows 7 and Ubuntu 10.10 and I think I may try and triple-boot it with Snow Leopard. I'm not too familiar at all with hackintoshes so, how should I go about configuring a partition for the OS?

Also: is there any known problems running windows and a mackintosh OS? :confused:

If someone can give me some insight here I can also provide my computer's specs.

---

### Post by nynepac on 2010-10-25
You're going to want to check out a place like insanely mac for something like that . You'll likely need Grub to manage the linux bit and then use the Chameleon bootloader to manage the whole bunch of them.

---

### Post by arrimapirate on 2010-10-25
In order to install OSX you need to format your hard drive as GPT (Guid Partition Table) This will require you to literally wipe everything off your hard drive. There is a workaround to allow you to install on a MBR formated HDD but i could never get it working. 

If you are willing to try this (make a dd backup first) you will need gparted with all the hfs+ extras installed to carve out you OSX partition. The you have to boot a special cd that will trick OSX into installing onto a non-apple approved computer. Then you have to install OSX as usual, install needed drivers (kext files) for you hardware if they exist, then fix your bootloader to let you actually boot it.

I can help a lot more if you still want to do this knowing all the risks and trouble it will be.

---

### Post by srs5694 on 2010-10-25
> **arrimapirate said:**
> In order to install OSX you need to format your hard drive as GPT (Guid Partition Table) This will require you to literally wipe everything off your hard drive.

Actually, it's possible to convert MBR to GPT non-destructively using [GPT fdisk.](http://www.rodsbooks.com/gdisk/) That said, the moderators here frown upon discussions of running OS X on non-Apple hardware. You'll have to take such questions to Hackintosh-specific forums.

---

### Post by arrimapirate on 2010-10-25
> **srs5694 said:**
> Actually, it's possible to convert MBR to GPT non-destructively using [GPT fdisk.](http://www.rodsbooks.com/gdisk/) That said, the moderators here frown upon discussions of running OS X on non-Apple hardware. You'll have to take such questions to Hackintosh-specific forums.

I wish i had known that when i tried this (had to backup 600gb of stuff) I wasnt aware that this was a touchy subject so ill just point you toward this excellent tut i just saw posted on lifehacker:
[http://lifehacker.com/5672051/how-to-build-a-hackintosh-mac-and-install-os-x-in-eight-easy-steps](http://lifehacker.com/5672051/how-to-build-a-hackintosh-mac-and-install-os-x-in-eight-easy-steps)

---

### Post by xTLx on 2010-10-25
Just out of curiosity does anyone know the laws  in most countries or parts of apple's user agreement that would technically make using Mac's OS on other machines other than their own illegal? It's really kind of odd, although it's quite effective, because it directs their OS almost completely to their own products.

---

### Post by xTLx on 2010-10-25
> **arrimapirate said:**
> I wish i had known that when i tried this (had to backup 600gb of stuff) I wasnt aware that this was a touchy subject so ill just point you toward this excellent tut i just saw posted on lifehacker:
[http://lifehacker.com/5672051/how-to-build-a-hackintosh-mac-and-install-os-x-in-eight-easy-steps](http://lifehacker.com/5672051/how-to-build-a-hackintosh-mac-and-install-os-x-in-eight-easy-steps)

Oh and hey great article! It looks as if Mac has been using Intel Processors... My i7 should do magic.

But out of curiosity and I'm VERY inexperienced on this subject, could I use a USB external hard drive as a hard drive to boot an OS from? Since I'm using a laptop it's not really possible to have two internal ones. Or is possible to configure one to act as an internal one?

---

### Post by arrimapirate on 2010-10-25
> **xTLx said:**
> Just out of curiosity does anyone know the laws  in  most countries or parts of apple's user agreement that would  technically make using Mac's OS on other machines other than their own  illegal? It's really kind of odd, although it's quite effective, because  it directs their OS almost completely to their own products.

Actually all Macs have whats called a  Trusted Platform Module chip (or TPM for short). When the OSX dvd boots, it checks the TPM chip on the motherboard. TPM chips are only on apple mobos, so if it doesnt find one it wont boot. Thats why you need the iboot disk. 

> **xTLx said:**
> But out of curiosity and I'm VERY inexperienced on this subject, could I  use a USB external hard drive as a hard drive to boot an OS from? Since  I'm using a laptop it's not really possible to have two internal ones.  Or is possible to configure one to act as an internal one?

You can install directly to a usb hard drive. Since i only have an iso i made of a friends OSX dvd i boot the iso off the external drive (its too big for a normal dvd) and then install it on the same drive.

---

### Post by xTLx on 2010-10-25
Wait, so what your saying is I can install an OS onto an external hard drive? I mean an obvious disadvantage would be it running slower (having to be attached by a USB cable) but I can boot a mac OS on an external hard drive then?

---

### Post by arrimapirate on 2010-10-26
> **xTLx said:**
> Wait, so what your saying is I can install an OS onto an external hard drive? I mean an obvious disadvantage would be it running slower (having to be attached by a USB cable) but I can boot a mac OS on an external hard drive then?

Yes. The speed difference isnt really that noticeable. OSX is built to run on slow hardware anyway (look at the specs of a MBP, they run about as fast as my 2005 laptop) You can also run Ubuntu from an external or set up a multi-boot on it you can take anywhere. The only os that i havent tried to run this way is Windows

---

### Post by xTLx on 2010-10-26
Hey thanks... I think I'm gonna try this out

---

### Post by arrimapirate on 2010-10-26
Yepp no problem. Good luck!

---

