---
title: "HP Pavilion dv9000 series finally working from the start"
date: 2008-09-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by alej on 2008-09-12
just happy to report that since I bought this laptop in May 2007 (AMD 64 bit, bcm4312) it hasn't been until intrepid ibex alpha 5 updated with kernel 2.6.27-3 that my laptop has had an easy transition to ubuntu.... and by that I mean no need of adding flags to the boot line, no need for ndiswrapper, no problems at all with NVIDIA suspend and resume.....

So to put it simply.....


GREAT WORK GUYS... KEEP IT UP....


As far as I am concerned, I see intrepid becoming the most burden free edition of ubuntu in history, since my picky HP laptop has never been happier...

---

### Post by Perpetual on 2008-09-14
Good to hear.  I have an HP DV6910US and Intrepid is the first Ubuntu that I can not get to boot.  All I get is 'kernel alive'.  Nothing more.  Haven't tried using any boot flags.  Hoping that the problem will iron out in the near future.

---

### Post by doorknob60 on 2008-09-14
Nice, my parents have a dv9008nr :) (PS does this mean no more rebooting to get it to reconize USB deivces?? :D)

---

### Post by vishalrao on 2008-09-15
i had to provide the nolapic boot option to boot intrepid (and it would only detect/enable 1 core of the dual core amd turion) until kernel .27-3.4 came along, now i dont need to provide any params. i have a pavilion tx1302au tablet running ibex amd64.

---

### Post by Perpetual on 2008-09-15
> **vishalrao said:**
> i had to provide the nolapic boot option to boot intrepid (and it would only detect/enable 1 core of the dual core amd turion) until kernel .27-3.4 came along, now i dont need to provide any params. i have a pavilion tx1302au tablet running ibex amd64.

I will have to see how Alpha 6 does Thursdayish when it releases.  I tried a daily build this weekend and it would not boot either.

---

### Post by AMIRITE on 2008-10-26
oh right.
i'm still having a bit of trouble with my dv9000. even on intrepid ibex.

---

### Post by myddewji13 on 2008-10-26
> **alej said:**
> just happy to report that since I bought this laptop in May 2007 (AMD 64 bit, bcm4312) it hasn't been until intrepid ibex alpha 5 updated with kernel 2.6.27-3 that my laptop has had an easy transition to ubuntu.... and by that I mean no need of adding flags to the boot line, no need for ndiswrapper, no problems at all with NVIDIA suspend and resume.....

So to put it simply.....


GREAT WORK GUYS... KEEP IT UP....


As far as I am concerned, I see intrepid becoming the most burden free edition of ubuntu in history, since my picky HP laptop has never been happier...

+1 but with and hp dv2708 (2000 series)...

---

### Post by Perpetual on 2008-10-27
[Still can not boot Intrepid on some HP laptops.]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/272247")

---

### Post by elj4176 on 2008-10-27
dv9074 here and the usb is recognized sometimes and sometimes not. I used to have to add the irqpoll option so I could use usb devices more than once.

webcam still doesnt work but who really cares. 

I did notice a problem with a super-slowdown of gedit that I posted about in another thread but it could be something specific to my install.

wireless works better than ever. 

I can't use the new nvidia driver because it messes up my mythtv frontend. I had to remove glx support in xorg.conf to handle stuttering playback and I cannot use compiz. I use this laptop as a mythfrontend a lot.

---

