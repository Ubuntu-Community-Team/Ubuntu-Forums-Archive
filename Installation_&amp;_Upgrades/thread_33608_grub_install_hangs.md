---
title: "grub install hangs"
date: 2005-05-11
forum: Installation &amp; Upgrades
---

### Post by rjlakajqa on 2005-05-11
standard installation proceeds normally until it gets to the "installing grub boot loader" screen, but it never gets past 0%. i waited for an hour. here are the specs:

amd64 3200+
160gb ata samsung hd
geforceFX 5200
foxconn NF4UK8AA-8EKRS mobo

i know that's kind of a strange mobo, but it has all the features i wanted. could it be the culprit?

i checked the md5 sums and they are OK. i also tried installing on a maxtor sata drive and had the same problem. 

thanks

---

### Post by lt_kije on 2005-05-11
This happened to me once, too: different hardware, similar problem. I just ran the install again and didn't have the same problem. I've since discovered that I had some crummy RAM in that box -- that could've been the problem. Either way, I'd replace RAM before a mobo.

Good luck!

lt_kije

---

### Post by alastair on 2005-05-11
Not sure.

You could always do an "expert" install and choose "no" to installing a bootloader. I think it then asks you where to put it - and lets you choose /dev/fd0 (floppy). Maybe a floppy boot as a test?

---

### Post by Innova on 2005-11-16
I am also having this problem installing breezy badger on:
Athlon 64 x2 3800+
Epox nForce4 Ultra
Hitachi 7k250 ata hard drive

Did anyone find a work around?

---

