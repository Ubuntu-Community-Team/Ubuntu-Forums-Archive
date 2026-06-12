---
title: "Ubuntu live cd/usb won't boot"
date: 2014-07-29
forum: Installation &amp; Upgrades
---

### Post by rossjwmitchell on 2014-07-29
Hi, i have been having trouble with the ubuntu live cd, when I try to boot from it I get to the menu where i can choose to try ubuntu, install it and what not, when I press try or install it goes to a screen with a flashing cursor for ages (much longer than my older slower pc) and then goes to an orange screen with ubuntu in the middle although in the font seen in the shell, it trys loading for ages with the dots doing their animation under the word ubuntu, then the dots stop doing their animation then the background turns black and nothing happens, I have tried all the options that appear when you press f6 on the menu at the beginning and I have disabled secure boot, fast boot and what not, I have even tried unplugging all my hard drives and my ssd.

My system
-i5 3570k @ 4.6GHz
-asus maximus V formula motherboard
-EVGA nvidia gtx 780 ti superclocked (reference card with overclock and different cooler as far as i know)
-16gb of corsair ram at 1600mhz
-I am also using a qnix QX2710LED monitor (i know this has some problems with X config after nvidia drivers are installed so I thought i should mention it)

I used to be able to boot ubuntu 13.10 in the past from the live cd and install it but I can't anymore, the things that have changed since then in my pc is that I upgraded my ram up to 16gb (used to be 8gb) and I have updated my gpu (gtx 770 to gtx 780 ti) , the problems I am having now are the same for 13.10 and 14.04lts, as well as the gnome editions of ubuntu 14.04 (don't know about ubuntu gnome 13.10). Do you guys have any suggestions as to how I can fix this? I assume it is related to the 780 ti.

---

### Post by sudodus on 2014-07-29
Welcome to the Ubuntu Forums :-)

The standard tip is to use the boot option **nomodeset**, but it seems you have tried that already.

The next tip is to try Ubuntu 12.04 LTS. This old version will be supported until April 2017, and might cooperate better with your graphics card. It is also well debugged and polished now, two years after the release.

If you graphics card is really new, you might also try the next version, Ubuntu 14.10, that is being developed, and is scheduled for release in October.

In all these cases I suggest that you try various boot options.

---

### Post by rossjwmitchell on 2014-07-29
ok, will quickly try 12.04 LTS and see if that works. Any idea what I'd be missing with 12.04 LTS compared to 14.04?

---

### Post by sudodus on 2014-07-29
One important difference is that the two flavours might be ***different*** in the support of hardware.

Some software might be too old in 12.04, but I would say it is not a severe issue, because it it updated with point releases, now 12.04.4, soon 12.04.5 will be released. Is there some particular software, where you need the newest 'bleeding edge' version?

---

### Post by rossjwmitchell on 2014-07-29
nah, not really, I will probably be using it mostly for java programming for uni, just wanted to make sure that there wouldn't be any major features missing, at least it will definitely be an improvement over what I use in our uni's labs.... Scientific linux

---

### Post by rossjwmitchell on 2014-07-29
Ok, I tried 12.04 LTS, it had the same problem, I then got desprite and unplugged my dvd drive and then it worked for some reason, albeit still in software mode for the video, will try with one of the newer versions to make sure that it was just the dvd drive causing the problems.

---

### Post by rossjwmitchell on 2014-07-30
14.04 works after removing the dvd drive, must be that my drive is faulty or incompatible, it's one of these £10 drives you can get on ebay so not overly surprising, will be getting a blu ray drive soon anyway, thanks.

---

### Post by sudodus on 2014-07-30
That was a surprise for me. I'm glad that you solved the problem and shared your result with us :KS

If you feel that this problem is solved, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

New problems have a better chance to get solved in a new thread with a good descriptive title.

---

### Post by hoodbrothers2 on 2014-07-30
I had a very difficult time installing ubuntu on my computer.  In the end all I had to do was update the bios!  So if anyone is reading this and has troubles, update everything!

---

