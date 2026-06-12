---
title: "booting to a formatted drive"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by pabloantonio on 2011-12-04
Hi there,

I'm trying to load edubuntu onto an old laptop from work. The hard drive has been wiped clean of all data because of licensing issues. I've created a usb bootdisk but I keep getting BootMgr is missing, which it would be as the drive has been formatted. Any ideas on how to progress?

Thanks

---

### Post by bluexrider on 2011-12-04
this should help you.

**Edubuntu 10.10 Installation Guide**



[http://edubuntu.org/documentation/10.10/installation-guide](http://edubuntu.org/documentation/10.10/installation-guide)

---

### Post by darkod on 2011-12-04
Sounds like it's trying to boot from the hdd, hence the bootmgr missing. Are you sure it can boot from the usb stick? And that you are actually booting from it?

You might need to play with the boot options a little.

---

### Post by pabloantonio on 2011-12-04
I suspect that the laptop is too old to boot from the USB. Is it possible to put the hard drive in a cradle and put edubuntu onto it from another machine? My newer laptop supports booting from USB. :confused:

---

### Post by darkod on 2011-12-04
It will probably complain about few bits and pieces but it should work if you install it connected to another computer. Especially if that's your only way.

Connect it to another computer, boot with the stick and install onto the HDD in question. Make sure you install grub2 on the same HDD.

The laptop should boot unless you run into some issue with video driver or similar. Without being able to boot that laptop with a stick or CD you can't try anything if it doesn't boot right away. But give it a shot.

Most important is the video driver. If the system boots you can always add drivers for toehr hardware later. But if you can't see anything on the screen it's not easy. :)

---

### Post by pabloantonio on 2011-12-04
Thanks Darkod,
 
I'll give it a go. Is Grub 2 a standalone or is it in the edubuntu bundle?

---

### Post by darkod on 2011-12-04
I actually wrote grub2 automatically, I've never used edubuntu. But it has to have a bootloader of course, and I guess it's grub2. In any case, in general terms, make sure the bootloader goes to the same HDD. It's never a stand alone, the new system will need to boot with something. :)

---

