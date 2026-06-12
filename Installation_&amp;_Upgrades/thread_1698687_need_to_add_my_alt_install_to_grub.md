---
title: "need to add my alt install to grub"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by n00b512 on 2011-03-02
My laptop has a pretty pitiful 60Gb hard drive, which is just enough space for my dual boot Windows/Ubuntu install.  But it has an SD card slot that I want load another install on.  The only problem is my laptop doesn't support booting from SD.  I know there is a way to point the bootloader on my hard drive to the filesystem on the SD card, ie chainloading, but all my searching on the net has come up with nothing.  Can anyone point me to a tutorial on how to do this?

[edit] I should mention I'm using Ubuntu 10.10 with Grub .97

---

### Post by grahammechanical on 2011-03-02
I am not saying this is the answer but ...

You do the install to the SD card that you want. If it gives you an option to install Grub, you say no. Then you boot into Ubuntu and run sudo update grub. The Grub program should detect all the operating systems and create a menu giving you a boot choice.

Are you trying to anything different than you would be if you wanted to put a third OS on the hard disc or on a USB memory stick? Not really, in my opinion.

Does the Ubuntu installation have access to the SD card? Is it detected in Ubuntu?

Regards.

---

### Post by n00b512 on 2011-03-03
I didn't think it would be that easy.  Yes, ubuntu reads the SD card, so no problem there.  But won't I need to add SD drivers into the init.d for the install that will be booting off the SD card?  I was also planning to install it onto an encrypted partition.  Will update grub automatically detect installations on encrypted partitions?  I was thinking I would have to manually add it in.

---

### Post by n00b512 on 2011-03-05
Well, I tried update-grub and it doesn't seem to have found the install on the SD card.  So back to the original question.  Does anyone know where to find a tutorial on how to do this or how to add this to grub manually?

---

