---
title: "Help! Ubuntu eats GB for breakfast!"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by Nonsense on 2008-05-04
I've been using Ubuntu Hardy now for awhile. Every time I start up my system the free space of the HD has been dramatically decreased (often by 1 or 2 GB). I find this rather strange since I haven't downloaded or installed anything. Today I "lost" 2 GB just by logging in! 

Help me Ubuntu community, you're my only hope.

---

### Post by Pumalite on 2008-05-04
Post:
df -h
top

---

### Post by tvtech on 2008-05-04
windows used to do that too me all the time.... never had linux do it though hope you find out what's up. !

---

### Post by GavinZac on 2008-05-04
Probably some error that is causing your logs to grow huge.

Use the disk usage analyser to see what's bigger than it should be.

---

### Post by Nonsense on 2008-05-04
> **Pumalite said:**
> Post:
df -h
top

/dev/sda2              44G   34G  8,0G  81% /
varrun                506M  108K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   68K  506M   1% /dev
devshm                506M   12K  506M   1% /dev/shm
lrm                   506M   36M  471M   7% /lib/modules/2.6.24-16-generic/volatile

---

### Post by Nonsense on 2008-05-04
> **GavinZac said:**
> Probably some error that is causing your logs to grow huge.

Use the disk usage analyser to see what's bigger than it should be.

I checked it and it shows that my var/backup is 25BG (!).
Bug?
Could it be fixed?

---

### Post by Pumalite on 2008-05-04
Unless you set some backup mechanism intentionally; I'd erase it. Then start looking for the culprit. Beryl use to be one.

---

### Post by Nonsense on 2008-05-04
> **Pumalite said:**
> Unless you set some backup mechanism intentionally; I'd erase it. Then start looking for the culprit. Beryl use to be one.

Duh.
I had previously installed Simple Backup and forgot all about it. It was set to backup everything daily. :oops:

Thanks anyway

---

### Post by Joeb454 on 2008-05-04
:lolflag: Sounds like something I would do. Search indexer's and hibernation files take up a lot of space too while we're on the subject :)

---

### Post by Pumalite on 2008-05-04
> **Nonsense said:**
> Duh.
I had previously installed Simple Backup and forgot all about it. It was set to backup everything daily. :oops:

Thanks anyway

You are welcome. Good luck.

---

### Post by Nonsense on 2008-05-04
> **Joeb454 said:**
> :lolflag: Sounds like something I would do. Search indexer's and hibernation files take up a lot of space too while we're on the subject :)

Thanks. I'll look into that. Right now I just feel blessed that I have 25GB more to fill with nonsense. Manna from heaven!

---

