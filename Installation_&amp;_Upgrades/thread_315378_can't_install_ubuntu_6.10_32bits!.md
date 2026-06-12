---
title: "can't install ubuntu 6.10 32bits!"
date: 2006-12-09
forum: Installation &amp; Upgrades
---

### Post by merlin77 on 2006-12-09
Hi all,

For a long time I've been using ubuntu (4.xx, 5.10, 6.06).  Now I've come to install 6.10, but the 32bit version does not install, and the 64bit does!

After the boot screen I get kernel panic - not syncing!  I've tried every option like ida=nodma noacpi nolacpi, but nothing works.

My HW: Athlon 64, 512MB, VIA chipset.

Can anyone help?

Thanks

---

### Post by compwiz18 on 2006-12-09
Run the **Check CD for defects** option at the CD boot screen - it is possible that the CD is corrupt, or not working.

---

### Post by compwiz18 on 2006-12-09
You could also just erase and reburn the CD, this might fix it.

---

### Post by DWright on 2006-12-09
I'm sure you have checked, but I've got to ask: Have you checked the MD5SUM on the 32bit CD? ...maybe it just need to be downloaded again.

...and I also have to ask: Why? If you have a 64bit Athlon, why install a 32bit operating system?

---

### Post by merlin77 on 2006-12-11
Thanks for helping..

First of all I don't think it's the CD.  I have burned the CD again (2 more times) from different images I've downloaded over net (and I have also tried a DVD version of the 32bit dist).

Also, the same cd's do work on different machines, and I have also checked them in VMware (on my machine).

However, the 64bit boots fine!

And the reason I don't want to use the 64bit version is because it's less supported with drivers and I get more crashes with it. I prefer the 32 bit version.

Can anyone help me install it?  Anyone has any idea?

---

### Post by maxg on 2006-12-16
I have the same problem with a new installation on a P4 512Mb, the installation phase whent okbut when I re booted the system I am geting the following error:

[<c01041df>] error_code+ 0x4f / 0x60
<0> kernel panic-not syncing:fatal exception in interrupt
I get the same error from the live CD, reading around in the forum it look like there have a lot of this error reported, any one managed to solve this type of error?
Thanks

---

### Post by jlc on 2006-12-20
Try the alternate cd

[http://ftp.wayne.edu/linux_distributions/ubuntu/6.10/ubuntu-6.10-alternate-i386.iso](http://ftp.wayne.edu/linux_distributions/ubuntu/6.10/ubuntu-6.10-alternate-i386.iso)

---

