---
title: "Dual booting 2 linux distros"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by chickenbowels on 2006-02-18
Hopefully this is an easy question.
I would like to Install Ubuntu Independently on harddrive c. Hard drive a and b are running Mandriva. Is there an easy how-to somewhere to do this? I guess this has to do with the bootloader and such, but I'm pretty much a newbie with Linux and I don't want to lose access to my Mandriva.
 Thanks for your help. 
Peace!

---

### Post by prizrak on 2006-02-18
Just go through the normal install and either install Ubuntu's GRUB in the MBR or just edit Mandriva's bootloader with the options needed. (Actually you might have to do it anyways)

---

### Post by cilynx on 2006-02-18
The Ubuntu installer asks very nicely where you would like to install it.  You will be able to see where your Mandriva is as well as where your new "hard drive c" is so that you can be sure to install in the right place.

The Ubuntu installer is also very good about setting up the bootloader to continue to work with other installed operating systems, be they Linux, Windows, or whatever.  This isn't Microsoft where the installer takes over the entire computer =)

Best of Luck

---

