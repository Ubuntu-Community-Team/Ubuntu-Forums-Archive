---
title: "Booting/Installing ubuntu just stops/blank screen"
date: 2012-09-30
forum: Installation &amp; Upgrades
---

### Post by Akiyatsu on 2012-09-30
Hello.  

I am quite a confident windows user, but otherwise very new to Ubuntu, and after some exploration last year with my laptop, I wish to now use Ubuntu exclusively on my desktop.  However I am having difficulty installing.  

I have tried both CD and USB methods, following the methods suggested on the main download page.  Each time I get stuck at either a blinking _ (cd method) or a screen very similar to the screenshot hopefully attached to this post (usb method).  

I have tested both usb and cd on my laptop and it will boot from them, so I am assuming that they have been created properly and are working as intended, and that the issue is with my desktop hardware perhaps?

I tried unplugging all unecessairy devices (everything bar a ps2 keyboard and usb mouse) the only thing I've not tried is to remove a pci sound card from the mobo.  

Quick rundown:

intel core i7 960 (overclocked, will this affect and install?)
12GB DDR3, on standard clock
SSD system drive and HDD data drive
nvidia gtx 580
asus xonar d2
acpi x64 based pc
cannot recall the mobo id at the moment and reluctant to open the pc at this hour

Cannot think other any other relevant details currently.  I've tried to look for similar errors on the forums and web in general but can't see anyone with an exact same issue, and fixes for similar ones have not proved successful for me.  

Any help is much appreciated, thank you.

---

### Post by Bashing-om on 2012-09-30
Akiyatsu; Hi ! Welcome to the forum.

I regret you are having difficulties installing ubuntu. Will try and help.

Boot the cd (bios set to 1st boot priority cd) and depress the shift key as soon as the bios screen clears ..Should have a boot options screen. [some systems require to hold it, others repeatedly tapping it]

Try the various options and advise on results.
[INDENT]kind regards <==BDQ

[/INDENT]

---

### Post by Akiyatsu on 2012-10-01
Thank you for the reply.  

However holding or tapping shift seems to have no effect.  It boots from the CD, proceeds to a purple/reddish screen with a white 'keyboard = man in bubble' symbol, and then I'm left at a blank screen with just a blinking _ in the top left.  CD is spinning plenty, but no matter how long I seem to wait, nothing happens, no error message or anything.

---

### Post by oldfred on 2012-10-01
If pressing key at accessibility icons - person & keyboard, should give a menu. Then you can press f6. And with nVidia you will need nomodeset boot parameter.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Do you have Windows installed and are you in UEFI or BIOS boot mode? Whichever mode Windows is installed in, is the mode you have to install Ubuntu in. Only the 64bit version offers both UEFI & BIOS boot options. And how you boot installer is how it will install.

If drive is partitioned with gpt and first partition is efi, then you are in UEFI mode.

---

### Post by Akiyatsu on 2012-10-03
Thank you for the replies.  

I am now writing this from my desktop running ubuntu.  It seems that although I used the same .iso to make the usb/cd they presented me with different boot screens.  Each of which gave different options and menus.  

Setting nomodeset enabled me to install ubuntu, so thank you very much for that.  

Sadly I was unable to get it to recognise my ssd drive, I may have to keep that aside for a windows install, until I can work out later on how to use it.  

Thanks again.

---

