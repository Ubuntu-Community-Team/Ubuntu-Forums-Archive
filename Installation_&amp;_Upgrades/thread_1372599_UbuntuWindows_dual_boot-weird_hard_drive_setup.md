---
title: "Ubuntu/Windows dual boot-weird hard drive setup"
date: 2010-01-04
forum: Installation &amp; Upgrades
---

### Post by dstrout on 2010-01-04
I am trying to dual boot Windows and Ubuntu on a 60-gig hard drive. (See [this PDF]("http://www.seagate.com/support/disc/manuals/ata/100221374a.pdf") on the manufacturer's website for more infomation on the HD.)  However, the hard drive is set up rather strangely.  Because I am using a machine with an old BIOS, the computer will not actually boot with a hard drive of this size attached.  I therefore have to set the jumpers to make the hard drive run in a limited capacity mode, where only 32 gig is available .  (For more information on the jumpers, see page 32 of the PDF.)  I currently have Windows installed on the hard drive, which I am able to do because it can only see the 32 gig.  When trying to install Ubuntu, however, I run into a problem, because Ubuntu for some reason is able to see all 60gigs of the HD.  It therefore attempts to install on the remaining ~28gig of the hard drive, which is beyond what the BIOS can see.  Therefore when I boot, I am unable to boot Ubuntu.

If anyone know how to work around this situation, or if I am unclear in some way, please reply.

---

### Post by tachuela on 2010-01-04
Sometimes you can get away with making a small /boot partition at the beginning of the drive (200MB)

---

