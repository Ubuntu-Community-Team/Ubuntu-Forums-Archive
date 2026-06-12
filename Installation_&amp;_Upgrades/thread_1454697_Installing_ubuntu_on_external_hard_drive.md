---
title: "Installing ubuntu on external hard drive"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by Leathermanwave on 2010-04-15
I originally had windows vista on my pc and then I installed ubuntu on a partition, then I decided that I wanted ubuntu to be installed on my external hard drive so that it can be run on any computer, so I installed linux on my external hard drive then I deleted the linux partitions on my internal hard drive, then to further complicate thing I decided that I wanted grub un-installed because it ran slow when reading off of a external hard drive and just use dell's normal boot selector so I inserted my vista cd and ran /fixmbr and /fixboot which deleted GRUB and returned the default booting into vista, now my problem is that when I try to run linux by using dell's boot devices options It won't run and says that 'there is no boot manager installed".

   My question: is it possible to have ubuntu on a external hard drive so that it can be booted from any computer? if so, how can I do it?

---

### Post by SkullTraill on 2010-04-15
Don't bother asking here. I had the same question, they ignored me. But I figured it out myself!

Connect your USB hard drive, and boot up with the installation CD inside. Then when installing choose "Guided - Use entire disk" and choose your external hard drive. Then continue setup until you see the "Summary" of the installation, at that point, click "Advanced" and make sure you install "GRUB" to your EXTERNAL hard disk. and then install Ubuntu, and make sure you set up your BIOS so that it boots from the EXTERNAL hard disk first.

If you need more help, PM me or add me on msn : skulltraill<at>live<dot>com

---

### Post by jtcitrus on 2010-04-22
This is essentially what I want to do.  I have a Toshiba Laptop that wont boot from USB and the CD/DVD drive is fails 50% of the way through install.  (I've tried different distros/discs... always fails.)  So... I want to plug the laptop hard drive into a usb enclosure and intall ubuntu, THEN move it back to my Toshiba laptop internally.  We'll see....

---

### Post by jerrrys on 2011-06-08
you said the vista word.  vista and gparted are not compatible.  use a window partition manager only.  and this only applies to vista.

---

### Post by linuxinstalledfromhdd on 2011-06-08
> **jtcitrus said:**
> This is essentially what I want to do.  I have a Toshiba Laptop that wont boot from USB and the CD/DVD drive is fails 50% of the way through install.  (I've tried different distros/discs... always fails.)  So... I want to plug the laptop hard drive into a usb enclosure and intall ubuntu, THEN move it back to my Toshiba laptop internally.  We'll see....

If it is not going to boot from a USB Flash Drive, then why do you think you can boot from a USB external hard drive? Something about that doesn't make sense. :S

---

