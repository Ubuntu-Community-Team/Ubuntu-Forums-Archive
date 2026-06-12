---
title: "failed command IDENTIFY PACKET DEVICE"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by gofes on 2012-05-20
OK. I upgraded to 12.04 (64) yesterday, completed the upgrade with no errors, restarted and everything seemed good!

This morning it boots but doesn't get to the GUI. I am given the command prompt, asking for login in, and password. 

Before the log in I get the followign error:

> exception emask 0x0 sact 0x0 serr 0x0 action 0x6 frozen
[45.592086] ata4.00 failed command IDENTIFY PACKET DEVICE
[45.592112] ata4.00 cmd a1/00:01:00:00:00/00:00:00:00/00 tag 0 pioi 512 in
[45.592113] res 50/00 03:00:24:00/00:00:00:00: Emask 0x4 (timeout)
[45.592172] ata4.00 status {DRDY}



I've had a look around and this is suggesting something to do with the hdd.

I have an SSD with Ubuntu installed and two HDD for storage

Any ideas what I should be doing?

---

### Post by gofes on 2012-05-20
Not sure if this is solved or not but . . . 
I downloaded the live cd, ran that had a look at my hard drives, everything seemed fine, so I rebooted with out the CD, and now everything seems fine.

---

### Post by gofes on 2012-05-21
Right, I got the error again this morning. It looks like sometimes ubuntu will load no problems, other times I get the error as above and only the command prompt?

Having a quick google I've found this for the smae error but causign a slow boot
[http://paulphilippov.blogspot.co.uk/2011/07/how-to-fix-slow-boot-with-ata-errors.html]("http://paulphilippov.blogspot.co.uk/2011/07/how-to-fix-slow-boot-with-ata-errors.html")

Before I do that, any ideas what it actually does?

---

