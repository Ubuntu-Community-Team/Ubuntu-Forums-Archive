---
title: "dapper drake fakeraid configuration"
date: 2006-04-01
forum: Installation &amp; Upgrades
---

### Post by capacman on 2006-04-01
Hi everybody.
The first thing i have to say about installing ubuntu dapper drake  on  a hardisk which is installed windows XP or something with fakeraid is you can follow the 
[https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto) but there is one issue. If you have encountered an error message like /dev/mapper/blablabla can not be found and and can not mount root partition(so cannot boot up),  then you have to go this links and change your
[/usr/share/initramfs-tools/scripts/local-top/dmraid]("http://librarian.launchpad.net/1828011/dmraid")
[/usr/share/initramfs-tools/hooks/dmraid]("http://librarian.launchpad.net/1801664/dmraid")

Those are my suggestions and  here my questions,i build dapper drake according to fakeRaidHowto. But i could not find base-config command and now many things in my dapper drake doesn't working  like  anti-aliasing fonts, sound,sudo, and network( because dapper still in development). Probably i could configure all of them manually but is there any command or something else(that make all preconfiguration which is made in normal installation process)  that can help me configure all those things. Thank you in advance....

---

### Post by zackiv31 on 2006-04-26
Same Exact problem and still can't get Ubuntu to boot... Anyone?

---

