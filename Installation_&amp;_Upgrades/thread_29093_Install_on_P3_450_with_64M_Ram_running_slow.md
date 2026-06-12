---
title: "Install on P3 450 with 64M Ram running slow"
date: 2005-04-22
forum: Installation &amp; Upgrades
---

### Post by noelferg on 2005-04-22
Have just installed Hoary on an old Compaq with an 8G HDD.

Have read 64M Ram is the minimum.

It is running painfully slowly. All programs load very slowly. (I have previously installed Hoary on a few machines, the slowest being an Athlon 700 with 384M Ram. It ran fine on that.)

Should I give up or are there worthwhile things I can do to speed things up?

 :?

---

### Post by magicfab on 2005-04-22
What is the processor speed ?
I have run with 256MB on PIII 500 and it's OK. If you're using Gnome, it takes a lot of resources. You could try using XFCE instead, for example.

---

### Post by kelean on 2005-04-22
[QUOTE=noelferg]Have just installed Hoary on an old Compaq with an 8G HDD.

Have read 64M Ram is the minimum.

It is running painfully slowly. All programs load very slowly. (I have previously installed Hoary on a few machines, the slowest being an Athlon 700 with 384M Ram. It ran fine on that.)

Should I give up or are there worthwhile things I can do to speed things up?

 :?[/QUOTE]
 The best thing you could do is add memory.  Im running a P3 450M and its fine.  It runs better than windoze did.  Another thing you could do is install XFCE4 because it does use as much memory.

---

### Post by lemone on 2005-04-22
It should run fine on that.  Your probably constantly hitting swap with 64mb, and I'm guessing that the 8Gb drive is 5400rpm.  I bet if you drop another 64Mb of RAM in there it will pick up considerably.  The placement of the swap partition on the physical drive can also help, but probably not much.  I've heard some people say that putting swap first on the outer edge of the drive is faster, and I've also heard people say that the inner part of the drive spins faster so swap works better there.  I opt for the outer edge since the heads rest out there and seek time is slightly faster.  That might be an interesting experiment, but the extra 64Mb would be better in either case.

---

### Post by noelferg on 2005-04-23
Processor is Intel P3 450

I have been reluctant to try a different Window Manager as I am at last getting reasonably familiar with Gnome. Not too keen totry XFCE where I might have to do more manual configuration.

By the way I am setting this box up for someone who knows nothing about Linux.

---

### Post by gizmospc on 2005-04-23
[QUOTE=noelferg]Processor is Intel P3 450

I have been reluctant to try a different Window Manager as I am at last getting reasonably familiar with Gnome. Not too keen totry XFCE where I might have to do more manual configuration.

By the way I am setting this box up for someone who knows nothing about Linux.[/QUOTE]


Since RAM has gotten considerably cheaper I would put in as much as either the computer will allow or as much as your friend will afford.  This should allow you to continue using Gnome as it's (seemingly) much more user friendly for someone that's new to Linux.  

This next idea is just my opinion, but I would also make sure your friend knows where to get help with commands (ie. command line actions) since this can be very stressful to someone that's more used to the Windows envirionment.  Just speaking from personal experinece.   :-D

---

### Post by moglenstar on 2005-04-27
well, ive successfully install warty on an old pentium 2 233mhz 182mb ram .. its not my main computer, but i wanted to mess around with ubuntu a bit before setting it up on my main computer.

with gnome it runs a bit slow, but its usable, its updating to hoary as i type this, and now that it has downloaded all of the files, its taking a long time to set them up!

 :)

---

### Post by arctic on 2005-04-27
with only 64 mbram, i recommend putting the swap at the first section of your hdd and make it not double ram size but three or four times your ram size. otherwise, most swap will be used by gnome. 256 swap should do the job.

if you are not too keen on running ubuntu but also willing to try other distros, i recommend to install damn small linux. it uses fluxbox as default and will run better with only 64 mbram than ubuntu unless you skip gnome and replace it with flux, icewm or another lightweight desktop.

---

