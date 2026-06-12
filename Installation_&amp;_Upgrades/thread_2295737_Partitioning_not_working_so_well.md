---
title: "Partitioning not working so well"
date: 2015-09-21
forum: Installation &amp; Upgrades
---

### Post by liam26 on 2015-09-21
Hi
Ive got an old Foxconn computer (well pc w/ foxconn board). It has 1.5 gbs of ram and a dual core proccecor, but im not sure of clock.

Anyway when it says install alongside windows xp professional, i go next and it shows me that slider but no matter how i try the install now button is greyed out.

I dont want to use advanced partitioning tool because i dont know how (ive done in past but cant remember how).

Any help would be nice and the Ubuntu version is 15.04 and im doing it off a flash drive.

Also, can you install amd64 ubuntu on x86, its not the case in windows but maybe in linux.

Thanks

-Liam

---

### Post by ajgreeny on 2015-09-21
If you windows partition is mounted the slider to shrink it will show as greyed out, so if you're using gparted in the live *ubuntu system try right clicking on the partition and choose unmount.

For your spec of machine I think you will get much higher system speed if you use Lubuntu or Xubuntu rather than Ubuntu, in fact you may have trouble getting Ubuntu with the unity desktop to run at all, depending on the graphic system.

---

### Post by grahammechanical on 2015-09-21
I do not know anything about Windows. With Ubuntu the i386 ISO image is a 32 bit Linux operating system. It will run on 32 bit CPUs and 64 bit CPUs manufactured by both Intel and AMD. On the other hand the Ubuntu amd64 ISO image is a 64 bit Linux operating system that will only run on 64 bit CPUs but the manufacturer can be either Intel or AMD. Yes, the labels are confusing. Reason is part of history.

---

### Post by yancek on 2015-09-21
One possibility is that your windows partition is taking up the entire drive.  You would need to unmount and shrink it as suggested above before installing.  You might take a look at the link below which has a tutorial on installing including a step by step for dual boot.  Although the "Install Alongside" method usually works, if something does go wrong, you won't have any idea what it was.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

