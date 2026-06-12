---
title: "xubuntu on a CF card?"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by mlabonte on 2006-12-01
Ok so here is what I am looking at:

I have a thin client with a ECS mobo, 800mhz Via processor, 512mb RAM, and an IDE CF card interface with a 1GB CF card.

I have confirmed by testing before with a laptop hard drive that the thin client WILL run xubuntu (quite quickly in fact, I was impressed.)

For my next project I would like to get it running on the 1 GB CF card. So my question is: is that even possible?

My ultimate goal is to set up a Wildfire Jabber server for approx. 100 users. I would like to run it on the thin client because of the added reliability of an embedded platform. So if you have any suggestions relating to my ultimate goal, please feel free to share.

---

### Post by kerry_s on 2006-12-01
For something like that i would do a custom install, to cut down the size & things you don't need. Grab a alternate cd or mini.iso &  install the base system then build up from there. See the how to mini ram install if you need help.

But if you don't want to deal with that, try DSL linux it's made to work like that & is only 50mb.

---

### Post by CyberX on 2006-12-01
Hi.
Yes, it is possible. In fact, i've been testing small web servers with CF cards (no movable parts = absolute silence) and it works quite good.

The very first configuration I had was a Xubuntu 6.06 custom installation (command line only). I found out that it would install  in a Pentium MMX 233 MHz with only 48 MB with a 512 MB CF (used a CF to IDE adapter).  With Lighttpd as web server and Sqlite instead of MySQL, it even ran a web forum!

I'm now using Ubuntu Edgy Alternate CD on a K6-2 366 MHz with 128 MB and a 1 GB CF card, so I'm sure your configuration will succeed.

Sugestions:
- use JFS as a file system, because it uses less CPU;
- get a fast CF card, with DMA support;
- find a way to run everything on memory to minimize CF wearing out - read the CF data sheet to find out how many read-write cycles it endures)

---

### Post by mlabonte on 2006-12-04
Thanks for the feedback.

Ran into a few problems with the install, however it is now up and running. Thanks again!

---

