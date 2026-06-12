---
title: "Ubuntu 16.10 | 16.04 without systemd"
date: 2016-10-21
forum: Installation &amp; Upgrades
---

### Post by muankan on 2016-10-21
Hi All, 

I'm not a fan of systemd, is there any possibility using Ubuntu,Kubuntu or other LTS without systemd?
I've tried some cli solutions like here : 

[http://askubuntu.com/questions/779640/how-to-remove-systemd-from-ubuntu-16-04-and-prevent-its-usage](http://askubuntu.com/questions/779640/how-to-remove-systemd-from-ubuntu-16-04-and-prevent-its-usage)

all doesn't work.

Thanks,
mk

---

### Post by TheFu on 2016-10-21
> any possibility
Yes.

Is it likely that you or I will solve it? No. Moving to a non-systemd distro would be 1,000x easier. If you put 500 hrs into it and already understand how init works, perhaps.

Systemd is like a cancer, constantly expanding to take over more and more.  Some of what they are doing is very smart. Some of what they are doing is because other teams have stepped away (udev) and we all need that code to be maintained.  Some of what they do is more efficient, but against Unix culture (binary log files).

If you like the old-school init scripts, move to a distro that uses them or BSD. That would be much easier.

---

