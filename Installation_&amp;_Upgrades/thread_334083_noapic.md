---
title: "noapic"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by atlien on 2007-01-08
In order to run the live cd and then install ubuntu I had to enable 'noapic'.

What is 'noapic'?

Second question is has anyone made Ubuntu work on an Asus M2N4?  Once I get it installed and remove the live cd it says something about 'grub' upon startup then it won't start.

There was almost full functionality (no wireless) with the live cd.  Without the cd, can't even get to the desktop.  I assume it's a motherboard compatibility issue.  

My config:
[Asus M2N4 SLI]("http://www.newegg.com/product/product.asp?item=N82E16813131068")
AMD X2 4200+
[Asus 7600 GS Silent]("http://www.newegg.com/product/product.asp?item=N82E16814121007")
[2 GB Mushkin DDR2800]("http://www.newegg.com/product/product.asp?item=N82E16820146117")
[2x 250 GB Western Digital SATA]("http://www.newegg.com/product/product.asp?item=N82E16822144701")
[500W Enermax Liberty]("http://www.newegg.com/product/product.asp?item=N82E16817194003")

Any past experiences or suggestions would be greatly appreciated!

---

### Post by Footer on 2007-01-25
APIC = Advanced Programmable Interrupt Controllers (I think)

I just finished building this box:

Asus M2N-SLI Deluxe motherboard
AMD Athlon 64 X2 4200+(65W) Windsor 2.2GHz Socket AM2 processor
Corsair XMS2 2GB (2 x 1GB) DDR2 800 (PC2 6400) Dual Channel memory
Albatron 7600GS 256MB GDDR2 PCI Express x16 video card
2 X 250GB Seagate SATA
430W Antec Neo HE

All components were recognized and passed POST on the first power-up.

I stumbled across your message doing a search since I ran into the 'noapic' message as well when trying to install AMD 64bit Kubuntu Edgy ...

Would appreciate hearing if you got this resolved yet or not.

---

### Post by edeuxk on 2007-02-10
it seems you need to update your bios asus has released a new version

---

### Post by Footer on 2007-02-11
> **edeuxk said:**
> it seems you need to update your bios asus has released a new version

I agree, that would probably resolve the issue.  Only problem is, I don't have a floppy drive and although the manual says you can use a USB memory stick, I'm not sure how to do that?  It's a Windows world we live in and updating the BIOS would be a simple matter in that regard but this machine has and will NEVER see Windows so I've got to figure out another way.

noapic is about the only issue I have left with this box.  Running Fiesty Fawn AMD 64 Herd 3 (but have been apt-get update/upgrade daily) for the past couple of weeks and it's been pretty stable.

Thanks for the reply!

:)

PS.  In the mean time, I just edited /boot/grub/menu.lst and added the noapic parameter to the kernel line and she boots fine (don't reboot often though -- it's Linux!).  :)

---

### Post by pross on 2007-04-20
[http://dlsvr03.asus.com/pub/ASUS/mb/socketAM2/M2N4-SLI/0902.zip](http://dlsvr03.asus.com/pub/ASUS/mb/socketAM2/M2N4-SLI/0902.zip) <- latest bios...

to install it make a small fat32 partition somewhere and extract the file into it..then reboot and go into the bios screen and select 'ez-flash' it should see your fat32 partition and allow you to install the file :)

oh and try using enable_8524_timer instead of noapic ;)

---

### Post by Footer on 2007-04-22
Thanks for the tip!  I grabbed the newer BIOS (it was up to 0903 for my motherboard) and put it on my memory stick and the EZ Flash BIOS utility recognized it as drive D: and it was a simple matter to flash it (why I didn't try that long ago I'll never know!).  Now there's no need for the noapic kernel parameter!  I'm still getting a processor 'racing' condition which I'm still trying to sort out (I think it's related to Firefox) but that's a topic for another time/thread.

Thanks again!

---

### Post by jonathanku on 2007-04-27
Just flashed my bios (latest is v902) but still getting an error. I'll post the details later... running out for a wee pizza/beer in the city (priorities..)

---

### Post by Footer on 2007-04-27
What kernel are you running on?  Also, are you on Edgy or have you upgraded to Feisty?

I'm running Feisty on kernel 2.6.20-15-generic and it boots straight away with no extra parameters.  I went to the 0903 version of the BIOS update which is the latest ver. for my board (Asus M2N-SLI Deluxe).

MMMM, pizza & beer.  :)

---

### Post by jonathanku on 2007-04-27
Yeah running Feisty now. Similar message to Edgy though:

> MP-BIOS bug 8254 timer not connected to IO-APIC
Kernel Panic - cnot syncing: IO-APIC + timer doesn't work! Try using the 'no-apic' kernel parameter.

So, say I do use the no-apic command - where does that get entered? If I edit one of the lines - which one? One that starts "boot" or "kernel" or a new line at the end?

Maybe if I await BIOS 0903 for my m-board, that will help.

Any advice appreciated.

p.s. italian sausage, red onion and jalepeno pizza with crisp german beer.... well worth it :D

---

### Post by Footer on 2007-04-28
You can add it at boot time by hitting "e" on the kernel you want to boot and I believe it's the 2nd line down (the long one) that starts with kernel.  At the end, you just add "noapic" without the quotes, leave a space between it and the last parameter that's already there (probably "splash"?).

Alternatively, this file is called menu.lst and lives in /boot/grub.  You can edit the file there and permanently add the parameter and then it will always be there and you don't have to manually add it at boot time .

Good luck!

:)

---

### Post by jonathanku on 2007-04-30
Thanks Footer. I did that and it solved that problem - but introduced others!

My USB mouse stopped working
My network interface stopped (thus no internet)
My sound device stopped working

I'm guessing you didn't find this behaviour with your system. But once again, any light you can shed would be appreciated.

---

### Post by Footer on 2007-04-30
Huh ... No, I had no further problems after adding just the noapic parameter.  A couple of other parameters I've used are:  acpi=off and nofb.  I don't recall where I got those from or what they do but I think it was from someone who had a similar problem and/or the same mobo as mine.  There's probably some documentation out there somewhere about all the various kernel parameters that can be applied.  Google is your friend in this case.  :)

Sorry I'm not much more help than that!  I hope you find the solution soon!

---

### Post by jonathanku on 2007-05-01
Footer, thanks for your help... the other parameters seemed to sort it out - see parallel thread:
[http://ubuntuforums.org/showthread.php?t=407932&page=3](http://ubuntuforums.org/showthread.php?t=407932&page=3)

---

