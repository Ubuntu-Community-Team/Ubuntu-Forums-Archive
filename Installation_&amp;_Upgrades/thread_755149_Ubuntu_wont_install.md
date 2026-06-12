---
title: "Ubuntu wont install"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by LMee on 2008-04-14
Hi,
i used to run Ubuntu on an old laptop and decided to put 7.10 on my spare machine in anticipation for 8.04.

So, I drop in the disk and tell it to go,
The loading bar goes backwards and forwards multiple times and then just crashes to a black screen.


the system is an AMD64 3200+ with 768 or Ram and a 120 Gb IDE hdd


Heres the error message;
Udevd [2270]: runprogram '/sbin/modprobe/ abnormal exit
[random number] endrequest: I/O error devfd0, sector0
,,__________,,____________,,____________,,
Buffer:I/O error devfd0, sector0

After wards it says some tuff about union fs and a loop:module being lodad and finally finishes with  a squashfs thing


Any help is greatly appreciated.

P.S.
Have also tried the alternative CD which i MD5'd - same result

---

### Post by LMee on 2008-04-15
bump

---

### Post by warp99 on 2008-04-15
If this is an old laptop try the alternate CD. Go to ubuntu.com download page and tick the box maked "Check here if you need the alternate desktop CD." Burn the CD at a very low rate, 2x or 4x. It may also be that your particular player can't read RW+/- discs properly if it's a very old player.

---

### Post by |{urse on 2008-04-15
>  the system is an AMD64 3200+ with 768 or Ram and a 120 Gb IDE hdd 
0_o wow if thats old, then im getting old too :lolflag:

---

### Post by Deathrend on 2008-04-15
> **|{urse said:**
> 0_o wow if thats old, then im getting old too :lolflag:

I died a little inside when I read his post then thought about it

Me: That's not that old! I rember the AMD64's coming out clear as day!.. Wait.. /cry

Long live the T-Birds!

---

### Post by |{urse on 2008-04-15
and thats really weird... theres not a floppy drive on your laptop. wait thats not a thinkpad is it? thats the only manufacturer i can think of that makes new laptops with the same peripherals i.e. cd/floppy interchangeable bays. Because thts exactly what its doing.. trying to install a floppy driver and crashing. kinda like it thinks your cd drive is a floppy?

---

### Post by |{urse on 2008-04-15
maybe no ta floppy driver but modprobe is def trying to put something in whilst your cd is a floppy drive if that makes any sense.. which it doesnt lol

lol @ t-bird and those t-breds too

---

### Post by LMee on 2008-04-16
I think youve majorly mis-understood me - I HAD it installed an old laptop - but am now trying to install it on a AMD64 machine. It's the AMD machine which has a big issue

---

### Post by oilchangeguy on 2008-04-16
your best bet is to copy and paste the error message into google, and see what comes up.

---

### Post by warp99 on 2008-04-17
> **LMee said:**
> I think youve majorly mis-understood me - I HAD it installed an old laptop - but am now trying to install it on a AMD64 machine. It's the AMD machine which has a big issue

Sorry about that, my mistake. The error message is the udev daemon trying to run, but fails so it has something to do with the usb. Do you have a usb drive attached to the computer when installing? If not did you try to use any boot options?

[https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29](https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29)

I would try the options acpi=off and irqpoll since it may be an interrupt issue.

---

### Post by LMee on 2008-04-17
Ive removed all USB devices - but have a PCI USB expander module thing - could it be that?

---

