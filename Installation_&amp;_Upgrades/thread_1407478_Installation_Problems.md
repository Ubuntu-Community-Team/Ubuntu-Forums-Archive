---
title: "Installation Problems"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by Taganini on 2010-02-15
I am new to Ubuntu and I was trying to install it on my computer that actually runs WIndows Vista. I was trying to setup Dual boot.

I downloaded Ubuntu 9.10 64bits image file and burned a CD. Then I can boot with Ubuntu and start installation but it says that the CD is corrupted. I downloaded again several times and burned couple diferent CD types with lower speed possible, and the problem still. When I burned the CDs I verified them and I can see the files on windows ambient. Not sure what I am doing wrong.

Is that any problem burning the Ubuntu image CD on windows ambient?
Can I install Linux from a Pen drive or a external hard drive?

Thank you all in advance
Regards

---

### Post by Mencarta on 2010-02-15
What kind of processor do you have? An Intel Pentium 4, AMD Athlon, etc.

---

### Post by Taganini on 2010-02-15
Sorry I missed that!
HP Pavillion dv7 (4Gb RAM w/ Intel Centrino Dual Core 2.5GHz 64bits)
Thanks

---

### Post by Mencarta on 2010-02-15
Intels are generally 32 bits. AMDs is generally 64 bits. Try the 32 bit version.

---

### Post by darkod on 2010-02-15
It shouldn't matter whether you burn the cd on windows.
Yes, you can install from usb stick. If you are creating it on windows it's best to use the free program unetbootin and use the ubuntu ISO to create a bootable usb stick. Format the stick as FAT32 first.
When unetbootin finishes ignore the question to reboot, just close it.

Then open the stick and to enable the ubuntu menu do:
1. In the root folder rename syslinux.cfg to syslinux.old
2. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

That will enable the standard ubuntu menu.

---

### Post by Taganini on 2010-02-25
Darko

It worked fine!! Thanks a lot!
Antonio

---

