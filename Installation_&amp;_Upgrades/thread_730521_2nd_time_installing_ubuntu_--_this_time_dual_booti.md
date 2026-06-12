---
title: "2nd time installing ubuntu -- this time dual booting but w/ woes"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by theartofbone on 2008-03-21
** a media check was done on the media prior to select the 'start install ubuntu' option, in which it passed testing**

Greetings... I had a nice working ubuntu system since Dec 2007 up until today. I realized that my installation wasn't as good as it could be, simply because it was the first time I was using the OS and I've managed to do things w/o direction, basically learning on my own. I had installed lots of apps, many of them doing the same function which in turn unstablized my system... in a way. For example, my wireless adapator quit functioning, after I installed half a gazillion apps that would automatically configure my wireless and it's ip/dns settings (wicd, twinkle, wifi radar, etc) and to access internet I've been directly connected via ethernet (old school).

This morning, I decided to reinstall my laptop's native OS, windows XP (tried using VMware for stuff, but too slow for my needs), cd key and all, and on top of that, I tried installing Ubuntu 7.10 amd 64 build. After successfully going through the install, the bootloader allows me to select "Windows XP home" boot into it, but upon selecting "Ubuntu 7.10, kernel 2.6.22-14", I get a blank screen. I soon realized that waiting some more would be to no avail. 

Now my question is, how can I make my computer boot into ubuntu via the boot loader, skipping the blank screen? I wouldn't mind reinstalling, as I do have the live/install cd.

My laptop specs are as follows: 
Model: Gateway MX6440;
Ram: 1 Gb (brand dont know)
CPU: 1 AMD Turion 64 ML-32 (1.8 Ghz)
HD: 100 GB disk, 93 GB total... 51 Gigs (55%) was set asside for linux during the install, and 41.895 gigs (45%) was set for Windows XP.
Wireless Lan: Broadcom 4318 chipset... <-- if anyone has an easy install for this, please let me know as well..

Thank you all for your time.

Will check back later, as of now, its far too late to do anything productful w/ regards to this mess...

Take care.

always,
Roberto

P.S I do repeat, my Windows XP is fully selectable on the boot menu, and I am online writing this with it. I've searched threads on here but my search terms were much too vague. 'blank screen dual boot' ... :)

---

### Post by theartofbone on 2008-03-21
:( 

When I press ctrl + alt + f1, the blank screen goes away, the ugly init messages are displayed, and X windows starts... 

This tip was found searching around... but I assume I shouldn't have to do that everytime I boot...

Perhaps the 32 bit (non amd64) version will work better? sigh... too bad I don't have that CD :(

still -- any more tips? Thanks...

---

### Post by Mustard on 2008-03-21
It's possible its related to the usplash problem if you are using Gutsy.  With this problem the resolution of the usplash screen was set incorrectly during the install, causing a failure to display the usplash screen.  It's a solvable issue if it is.

[http://ubuntuforums.org/showthread.php?t=700673&highlight=usplash+gutsy](http://ubuntuforums.org/showthread.php?t=700673&highlight=usplash+gutsy)

If you read over the guide above and just check what the resolution of your usplash screen is compared to your normal screen resolution settings, you should be able to determine if this is the issue.

---

### Post by theartofbone on 2008-03-21
Dear friend, thank you for your help. That was just the solution...

Cheers..

I find this new 64 bit compiled version of ubuntu 7.10 a bit more responsive than the 32 bit 6.x ==> 7.10 previous install. Or am I imagining this?

---

### Post by Mustard on 2008-03-21
> **theartofbone said:**
> Dear friend, thank you for your help. That was just the solution...

Cheers..

I find this new 64 bit compiled version of ubuntu 7.10 a bit more responsive than the 32 bit 6.x ==> 7.10 previous install. Or am I imagining this?

Glad I could help :)  It was a great description of the problem.  Good descriptions make troubleshooting so much easier.  Well done.

I'm not a 64bit user so I can't really compare. :D

I'd just mention that you can mark this thread as [SOLVED] using the thread tools menu at the top of this thread.  This would be helpful to others who are searching the forum for solutions.

Good luck and have fun!

---

