---
title: "Can't install wonderful Ubuntu anywhere, help"
date: 2007-03-06
forum: Installation &amp; Upgrades
---

### Post by juice99 on 2007-03-06
i can't install ubuntu (tried versions 6.06, 6.10 and alpha 5), seems like cdrom fails to be mounted durning instalation. At least in casper.log i have
"Unable to find a medium containing a life file system"

and in alpha 5 it goes to ramsh or something, in 6.06 and 6.10 it just stalls.

also i have message on first console:

udevd-event[1962]: run_program '/sbin/modprobe' abnormal exit


i tried changing in BIOS how SATA works - from AHCI to IDE or IDE/RAID but that doesnt help! i was suggested on #ubuntu to add pci=noacpi and acpi=off to kernel boot options, but that doesnt help either (i added them by pressing F6 in menu and just typing)

what can i do? i tested 3 different CD and 2 different CD-ROMS. My Motherboard is Gigabyte GA-965P-S3 , which is ICH8 based motherboard.

That's why i tried alpha 5 ubuntu too, becuse i heard, cdrom support under ubuntu is working fine from 2.6.18 or .19 and 6.06 and 6.10 has lower kernel.

but that didnt help. what to do now?

---

### Post by juice99 on 2007-03-06
no ideas?

---

### Post by juice99 on 2007-03-07
anyone?

---

### Post by ardvark71 on 2007-03-07
Hi...

Are the CD's from Canonical or or they just burned copies using store bought writeables? Can you get to the initial option screen?

Best Regards...

---

### Post by juice99 on 2007-03-07
they are store bought and i can get initial option screen.

when i choose something, i get first screen with waiting bar but no text below it, and thats it.

I tried alternative CD - and it works, but after i install it, it doesnt want to start up :( i mean, i can install it, then reboot, then it starts booting and stops at the same step as it was stoping when i was installing desktop version

which means, it only shows empty bar, and no text below it.

---

### Post by ardvark71 on 2007-03-07
> **juice99 said:**
> they are store bought and i can get initial option screen.

when i choose something, i get first screen with waiting bar but no text below it, and thats it.

I tried alternative CD - and it works, but after i install it, it doesnt want to start up :( i mean, i can install it, then reboot, then it starts booting and stops at the same step as it was stoping when i was installing desktop version

which means, it only shows empty bar, and no text below it.

Hi...

Click on the option to check CD integrity for the burned disk. Bad burns will definately cause problems. If it's not that, I'm guessing Ubuntu doesn't like your particular SATA/IDE/RAID setup, possibly a lack of a driver. Have you tried any other distro or Windows? If so, what was the result?

---

### Post by juice99 on 2007-03-08
windows works, newest debian works (only while using latest snapshot of installer)

I finally managed to install 6.06 ubuntu using this guide [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

but it has 2.6.15 kernel, and my network card is working only from 2.6.19+ .

so i tried to use 2.6.20 kernel from feisty (upgraded all packages that were needed for linux-image-2.6.20) but the system didnt boot up!!!

so like i said, i installed 6.06, then i upgraded with apt-get upgrade and dist-upgrade to 6.10.. and it boots up (it's 2.6.17) but when i try to upgrade futher, to 2.6.20 also using apt-get upgrade/dist-upgrade, it doesnt boot up on 2.6.20. just saying it couldnt mount root

So i tried to compile 2.6.20.1 and 2.6.19.7 by myself from the sources, but i get these messages:

[http://cba.pl/sys9/crash/DSC00035.JPG](http://cba.pl/sys9/crash/DSC00035.JPG)

this is my dmesg from working 2.6.17 (ubuntu-made one):
[http://cba.pl/sys9/crash/dmesg](http://cba.pl/sys9/crash/dmesg)

these are two of _MANY_ configs i tried when trying my own kernel:
[http://cba.pl/sys9/crash/conf1](http://cba.pl/sys9/crash/conf1)
[http://cba.pl/sys9/crash/conf2](http://cba.pl/sys9/crash/conf2)

This is my grub menu.lst:
[http://cba.pl/sys9/crash/menu.lst](http://cba.pl/sys9/crash/menu.lst)
Root partition just doesnt want to work :( what could i forget to compile in ?

I have two options: 
- somehow add network card module from 2.6.20 or 2.6.19 to 2.6.17 kernel (i dont know how, when i just insmod 2.6.19 module while being on 2.6.17, it says bad symbols and things like that)
- or, make 2.6.19/2.6.20 kernel work on my hard drive/motherboard

please help me, i spent more than 20 hours trying to solve this

---

### Post by ardvark71 on 2007-03-08
> **juice99 said:**
> 
I have two options: 
- somehow add network card module from 2.6.20 or 2.6.19 to 2.6.17 kernel (i dont know how, when i just insmod 2.6.19 module while being on 2.6.17, it says bad symbols and things like that)
- or, make 2.6.19/2.6.20 kernel work on my hard drive/motherboard

please help me, i spent more than 20 hours trying to solve this

Believe me, I understand, I've spent many hours on my copy of Ubuntu as well, many of them needlessly. I think the easiest solution here would be to get a different network card that is compatible with the 2.6.15 (6.06) kernel and see if that runs stable without any problems or glitches.

I'm apologize but my knowledge with Linux isn't very comprehensive.:( 

Best Regards...

---

### Post by juice99 on 2007-03-08
it's now more than 25 hours and still nothing :( i tried 2.6.21 release candidate , but it's the same, and 2.6.17 doesnt want to compile - probably i have too new libc6-dev package

i don't want to buy network card only becouse i can't install new kernel - i'm pretty sure it is the matter of the right .config option to check, but nobody seems to know which one.

---

