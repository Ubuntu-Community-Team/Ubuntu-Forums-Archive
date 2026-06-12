---
title: "Sorry about my failure"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by zebraa on 2006-11-06
Apologies if this is a FAQ FAQ. I am trying to load Ubuntu 6.06 20060531 on my laptop, which is a Rock Agenda XT500 Pentium3 700mhz with 256Meg of Ram and a 14gig HD. I have burned the CD  and it works fine on my main PC and has correctly created a partition and now runs from the HD on that.

But this CD will not load and instal on the laptop. I get the menu screen and then, no matter what option or failsafe variant I use, it shows "Loading Linux Kernel", 100% on bar, goes to blinking cursor and hangs. The machine has been correctly partitioned with Partition Magic (see below).

The same happens with almost every other distro I have tried  including Puppy, Mepis, Gentoo etc, all of which will load on my main machine. 

The only live CD distro which does load on the laptop, and is now on the HD as well, is DSL. It works fine, showing that the partitions are all valid. 

But I can't believe a Pentium3 256Meg 14gig HD shouldn't accomodate Ubuntu instead. I can't even get to the run or instal screen.

Any thoughts? Many many many thanks. 

PS Is there a way to simply instal and run Ubuntu on the laptop?

---

### Post by Titus A Duxass on 2006-11-06
Have a go with the alternative install CD which can be downloaded.

---

### Post by Sef on 2006-11-06
> The machine has been correctly partitioned with Partition Magic

Partition Magic and Linux tend not to get along.  Partition with [GParted]("http://gparted.sourceforge.net/") instead.

> Have a go with the alternative install CD which can be downloaded.

Try the alternate cd.  Often it will work where the desktop cd has failed.  It is text-based, but simple to install.  Just basically the defaults or inputting your name, computer name, etc.

---

### Post by zebraa on 2006-11-06
Thanks. I've tried the alternative live cd (and tested it on my main PC) but the same thing happens on the laptop. I get to the end of the "Loading kernel" bar and then I hang with a blinking cursor. I've tried various of the options, including terminal and expert, many of which I've tried before from the normal live cd, and the same thing happens.

I can't see that Partition Magic is the problem, because I never get to the hard drive stage, and anyway the hard drive is already working with DSL on it if I boot from there.

Further thoughts welcomed. I've spent dozens of hours on this now which is really silly, but then I am :)

---

