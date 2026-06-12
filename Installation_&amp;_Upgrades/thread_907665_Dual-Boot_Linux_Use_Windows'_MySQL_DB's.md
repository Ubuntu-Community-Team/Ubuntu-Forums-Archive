---
title: "Dual-Boot Linux Use Windows' MySQL DB's?"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by jsampsonpc on 2008-09-01
I just installed Ubuntu (Dual-boot with Vista) about 4 days ago, and I would like to continue working on projects that I had been working on while using Windows.

I was able to point apache to /media/disks/.../www/ and use my Windows dir as my localhost, and now I would like to point my apache to the database files on my windows machine.

Anybody ever do anything like this, or have some general direction that would help?

Thanks in advance,

Jonathan Sampson
(A Potential Ex-Windows User)

---

### Post by tuxulin on 2008-09-01
> and now I would like to point my apache to the database files on my windows machine

isnt databases built using mysql and access is provided via PHP, Perl, python and .NET which is hooked up to forms ?

the goal that you are trying to create/recreate is not really a good one and neither
can you point apache to your database(s)

a better idea would be to reinstall LAMP on linux. export your database tables, move your web pages and any media to the new LAMP under linux 

you will have much less headaches

Tuxulin

---

### Post by jsampsonpc on 2008-09-01
I suppose I will just have to move it all over. I was hoping that there would be some intermediate stage where I could access the data from both OS's with ease.

I did find my my.cnf file in Ubuntu and point the datadir to the /media/disk/ location, but that didn't exactly solve my problem.

Oh well, thanks!

---

