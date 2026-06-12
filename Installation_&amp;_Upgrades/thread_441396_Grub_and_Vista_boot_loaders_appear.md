---
title: "Grub and Vista boot loaders appear"
date: 2007-05-12
forum: Installation &amp; Upgrades
---

### Post by John Picton on 2007-05-12
I've installed Ubuntu FF with my Vista system as dual boot. All works well except for one annoyance, It looks like the Ubuntu (Grub) boot loader appears first (I then choose Vista) and then the Vista Boot Loader appears (from which I can choose Vista or Ubuntu).

I would rather that just the Vista boot loader appeared from which I could either boot into Vista by default after x seconds, or choose Ubuntu.

Anyone have any idea how I can disable the Ubuntu Boot Loader and just use the Vista one? I used EasyBCD to put the Vista boot loader back after the install of Ubuntu.

Thanks in advance

---

### Post by Computer Guru on 2007-05-12
From a live CD install GRUB to the *BOOTSECTOR* of the Ubuntu partition.
Then in EasyBCD 1.6 on Vista choose to add the Ubuntu partition to the bootloader.

Here's the how-to: [http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
Skip down to "reinstalling grub" and go from there.

Cheers!

---

### Post by John Picton on 2007-05-12
Thanks for that. One more question:

If I decided that I wanted to use the Ubuntu boot loader rather than the Vista one, but I wanted to have Vista appear first in the list and boot up on default after x seconds, do I just need to change the order that they appear in the GRUB file, which I can change using the Terminal?

I was going to try it but was worried that if I messed it up then nothing would boot! At the moment Ubuntu is set as the first choice and will load if the countdown completes.

Thank you.

---

### Post by Computer Guru on 2007-05-14
Yeah - just change the ```
default 0
``` line to ```
default 1
``` or whatever entry number Vista is in your grub file.

---

