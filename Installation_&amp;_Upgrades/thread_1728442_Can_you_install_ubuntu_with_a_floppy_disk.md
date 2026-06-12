---
title: "Can you install ubuntu with a floppy disk?"
date: 2011-04-13
forum: Installation &amp; Upgrades
---

### Post by eckeroo on 2011-04-13
Hello,

My A7M266 motherboard does not allow boot from USB. The options are Floppy, HDD, CD-ROM and LAN. I'm not familiar with a LAN install, but I know the motherboard itself does not have onboard LAN but does have a PCI LAN card installed.

PATA CD/DVD drives are getting harder to come by. So assuming these become extinct, is it possible to initiate an Ubuntu USB install from a floppy boot?

---

### Post by poodoopealeoaph on 2011-04-13
i'm not sure that it would work if you tried to install with floppy discs. You would have to fight to get all of the information loaded onto a floppy and even then the boot loaders might not be installed correctly. That and you would have to use like 20 or more floppy disks to get the whole process to work and with that many disc changes, I'm not sure the installer would stay going...

---

### Post by avatarmonkeykirby on 2011-04-13
I'm sure it's possible, if your computer can still boot from floppy there should be some way to do it. The only problem is that floppies are dated and there hasn't been a specific installer made for them. I imagine that this is because the live disk is aproximately 690 MB spit along 1.5 MB floppies means you need 460 floppy disks.

Sorry I can't directly answer your question as to how to do this with floppies, but your best bet would be to use a CD.

---

### Post by oldfred on 2011-04-13
I have not used it but some have had it work and others have had issues.

Boot USB or PCMCIA (new)
[http://www.plop.at/en/home.html](http://www.plop.at/en/home.html)

This only boots grub, but from grub you can do a lot if you know how.
Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

---

