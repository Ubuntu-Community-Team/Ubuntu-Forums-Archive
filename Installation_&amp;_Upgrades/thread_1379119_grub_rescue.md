---
title: "grub rescue"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by soloman498 on 2010-01-12
I had Windows xp loaded onto a 160gb hdd only taking up 30gb.I loaded Ubuntu 9.10 and shared the hdd evenly.9.10 seemed to load o,k but when it restarted I only got a black screen with the following:         

GRUB loading.
error: no such partition
grub rescue>

 I tried loading 9.04 to use the terminal,supergrub and xp but the machine will not read from an live disk even.Any ideas please?:P

I disconnected the 160gb hdd and hooked up another hdd with open solaris on it and the computer worked fine.

---

### Post by mifi on 2010-01-12
Have a look here: [https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2").

It did not help however.

At the grub rescue prompt, I typed 'ls' as is suggested in several threads. The 'ls' command return no information, just two empty lines.

So it is trying to tell me that grub has found no disks to boot from, while there are two harddisks in the machine??

When I boot from the live CD, I have no problems in mounting the 9.10 rootdevice (which is /dev/sdb1 in my case) and run 'grub-install'.
After this reconstruction my machine boots fine, but only once.

I am stupified...

Help!

m

---

