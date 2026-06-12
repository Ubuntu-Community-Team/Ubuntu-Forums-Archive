---
title: "considering dual-boot (Hardy/Puppy), have questions"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by mailman1175 on 2009-12-05
My wife's AspireOne is presently running Hardy. Hers is the 512MB RAM/8GB SSD version, so Hardy's a bit slow sometimes, but it works, and has been very stable (when I don't futz with it, anyway), thanks in no small part to a lot of help I've gotten from the Ubuntu community.

I started looking into Puppy Linux the other day, thinking its light weight and small footprint might be just the thing for the middling hardware that comes in these netbooks. I don't want to dump Hardy ('cause if I've learned anything about using Linux on a computer that's not a dedicated test-bed, it's "if it ain't broke, don't fix it"). Obviously, Puppy's light enough to run off a USB stick, and that's what I originally had in mind. But, it occurred to me this morning that it might be small enough I could dual-boot it with Hardy.

I've searched a bit, but haven't found quite what I'm looking for. Really, the first question I have is, "Do I have room?" That is, the 8GB SSD has 2.4GB free. A Puppy install should only be a couple hundred MB, but let's say I set up a 500MB partition for it. Is that enough room to allow for Hardy updates, etc? We use an external hard drive and an SD card for most file storage, so the SSD is pretty much dedicated to the OS.

Now, assuming I've got room on the SSD for a dedicated Puppy partition, and assuming I can use the Puppy MasterInstaller (or whatever it is they call it; I can't remember) to get Puppy installed to that partition, is Ubuntu's GRUB going to recognize the Puppy install? I assume I'm going to have to edit menu.1st, or is GRUB "smart" enough to recognize another boot partition? How do I get some kind of delay in the boot process so I can make the choice between OS's?

So really, this is a "dual-booting for dummies" kind of deal. I'm not a *total* n00b, but am not a guru by any means.

TIA

---

### Post by zvacet on 2009-12-05
You can shrink your ubuntu partition to make place for Puppy.AFAIK full install take ~1,2GB so you can try frugal install.See [here.]("http://puppylinux.org/main/index.php?file=Manual-English05.txt")I believe that you will find on Puppy pages how to add Puppy to the grub and not overwrite it.

---

### Post by mailman1175 on 2009-12-05
> **zvacet said:**
> You can shrink your ubuntu partition to make place for Puppy.AFAIK full install take ~1,2GB so you can try frugal install.See [here.]("http://puppylinux.org/main/index.php?file=Manual-English05.txt")I believe that you will find on Puppy pages how to add Puppy to the grub and not overwrite it.

Can I use gparted to shrink the Hardy install? If not, how do I go about non-destructively adding a partition?

Thanks!

---

### Post by zvacet on 2009-12-05
You can shrink partition with your Ubuntu live CD or with [Gparted live CD.]("http://gparted.sourceforge.net/") I never done it but I think you can do it with Puppy too,but I will download gparted live CD because it is a good tool.

---

