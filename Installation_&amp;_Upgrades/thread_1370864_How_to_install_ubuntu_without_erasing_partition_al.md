---
title: "How to install ubuntu without erasing partition alignment?"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by Ero on 2010-01-02
I'm trying to do a partition alignment on my main SSD to improve SSD performance and then install Ubuntu on the SSD. I can do the alignment with no problem but when I install ubuntu the alignment is erased. Is there a way to install ubuntu without getting rid of the alignment?
Thanks

---

### Post by jamb on 2010-05-08
Easy, well it depends. If you have some practice using the command line interface, and have used fdisk for partitioning before, I would say its a good start. Its also depends on what systems and how many, you plan to have on the disk.

If you have a similar set-up like me, were I only use one ubuntu/debian, and are prepared to do new install - then I can help - and its easy (but you will need the alternate installer CD - not the standard GUI one)

---

### Post by kansasnoob on 2010-05-08
The following guide shows how to pre-partition and install to those existing partitions without changing that partition layout. Since you already have the partitioning done (I think) you could skip down to about half-way through that.

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

It basically comes down to writing down the partition designations (as seen by Ubuntu, eg: sda1, sda2, etc) and being certain to select and properly assign those partitions using the "manual" install option.

Browse through about the last half of that tutorial and post back if you have more questions.

---

