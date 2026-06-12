---
title: "Where should I install bootloader to? (Maverick)"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by gabriella on 2010-10-14
Hello...

I decided to install Maverick. The installation procedure is slightly different and one question that comes up that wasn't there previously is option of where the boot loader should be placed. Before it just "did it"

So I have 3 options in this order:

1.  My hard disk
2.  /dev/sda2  (my linux partition) 
3.  My old windows partition

Which of these was it installed to by default in previous releases? The second option maybe?


This leads me to a second question......
If I decided to either delete the Windows partition (likely soon as I never use it) and install a different Linux distro or simply add a third Linux distro anyway as a tri boot which would be the best place for the boot loader? i.e just to add it to the Grub list without changing the bootloader. I seem to recall some minor issues with a new OS replacing the original boot loader with it's own if you didn't do it right.

Thanks for any advice.

---

### Post by dino99 on 2010-10-14
install grub-pc on /dev/sda (not sda2), usually its the bios hdd booting choice (in case of multi hdd)

even if you install more distro (without installing grub-pc again), grub2 will find them and list to its menu.

---

### Post by dabl on 2010-10-14
> **gabriella said:**
> 

So I have 3 options in this order:

1.  My hard disk
2.  /dev/sda2  (my linux partition) 
3.  My old windows partition

Which of these was it installed to by default in previous releases? The second option maybe?



If you see a boot menu, on which you get to choose to boot either *buntu or Windows, then the answer is #1.

For future purposes, unless you have plans to install a new version of Windows, it's probably a safe bet to install Ubuntu's Grub on /dev/sda (the hard disk MBR) again.

Then, for the next Linux that you install, you'll need to choose to install Grub into the _partition_ for that Linux (or else, you'll be choosing to overwrite the MBR and let the newer Linux have control of the boot menu).

Hope this helps.

---

### Post by gabriella on 2010-10-14
> **dabl said:**
> If you see a boot menu, on which you get to choose to boot either *buntu or Windows, then the answer is #1.

For future purposes, unless you have plans to install a new version of Windows, it's probably a safe bet to install Ubuntu's Grub on /dev/sda (the hard disk MBR) again.

Then, for the next Linux that you install, you'll need to choose to install Grub into the _partition_ for that Linux (or else, you'll be choosing to overwrite the MBR and let the newer Linux have control of the boot menu).

Hope this helps.

@dino99
@dabl

Yes that explains it! Thanks :)

---

