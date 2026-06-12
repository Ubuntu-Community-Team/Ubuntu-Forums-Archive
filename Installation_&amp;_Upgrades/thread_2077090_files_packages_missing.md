---
title: "files packages missing"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by abelito8 on 2012-10-27
{SOLVED}

Hi there, 

I am using 12.04 LTS on a sony vaio

when I try to update it gives me the message below...the problem is also that I get the same message when I try to install ubuntu one. Any ideas of what this may mean?

 Failed to fetch cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/dists/maverick/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognised by APT. apt-get update cannot be used to add new CD-ROMs

---

### Post by Mark Phelps on 2012-10-27
It's trying to retrieve packages from the CD -- which is probably NOT mounted, so it's going to fail.

If you have Synaptic Package Manager installed, in the tab listing the repositories, I believe there's a checkbox to include the CD -- which you need to uncheck.

---

### Post by jerrrys on 2012-10-27
Go to Software-Sources and uncheck CDrom.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

---

### Post by abelito8 on 2012-10-28
so simple...
thanks a million

---

### Post by jerrrys on 2012-10-28
If only it could be like that all the time  :)

Please mark this solved

---

### Post by abelito8 on 2012-10-28
....when I replied I was looking for the "solved" option
but cannot find where I should modify the post...

---

### Post by hakermania on 2012-10-28
On the upper right corner, thread tools->mark this thread as solved.

---

### Post by abelito8 on 2012-10-28
efkaristo
just learned another new thing :)

---

