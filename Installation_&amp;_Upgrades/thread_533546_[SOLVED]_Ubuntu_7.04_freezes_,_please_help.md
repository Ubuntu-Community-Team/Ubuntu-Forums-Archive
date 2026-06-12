---
title: "[SOLVED] Ubuntu 7.04 freezes , please help"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by Mattemannen on 2007-08-24
Hi everyone,

Im trying to install Ubuntu 7.04 on my machine using the livecd, it gets as far as showing the desktop and then it totally freezes and I have to reboot and start again.
I manged to complete the installation using the text-based install cd but ones it boot same thing happens again, sometimes I can actually start a program or two.. but after a couple of minutes at best it hangs again.
based on some posts here and other searches on the net gave me some hints that foxconn motherboards ( which I have ) isnt very compatible with linux at all.
Can someone confirm that this is the case or does anyone have any other good hints for me?

please help.. I really want to run ubuntu on this box.

thanks in advance

Mattias

---

### Post by forestpixie on 2007-08-24
can you post some specs - especially memory

---

### Post by Mattemannen on 2007-08-24
Heres some specs on the machine

Motherboard: Foxconn P9657AA-8EKRS2
CPU: Interl Core 2 Duo E6600 2,4Ghz
Memory: 1GB DDR2 PC6400 ( have to post update on the brand later when I get home )
Graphic: Leadtek Geforce 8500GT 512Mb

---

### Post by Digitbig on 2007-08-24
I think the problem might be that you're low on hard drive space.

---

### Post by Pumalite on 2007-08-24
Post df -h (if you can)(You could use a live CD if necessary)

---

### Post by Mattemannen on 2007-08-24
Its a brand new 250gig drive.. so I dont think that is the problem.. but I will try and post results of df in while when I get home.. actually when I think of it.. you might be right anyway.. I have experienced the freezes many times when Ive tried to do a apt-get upgrade

thanks for now.. I will post results later

Mattias

---

### Post by Mattemannen on 2007-08-24
Here is some update

output from df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             144G  2.2G  135G   2% /
varrun                506M   96K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M  124K  506M   1% /proc/bus/usb
udev                  506M  124K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   33M  473M   7% /lib/modules/2.6.20-15-generic/volatile

the memory is a 1gb A-Data PC6400

hope anyone can help with this..could it be the system gets too hot?? its the cpu fan that came with the cpu though.. you would think that would be enough.

---

### Post by Pumalite on 2007-08-24
Your hard drive space is fine. What did you install with? Live CD? Alternate CD?

---

### Post by Mattemannen on 2007-08-24
I used the alternative cd, the livecd froze before it got a chance to even begin the installation.

/Mattias

---

### Post by Pumalite on 2007-08-24
Try other distros and see if there is a generalized incompatibility with Linux or is with Ubuntu only. Let us know.

---

### Post by Mattemannen on 2007-08-27
Heres a little update on the situation..

I got tired of it all and install windows xp... err.. no i didnt.. but I bought a new Asus motherboard instead.. everything is the same except the motherboard.. now asus instead of foxconn and everything seems to be working perfectly now.. :)

so a word of advice from me would be.. if you want to run ubuntu ( or maybe linux overall ) stay away from foxconn motherboards at the moment.. dont know how mac guys do it though.. cause what Ive heard all mac's nowadays have foxconn boards.. maybe I was just out of luck..

anyway.. thanks everyone for your suggestions and comments! cheers.

//Mattias

---

### Post by forestpixie on 2007-08-27
can you mark it solved for others - if you don't know how it's thread tools on your first post.

And glad you got sorted, welcome :)

---

### Post by Pumalite on 2007-08-27
> **Mattemannen said:**
> Heres a little update on the situation..

I got tired of it all and install windows xp... err.. no i didnt.. but I bought a new Asus motherboard instead.. everything is the same except the motherboard.. now asus instead of foxconn and everything seems to be working perfectly now.. :)

so a word of advice from me would be.. if you want to run ubuntu ( or maybe linux overall ) stay away from foxconn motherboards at the moment.. dont know how mac guys do it though.. cause what Ive heard all mac's nowadays have foxconn boards.. maybe I was just out of luck..

anyway.. thanks everyone for your suggestions and comments! cheers.

//Mattias

Thank you for the tip.

---

