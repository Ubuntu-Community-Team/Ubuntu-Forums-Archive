---
title: "Win 7 + Ubuntu Dual boot help"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by NathanNZ on 2010-02-08
Ok so im reasonably new to ubuntu.

I've had it installed and running on virtual machines for a while now and i've just received a spare 500gb hard drive.

So the setup i have is 
1Tb = Storage
500Gb = Windows 7 Ultimate 64bit
500Gb = Ubuntu 9.10

At first all installed and ran fine.

The windows operating system was set to default and to boot into ubuntu i had to F8 into boot menu to choose the other 500Gb hard drive which would boot ubuntu.

This was a pain so I tried to follow some tutorials about EasyBCD
and setting it up so I could boot ubuntu through windows Boot manager.

From that point if I choose ubuntu from the windows boot manager it would say something like \NST\nst-*** **** ***** ****.mcr (that was a guess) cannot be found blah blah reset windows boot manager using the repair DVD. I knew what it was talking about so reset the Boot manager in EasyBCD to normal. 

But now no if it try booting off the ubuntu hard drive grub locks up.

Sorry If thats long but ive learnt from helping others that the more info you can give the easer it is.

Im happy to answer any questions aswell.

Thanks heaps,

Nathan

---

### Post by ssican on 2010-02-08
See:

1)How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)


2)Try, EasyBCD 2.0 BETA -Build 79 
[http://neosmart.net/forums/showthread.php?t=642](http://neosmart.net/forums/showthread.php?t=642)

---

### Post by NathanNZ on 2010-02-08
Ok so now I can get back to grub but it hangs..... no error just hangs

something like

grub 1.5 blah blah

Grub loading, please wait...


I left it for 5mins and nothing??

Sorry im still learning

thanks

---

### Post by NathanNZ on 2010-02-08
just an update i left the grub loading, please wait... for 25mins and still no error

---

### Post by golusweet on 2010-02-08
Just reinstall again.

---

### Post by Mark Phelps on 2010-02-08
It's not necessary to completely reinstall just because you have a boot problem!!

But you need to tell us which you want to use to control boot options: GRUB 2 or EasyBCD 2.  They work in entirely different ways.

---

### Post by NathanNZ on 2010-02-08
> **Mark Phelps said:**
> It's not necessary to completely reinstall just because you have a boot problem!!

But you need to tell us which you want to use to control boot options: GRUB 2 or EasyBCD 2.  They work in entirely different ways.

I can just reinstall if its easier ..there is no personal data on the hard drive and ubuntu's installation is pretty easy but i like learning so id rather try solve this so i learn for future.

Well nether at the moment as anyway I try booting ubuntu it hangs.

I'd prefer to use Grub as the boot selector though.

thanks

---

### Post by darkod on 2010-02-08
If you prefer Grub2 (which is better anyway), why did you mess with EasyBCD? You said it yourself, you had the windows hdd as first boot option in BIOS and unless you hit F8 and select the ubuntu hdd, it was booting windows directly.
Why not set the ubuntu hdd as first option in BIOS permanently and use the Grub2 menu to select ubuntu or windows depending what you want to boot.
If you reinstall, I suggest you do it like that. Grub2 does the job well, no need to go to third party bootloader like EasyBCD (it's not included in windows).

---

### Post by NathanNZ on 2010-02-08
> **darkod said:**
> If you prefer Grub2 (which is better anyway), why did you mess with EasyBCD? You said it yourself, you had the windows hdd as first boot option in BIOS and unless you hit F8 and select the ubuntu hdd, it was booting windows directly.
Why not set the ubuntu hdd as first option in BIOS permanently and use the Grub2 menu to select ubuntu or windows depending what you want to boot.
If you reinstall, I suggest you do it like that. Grub2 does the job well, no need to go to third party bootloader like EasyBCD (it's not included in windows).

Because after a day or so of doing that grub randomly stopped working that's why I tried EasyBCD which I know doesn't make any sense because all that does is points it to grub but I realised that after a hour or two, remember im still learning.

...Pretty much all i need to know now is why does grub hang?

its while it says grub loading, please wait...

It doesnt move on from that ...ive sorted everything else thanks

---

