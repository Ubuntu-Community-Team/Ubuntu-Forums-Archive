---
title: "Grub error 21. Thanks to Ubuntu I can't start my computer"
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by RinMin on 2007-01-30
*This is me ranting for a bit.. you can skip to the important stuff* I have HAD it with Ubuntu. i have not been able to do ONE thing with it. After the countless times I tried to install it I finally had a working copy. Could i get it to play mp3's... NO. Could I get either of my supposedly compatible network adapters to work... NO. I'm much more happy with XP and a bunch of open source programs then that mess. 


Anyway....
I think I screwed something up. I had Windows on my internal hard drive and ubuntu on a partition in my external one. I decided to format the ubuntu partition but the next time I tried to start my computer I get this error message about grub error 21. All I want to do is start my computer in peace. I even set it so my computer would only boot from a SATA drive.. and still nothing. Please help :( .

---

### Post by unisol on 2007-01-30
what are your system specs?

---

### Post by RinMin on 2007-01-30
Umm... Dell optiplex gx280. Intel Mobo LGA775. Pentium 4 2.6Ghz. 1GB RAM. 80Gb HD. Anything else?

---

### Post by RandomJoe on 2007-01-30
The way Grub works, the bootloader looks to the /boot/grub directory on the Ubuntu partition to see what to do.  So when you reformatted it, you lost that.

However, not all is lost.  Hopefully you have the WinXP install disc.  On Win2K and previous if you run 'fdisk /mbr' that would put Windows' bootloader back on and you'll be back to running just Windows.  I believe WinXP is the same - but I've not had to do that, never set up a dual-boot with XP...  (If that isn't it, there _is_ an equivalent command, you'll have to either search for it or wait for someone else to come along... ;) )

I just realized I didn't explain *how* - you would boot the installer disc, and at some point tell it to quit the installer to get to a DOS prompt.  You can run the command there.  Again, it's been a long time and I haven't done it with XP...

---

### Post by ucsdrake on 2007-01-30
the grub error 21 means 

# 21 : "Unknown boot failure"

This error is returned if the boot attempt did not succeed for reasons which are unknown.


[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)

i had this problem when i installed Ubuntu to my external hard drive and had GRUB installed on hd1 (my internal drive) ... make sure that youre external drive is plugged in, turned on (for at least 5 seconds to be sure) and if it gives you the error 21 message press ctrl + alt + delete ... after that it should restart successfully (it did for me anyways if i didnt give my external enough time to boot up)

hope that helps

---

