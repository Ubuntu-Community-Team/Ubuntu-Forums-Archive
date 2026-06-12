---
title: "Raid1 wount boot any how, shall I try with Debian?"
date: 2006-11-25
forum: Installation &amp; Upgrades
---

### Post by jose3 on 2006-11-25
Hi guys.
As I have succesfully installed RAID1 on three SCSI disks on my file server I tryed a similar configuration with three IDE disks for my MySql but...

I have taken the precaution of using three exact IDE disks and created RAID1 with the setup of the same 6.06 Alternate that I have used to setup the file server. Installation went ok (several times with different partition configurations say /,/swap,/home,/boot) but when came to the point that the RAID had to boot nothing happened, black screen with upper left white cursos pulsing.

I have searched for a solution and found out that there are a couple of bugs regarding RAID1 in most cases from updates from Edgy to Dapper but not my case.

In fact here there is a possible solution but I am not fond of starting a server setup this bad.
[http://www.ubuntuforums.org/showthread.php?t=287723&highlight=raid1+grub]("http://www.ubuntuforums.org/showthread.php?t=287723&highlight=raid1+grub")

Shall I use an older version?. If so where I could find an old Alternate version? Shall I try Debian?

Please help me decide what is the best solution for this case. I am very happy with Ubuntu and dont want to move.

Many thanks in advance.

---

### Post by jose3 on 2006-11-26
Came to the point where I am getting a little dissapointed and is a pitty because I was pretty happy with the results Ubuntu has given me.

So far tryed with both 6.06 altenate and server and 6.10 with no good result. Tryed also to configure Raid5 but GRUB failed to setup.

Please if there is any orientation you can give me I would appresitate.

Thanks.

---

### Post by jose3 on 2006-11-26
Damn!!! There so much I have to learn in my life!!!

Default setup made the trick.

Thanks anyway for those views.

Jose.

---

