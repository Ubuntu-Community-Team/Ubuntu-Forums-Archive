---
title: "problem installing ubuntu x64 on GIGABYTE ga-ep45-ds5 motherboard"
date: 2008-10-24
forum: Installation &amp; Upgrades
---

### Post by eyeJ on 2008-10-24
Hello im trying to install ubuntu x64 and it seems that im having trouble with sata drivers or something. :confused:

motherboard: GIGABYTE GA-EP45-DS5
processor: Intel Core 2 Quad Q6600
RAM: 2gigs of 1066mhz ram

other components are older ones and all worket great with ubuntu, the above ones are recently bought new ones

the error im geting: 
ata1: softreset failed (device not ready)
ata2: softreset failed (device not ready)

I googled on the topic but i dont know witch way to turn.
Thank you for your time! :)

---

### Post by Shaoline on 2008-10-24
May I ask what version of Ubuntu you are using, or trying to install?
You should try get a hold of the Intrepid Ibex beta daily build iso.. that one has later hardware support and may just be what you need, should it be a driver issue.

Someone else might be able to supply the link to those image-files..?

---

### Post by eyeJ on 2008-10-25
> **Shaoline said:**
> May I ask what version of Ubuntu you are using, or trying to install?
You should try get a hold of the Intrepid Ibex beta daily build iso.. that one has later hardware support and may just be what you need, should it be a driver issue.

Someone else might be able to supply the link to those image-files..?

Thank you for replying!
I'l google some for the Ibex iso's ;)
Im trying to install Ubuntu 8.04 :)

---

### Post by eyeJ on 2008-10-31
I found the solution just a few hours ago and im posting it here so that other people with the same motherboard as I (GA-EP45-DS5) can install ubuntu on their systems.

The solution is to disable the second sata II controller that is integrated on the motherboard in the system BIOS.
To Disable:
Turn on your computer and press <Delete> to enter BIOS Setup during the POST. In BIOS Setup, go to Integrated Peripherals, ensure that Onboard SATA/IDE Device is disabled (the one on the bottom of the list). press F10 confirm with Y and press Enter. After that put your install cd and now there should be no errors when trying to check the cd or start the live cd hopefully :)

This should work for all versions of ubuntu that don't support the GIGABYTE SATA2 SATA Controller on the GA-EP45-DS5 motherboard.

U can find more info on the stuff I'm talking about here in your motherboard manual key things to look for are: GIGABYTE SATA2 Controller and Intel ICH10R SATA Controller. ;)

Also make sure that after that all your drives are connected to the yellow sata connectors on the motherboard. You can also use the PATA green connector on the board for your cd or hdd to install ubuntu.

---

### Post by eyeJ on 2008-10-31
Actualy I have to correct myself: The PATA green connector will not work if you disable the GIGABYTE SATAII controler :(

Well that's it for now I'll post more info as soon as I figure it out :KS

---

### Post by MisiekBest on 2008-11-04
> **eyeJ said:**
> 
The solution is to disable the second sata II controller that is integrated on the motherboard in the system BIOS.
To Disable:
(..)ensure that Onboard SATA/IDE Device is disabled (the one on the bottom of the list). press F10 confirm with Y and press Enter.

Of course if your cd/dvd rom is not an IDE device ;)
Same problem here. Unfortunately i don't have sata cd reader so i wasn't able to test your trick :|
I have tried several daily snapshots of 8.10 but it seems like new kernel still can't handle p45 sata chip. The problem is known, many posts found in google but no solution yet... so we have to wait :(
BTW, if you will wait longer (during boot) after 7-10min (can't remember exactly) ubuntu will start anyway. (of course installation on hdd will fail - no disks ;) )

---

### Post by eyeJ on 2008-11-05
> **MisiekBest said:**
> Of course if your cd/dvd rom is not an IDE device ;)
Same problem here. Unfortunately i don't have sata cd reader so i wasn't able to test your trick :|
I have tried several daily snapshots of 8.10 but it seems like new kernel still can't handle p45 sata chip. The problem is known, many posts found in google but no solution yet... so we have to wait :(
BTW, if you will wait longer (during boot) after 7-10min (can't remember exactly) ubuntu will start anyway. (of course installation on hdd will fail - no disks ;) )

To bad you don't have the sata cd drive, I have no other problems after installing ubuntu everything works perfectly.
Maybe you should just get some sata cd or dvd drive coz they are not expensive these days :)

I hope the problem gets fixed soon ;D

---

### Post by MisiekBest on 2008-11-06
> **eyeJ said:**
> To bad you don't have the sata cd drive, I have no other problems after installing ubuntu everything works perfectly.
Maybe you should just get some sata cd or dvd drive coz they are not expensive these days :)

I hope the problem gets fixed soon ;D

Yeah, i know ;) Anyway...
Maybe ill try to install it from network or usb :mrgreen:

---

### Post by jblackthorne on 2008-11-06
I am not sure if you figured it out or not, but here are some important points:

* The SATA controllers must be set to EHCI mode (they will not work in IDE mode)
* Double-check you have the latest bios update.  The P45 chipset with 45nm chips requires an updated stepping support for the 2.6.27 kernel to work properly.

Hope this helps.

---

### Post by MisiekBest on 2008-11-07
> **jblackthorne said:**
> I am not sure if you figured it out or not, but here are some important points:

* The SATA controllers must be set to EHCI mode (they will not work in IDE mode)
* Double-check you have the latest bios update.  The P45 chipset with 45nm chips requires an updated stepping support for the 2.6.27 kernel to work properly.

Hope this helps.

Hmm, i have F11 version, F12 is the latest. Good point. I will try, maybe it will help.

**edit**
nope, BIOS@F12 and still same problem

**eyeJ:**
Good solution. It works!
Ive copied Ubuntu (last 8.10 snap) into usb pendrive using this tool: [http://unetbootin.sourceforge.net/]("http://unetbootin.sourceforge.net/") and istalled it with disabled IDE in BIOS. All is working fine (except dvdrom :P)
Thanks!

---

### Post by IeU on 2009-01-03
Sorry for the bump, but . . .

Latest snapshot would be . . . ?
8.10_Live
or
Daily_Live

?

Thanks !

---

### Post by SM411 on 2009-03-26
Thank you so much. Been looking for a fix to this problem for ages. Was about to buy a new mainboard or a sata controller. Thanks for this!

---

