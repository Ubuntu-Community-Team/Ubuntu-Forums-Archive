---
title: "gParted will not part my Gs!"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by Curtiee on 2009-12-26
Okay, I decided I was going to install Ubuntu, and remove Windows 7. I was then going to REINSTALL Windows 7 afterwards, and have a dual boot.

But now, because I've installed Ubuntu across my ENTIRE HDD, I cannot split it. 

So I went to just try install Se7en again, but now it will not boot from CD.

What should I do?

Cheers,
Curt

---

### Post by taurus on 2009-12-26
Check your BIOS to see if CD/DVD drive is still the first option in the boot order.

Normally, you would install windows first, then Ubuntu, not the other way around because installing windows after Ubuntu will wipe out GRUB.  Then, you have to reinstall GRUB again if you want to get back to your Ubuntu.

---

### Post by mattmyers83 on 2009-12-26
You can try pressing f12 at boot as well.  Thats usually the boot menu on most bios's

---

### Post by Curtiee on 2009-12-26
> **taurus said:**
> Check your BIOS to see if CD/DVD drive is still the first option in the boot order.

Normally, you would install windows first, then Ubuntu, not the other way around because installing windows after Ubuntu will wipe out GRUB.  Then, you have to reinstall GRUB again if you want to get back to your Ubuntu.
I have done that. I've set the Toshiba CD/DVD something or other to the top one, and then USB CD/DVD to the second one in the boot order, but it still doesn't boot. I also had difficulty booting the Ubuntu 9.10 disk, and had to install the booting help software. I was going to partition Windows, and install Ubuntu, like I have before, but my HDD is a bit messed up due to the fact I did previously have an Ubuntu partition. On EASEUS Partition Master, it called that partition *:\, and I did not want to delete that one... It also wouldn't perform multiple processes, as I had to use the Pro Demo with it being a 64 bit install. But yeah, I realised I'd have to install Ubuntu AGAIN afterwards. 

> **mattmyers83 said:**
> You can try pressing f12 at boot as well.  Thats usually the boot menu on most bios's
Like I said above, I've done that, and it just won't boot >: (

---

### Post by taurus on 2009-12-26
Sounds to me like it has nothing to do with Ubuntu but either your BIOS or your CD/DVD drive.  Maybe you should see if there is a newer BIOS for your machine that you can update!

---

### Post by Curtiee on 2009-12-26
> **taurus said:**
> Sounds to me like it has nothing to do with Ubuntu but either your BIOS or your CD/DVD drive.  Maybe you should see if there is a newer BIOS for your machine that you can update!

I shall have to do that indeed... My internet's playing up though, some pages it will load, most others it wont. Ubuntuforums work fine, but then others either load from cache or not at all. Oh well.

I may try an external optical drive we have floating around the house somewhere. :)

---

### Post by Curtiee on 2009-12-26
> **Curtiee said:**
> I shall have to do that indeed... My internet's playing up though, some pages it will load, most others it wont. Ubuntuforums work fine, but then others either load from cache or not at all. Oh well.

I may try an external optical drive we have floating around the house somewhere. :)

Well well well, it appeared to do something, then just loaded up Ubuntu. It did definitely boot from the external DVD Drive, but to no avail. 

What do? ):

Edit: "This disc contains a "UDF" file system and requires an operating system
that supports the ISO-13346 "UDF" file system specification." - Does Ubuntu support UDF? :x

---

### Post by Curtiee on 2009-12-26
Nope, it will not boot from disk. I even tried installing PowerISO through WINE, but it just told me the virtual drive manager was not installed correctly, so I have no other ideas... Can anyone help me and my predicament? ):

---

### Post by darkod on 2009-12-26
> **Curtiee said:**
> Nope, it will not boot from disk. I even tried installing PowerISO through WINE, but it just told me the virtual drive manager was not installed correctly, so I have no other ideas... Can anyone help me and my predicament? ):

If you have decided to wipe the drive and install win7 then ubuntu, boot with ubuntu cd, Try Ubuntu option, open Gparted and delete all partitions. Then create one single primary ntfs partition for your win7 system partition, select the size as you want.
Install win7 on that partition. Then just install ubuntu with the Use Largest Available free space option. That would be the easiest approach I think.
As for not booting from cd/dvd, you have to sort that out obviously. Another option would be to create bootable usb stick and boot with that.
I haven't used EASEUS or similar, since you have the ubuntu cd stick with Gparted, that's a very good partition manager. And as you probably already figured out, if planning to dual boot (regardless which OS will be installed first) it's a bad practice to let one OS take the whole drive because then you have to create space for the other OS.

---

### Post by Curtiee on 2009-12-26
> **darkod said:**
> If you have decided to wipe the drive and install win7 then ubuntu, boot with ubuntu cd, Try Ubuntu option, open Gparted and delete all partitions. Then create one single primary ntfs partition for your win7 system partition, select the size as you want.
Install win7 on that partition. Then just install ubuntu with the Use Largest Available free space option. That would be the easiest approach I think.
As for not booting from cd/dvd, you have to sort that out obviously. Another option would be to create bootable usb stick and boot with that.
I haven't used EASEUS or similar, since you have the ubuntu cd stick with Gparted, that's a very good partition manager. And as you probably already figured out, if planning to dual boot (regardless which OS will be installed first) it's a bad practice to let one OS take the whole drive because then you have to create space for the other OS.

I cannot get this to boot at all. I was wondering about deleting the entire HDD, but then I fear I would be left with a brick knowing my luck. 

Nothing seems to be going right for me, at all. Your post makes complete sense, I understand how and why to do it, but nothing will boot at all. What should I do? ):

---

### Post by darkod on 2009-12-26
If I understood correctly your ubuntu is booting at least. Why don't you try the usb stick option?
Open USB Startup disc creator in System-Administration, use the downloaded ISO and create the bootable usb stick.
Set the USB to boot first in BIOS and see how it goes.
You definitely need to solve this and make your pc boot from cd or usb. For future use too.

---

### Post by Curtiee on 2009-12-27
> **darkod said:**
> If I understood correctly your ubuntu is booting at least. Why don't you try the usb stick option?
Open USB Startup disc creator in System-Administration, use the downloaded ISO and create the bootable usb stick.
Set the USB to boot first in BIOS and see how it goes.
You definitely need to solve this and make your pc boot from cd or usb. For future use too.

That's what I tried doing, but it just will not boot AT ALL.

The iso I have for Windows 7 says that *"This disc contains a "UDF" file system and requires an operating system that supports the ISO-13346 "UDF" file system specification."* which I'm not sure if Ubuntu supports or not...

I also set the USB to boot first, but it just refuses to do anything when booting from CD/DVD or even USB stick... :/

---

