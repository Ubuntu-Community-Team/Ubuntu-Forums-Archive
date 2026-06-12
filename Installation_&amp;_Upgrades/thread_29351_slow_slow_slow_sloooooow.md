---
title: "slow slow slow sloooooow"
date: 2005-04-24
forum: Installation &amp; Upgrades
---

### Post by kerinin on 2005-04-24
i just cobbled together a desktop and i'm trying to get ubuntu working on it.  the install went OK (more about this later), but the machine is unbelievably SLOW.  some quick specs:

900Mhz Intel IV
128Mb Ram
15 Gb HD
Lan card
Matrox Millinium 4Mb graphics card

(not much ram, i know)  it takes 20-30 seconds to load a terminal window, which seems excessive, even in Xfce.  I've tried starting with noapic - makes no difference.  the system seems to run ok without X (ie no noticeable slowness).

i had some problems with the video card.  the chipset has an integrated graphics engine which ubuntu installed as the primary driver.  i tried to install the s3virge driver for the Matrox card but couldn't get it configured correctly.  i've also installed mandrake and fedora - both of those installed the video card correctly, and both were just as slow, so it seems like the card isn't the problem.

i've also set up apache/php4/mysql, and it takes forever (5-10 seconds for phpinfo) to process requests (though it could be that my browser is just really slow).

help???  i really want to keep windows off this machine...

---

### Post by crazybill on 2005-04-24
What does #**head /proc/meminfo** show?

You might try putting more RAM in your box. RAM is cheap and does wonders for how fast your processing will go. It looks like RAM is your weak link.  Otherwise, kill unwanted processes.

You can see everything that is running with 

#**ps auwx**

---

### Post by kkith on 2005-04-24
I am assuming you have IDE drives.  If so, have you checked if DMA is turned on?  As super user, try:

hdparm -d /dev/hdc (or whatver drive it is).

If it is turned off, try turning it on and see how your performance is.

To check performace, try:
hdparm -t /dev/hdc

---

### Post by rwabel on 2005-04-24
[QUOTE=crazybill]What does #**head /proc/meminfo** show?

You might try putting more RAM in your box. RAM is cheap and does wonders for how fast your processing will go. It looks like RAM is your weak link. Otherwise, kill unwanted processes.

You can see everything that is running with 

#**ps auwx**[/QUOTE]

I've 1 GB of RAM, and I've the feeling that ubuntu is slower than windows. Is there something that indicates me why it's slow? Should I do a swap partition, I heard once with 1 gb of ram it's not neccesary.
MemTotal:      1036484 kB
MemFree:          6076 kB
Buffers:         20136 kB
Cached:         306336 kB
SwapCached:          0 kB
Active:         765696 kB
Inactive:       223612 kB
HighTotal:      131008 kB
HighFree:          140 kB
LowTotal:       905476 kB

---

### Post by kerinin on 2005-04-24
[QUOTE=crazybill]What does #**head /proc/meminfo** show?

You might try putting more RAM in your box. RAM is cheap and does wonders for how fast your processing will go. It looks like RAM is your weak link.  Otherwise, kill unwanted processes.

You can see everything that is running with 

#**ps auwx**[/QUOTE]
 meminfo produces:
MemTotal:        61008 kB
MemFree:          2700 kB
Buffers:           628 kB
Cached:          16932 kB
SwapCached:      13640 kB
Active:          37016 kB
Inactive:         2336 kB
HighTotal:           0 kB

there are a lot of processes running, but most of them are kde-related, and i have the same problem running Xfce which (i assum) doesn't run as many processes.

i'm thinking about getting some RAM though...
HighFree:            0 kB
LowTotal:        61008 kB

---

### Post by kerinin on 2005-04-24
[QUOTE=kkith]I am assuming you have IDE drives.  If so, have you checked if DMA is turned on?  As super user, try:

hdparm -d /dev/hdc (or whatver drive it is).

If it is turned off, try turning it on and see how your performance is.

To check performace, try:
hdparm -t /dev/hdc[/QUOTE]
 DMA is off - how do i turn it on?

hdparm produces:
/dev/hda:
 Timing buffered disk reads:   64 MB in  3.02 seconds =  21.22 MB/sec

is this slow?

thanks again!

---

### Post by kkith on 2005-04-24
Ah yes, I believe your problems will be solved if you turn on DMA for your hard drives.

Try (as super user):
hdparm -d1 /dev/hda (this turns on DMA),

otherwise

hdparm -d0 /dev/hda turns OFF DMA.

As far as read performance, 21.22 MB/sec isn't bad at all.  I get about 25.25 MB/sec, close enough.

---

### Post by kkith on 2005-04-24
[QUOTE=rwabel]I've 1 GB of RAM, and I've the feeling that ubuntu is slower than windows. Is there something that indicates me why it's slow? Should I do a swap partition, I heard once with 1 gb of ram it's not neccesary.
[/QUOTE]

You'll want to check if DMA is turned on for your hard drives.

---

### Post by kerinin on 2005-04-24
thanks - it's better, and if i'm running Xfce it's pretty workable.  the server is still sluggish but i suspect that's a RAM problem.

---

### Post by kkith on 2005-04-24
[QUOTE=kerinin]thanks - it's better, and if i'm running Xfce it's pretty workable.  the server is still sluggish but i suspect that's a RAM problem.[/QUOTE]
 Hm, that is kind of strange.  Your specs are good enough to run at a pretty good pace. Linux is good in that it can run well on older machines (all the way down to a 386).  It looks as if you have decent specs, 128 MB of RAM should run X and xfce at a decent pace.  What exactly do you mean by sluggish?

---

### Post by nad on 2005-04-24
kerinin,

You are showing only 64megs of ram ( meminfo produces: MemTotal: 61008 kB). I assume 4 megs share memory. What does your bios detect?

---

### Post by kerinin on 2005-04-24
that was one of the problems: one of my ram chips wasn't all the way in the slot.  when i snapped it in place things started moving a lot faster ;)

the DMA also helped (i added it to my hdparm.conf file) and i'm running Xfce.  

no problems anymore really, but i'd still like a little more RAM...

---

### Post by nad on 2005-04-24
Great. Just remember to seat it all the way!

---

