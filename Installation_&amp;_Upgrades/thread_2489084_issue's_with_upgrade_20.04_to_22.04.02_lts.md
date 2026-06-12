---
title: "issue's with upgrade 20.04 to 22.04.02 lts"
date: 2023-07-18
forum: Installation &amp; Upgrades
---

### Post by rudibloes on 2023-07-18
Hey there,
 
I am sorry.
It didn't work. I guess i am 'lucky' the system didn't break all together. As it stated at the end of the failed upgrade 'Your system might be broken and won't work'. I am left with a system half upgraded and will probably run in to more problems. So much for a good system. If a new LTS upgrade not ready, why serve it?
I can not trust the failed sytem anymore.
Here are some screenshots during the upgrade. I hope this helps solve things for the future.
I guess there's no way to turn back to before the upgrade? 
I will be forced to do a total new install and spend some days installing every thing again from scratch? 
Can I avoid this with future upgrades?

Greetings
Rudi

---

### Post by Rubi1200 on 2023-07-18
Hi,

Screenshots are very hard to decipher for someone wanting to help.

Please run these commands in order and stop and post any errors you get.

Use the Go Advanced option when replying and paste between # code tags.

```
sudo apt update && sudo apt upgrade
```

Also ```
cat /etc/default/sources.list
```

Thanks.

---

### Post by Impavidus on 2023-07-20
libc6 is a pretty important part of your system. If that's broken, don't expect your system to be usable at all. I guess you're unlucky. Usually, release upgrades work well, but sometimes they fail. Fixing a broken release upgrade is rarely a good use of your time. Just try a fresh install. You can keep your documents and settings (easiest if you've got a separate home partition, but not impossible otherwise) and reinstall your applications with a few clicks or commands. Of course, you already made a backup of your documents.

---

