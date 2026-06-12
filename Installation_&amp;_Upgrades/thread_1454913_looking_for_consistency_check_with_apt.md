---
title: "looking for consistency check with apt*"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by lct on 2010-04-15
Hi,

I was updating my home system remotely, and the ssh connection timed out. And I was not using screen as I always do ! :-( Since I'm a little bit paranoid, I was looking for a way to check if updates were successfully installed.

In /var/log/dpkg.log, everything seems ok. I know the last packages that have been installed by "apt-get dist-upgrade":

> 
lct@bigbang:~$ tail /var/log/dpkg.log 
2010-04-15 13:47:29 status installed software-properties-gtk 0.75.10
2010-04-15 13:47:29 status triggers-pending python-central 0.6.15ubuntu1
2010-04-15 13:47:29 status triggers-awaited software-properties-gtk 0.75.10
2010-04-15 13:47:29 trigproc libc-bin 2.11.1-0ubuntu5 2.11.1-0ubuntu5
2010-04-15 13:47:29 status half-configured libc-bin 2.11.1-0ubuntu5
2010-04-15 13:47:30 status installed libc-bin 2.11.1-0ubuntu5
2010-04-15 13:47:30 trigproc python-central 0.6.15ubuntu1 0.6.15ubuntu1
2010-04-15 13:47:30 status half-configured python-central 0.6.15ubuntu1
2010-04-15 13:47:30 status installed software-properties-gtk 0.75.10
2010-04-15 13:47:30 status installed python-central 0.6.15ubuntu1



I'm now looking for a way to check the status of the installed package python-central. Is there an apt* tool providing some kind of consistency check based on md5/sha1sum/etc. of installed files ?

Same question for an entire system ?

Thanks for your help,
Regards,
Laurent.

---

