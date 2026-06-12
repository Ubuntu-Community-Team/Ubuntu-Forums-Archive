---
title: "Triple Boot Question"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by Skyy on 2007-11-07
Hi, I have a little question regarding triple booting WinXP, Win Vista and Ubuntu 7.10.

I wanted to try Linux for quite a while now but I had always trouble with GRUB...

My HDD Setup is as following:

IDE1 Master:
WinXP

IDE1 Slave:
WinVista

SATA:
Random Data

External USB HDD:
Random stuff and
10GB unallocated

I wanted to install a different Linux a while ago on my SATA drive, but after reboot I only got the Vista bootloader so I changed the boot sequence to my SATA drive and then I only got a screen with GRUB written on it. I tried to fix this but after a while I gave up...

Now I want to give Ubuntu a try but this time I want to install it on my External USB drive (my Mainboard supports USB boot) Would this work without killing my two Windows? And has Ubuntu a different GRUB handling then other distros, so I wouldn't get the "GRUB" only screen again?

Oh and is Ubuntu compatible with Compiz Fusion and a ATI card?

Thanks for help in advance!

NOTE: I'm not a PC newb but a Linux newb^^

oh btw. I read about Instlux, but I'm quite confused... If I install Ubuntu with instlux, will it kill my Windows? Since I read that instlux  will update your Windows to Linux which sounds to me like Windows will get deleted....

---

### Post by dabl on 2007-11-07
> **Skyy said:**
> 

Now I want to give Ubuntu a try but this time I want to install it on my External USB drive (my Mainboard supports USB boot) Would this work without killing my two Windows? And has Ubuntu a different GRUB handling then other distros, so I wouldn't get the "GRUB" only screen again?



It is possible to do what you want here -- but it will be a "project".  Yes, *buntu uses the same Grub as other Linuces and it works the same way (i.e. you can still get a "GRUB _" screen).  Here's some relevant guidance:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

You'll probably NOT want Grub to write a boot menu, since you're running Vista.  It has a boot menu feature (so I am told ...).

> 

Oh and is Ubuntu compatible with Compiz Fusion and a ATI card?



YES, but ATI cards are not famous for their excellent Linux drivers.  I would advise using the Envy script installer to install the proprietary driver, which is a necessary pre-condition to running compiz.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)


> 

oh btw. I read about Instlux, but I'm quite confused... If I install Ubuntu with instlux, will it kill my Windows? Since I read that instlux  will update your Windows to Linux which sounds to me like Windows will get deleted....

I have no clue -- it's not a popular method.  I use the Alternate Install CD.  You need to review the Vista boot menu editing options -- probably that is the way to handle the situation, rather than Grub.

Good luck!  :)

---

### Post by Skyy on 2007-11-07
Thanks for assitence dabl!

is it possible to install Ubuntu without any bootloader? Or is this what you ment with "You'll probably NOT want Grub to write a boot menu"? I heard that VistaBootPRO a Vista Bootloader modifer is able to add Linux to the Vista loader, I totally forgot about it, thanks for reminding me^^ 

Although I fear I might get a "Device not avalable error" or something like that because I think Vista can't access any USB drives before it's completely booted but I don't know...

---

### Post by dabl on 2007-11-07
Yes --  well, actually I would say "It's possible to have the bootloader installed where it won't make any difference in the computer's functioning at boot."

At then end of the installation process (and it's best to use the Alternate Install CD which makes this more obvious) you have the choice of where Grub is written.  If you actually don't want a boot menu to be created or amended, which is your situation, you just point it to the root directory of the new OS that you just installed.

Then, at your leisure, you will need to edit your existing boot menu to add appropriate lines reflecting the new OS.  I've done it this way on internal hard drives, and I'm sure it's the same with connected USB drives, except you have the extra issues of making them bootable.   :)

---

### Post by Skyy on 2007-11-07
Editing Vistas boot menu is no problem for me :) Where can I get a Alternate Install CD?

---

### Post by dabl on 2007-11-07
See the big [COLOR="YellowGreen"]**green**[/COLOR] arrow here?

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

  Check the box right under it, then click "Start Download".

---

### Post by Skyy on 2007-11-07
Oh I see, thank you! Is the text installer more complicated then the normal GUI install?

---

### Post by Skyy on 2007-11-08
Sorry for bumping, I wanted to install Ubuntu now, but I got stuck at the HDD select screen.
I marked my External HDD with Guided Install but will this overwrite the partition on my external drive or will it use the 10GB unallocated space?

---

### Post by bulldog on 2007-11-08
Nope,no guided install,choose manual and point it to the free space,don't forget the swap if you don't have one that is.

---

