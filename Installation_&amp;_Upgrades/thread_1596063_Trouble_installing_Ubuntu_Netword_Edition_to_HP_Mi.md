---
title: "Trouble installing Ubuntu Netword Edition to HP Mini Netbook"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by Rodayo on 2010-10-13
Right so I'm trying to install ubuntu on my HP mini because it's a bit too slow when it runs windows 7 ultimate. 

I installed the Ubuntu Netbook Edition onto usb thumb drive as per these instructions:
[http://www.ubuntu.com/netbook/get-ubuntu/download]("http://www.ubuntu.com/netbook/get-ubuntu/download")

I changed the boot order on my netbook to the usb drive and everytime I try to boot up I get this message in a black screen and nothing else happens:

"SYSLINUX 3.86 2010-04-01 EBIOS Copyright (C) 1994-2010 H. Peter Anvin et al"

PS: its an HP Mini 110-3000

PPS: I messed up the title; I keep getiing "network" and "netbook" confused. =P

---

### Post by texastrey1836 on 2010-10-13
I'm having the same problem, but I don't get any response. I did install a new hard drive, but it's the same kind of computer--HP Mini 110. It will work once after install but then it won't work; just a blinking cursor.

---

### Post by Rodayo on 2010-10-13
> **texastrey1836 said:**
> I'm having the same problem, but I don't get any response. I did install a new hard drive, but it's the same kind of computer--HP Mini 110. It will work once after install but then it won't work; just a blinking cursor.

Maybe a diff version of ubuntu will work. you know any other distros that are meant for netbooks?

Edit: I figured out my problem. There was a minor detail that I overlooked early on. When I was using Universal USB installer, it didn't version 10.10 (which is what I downloaded) on the list so I just chose 10.04 instead. I tried again with a diff. version of usb installer which had 10.10 on the list and it did the job.

---

### Post by leuribe2 on 2010-11-24
I had the same problem and tried the latest version of the Universal USB installer without having any success...

I was able to solve it using **UNetbootin **software to create the bootable LIVE USB... after that, everything ran as expected.

Hope this helps!!! :)

---

