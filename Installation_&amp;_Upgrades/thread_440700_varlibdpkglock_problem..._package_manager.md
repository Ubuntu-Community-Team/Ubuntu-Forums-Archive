---
title: "/var/lib/dpkg/lock problem... package manager"
date: 2007-05-11
forum: Installation &amp; Upgrades
---

### Post by Davez69gto on 2007-05-11
ok so here's the problem.

I beleive at some pt on my last install through the package manager it froze and i had to hard shutdown.  Well after that i wanted to install VLC vid player and well there was no sucess.  I'll give you a simple version of what it says...

When i do:
sudo apt-get install ssh
it comes up w/
"
dave@Davezlappy:~$ sudo apt-get install ssh
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
"
I've read other places that you can fix this by deleting the lock file in here and all will be well.  This file is labeled as a "weird" file and when i try to remove it i get.
"
dave@Davezlappy:/var/lib/dpkg$ sudo rm lock
rm: remove write-protected weird file `lock'? yes
rm: cannot remove `lock': Operation not permitted
"
When i do an ls -l i get
"
dave@Davezlappy:/var/lib/dpkg$ ls -l
total 2409381506
?r-xrw--wT   104  758710379    3502953 1314877038 1996-02-22 22:49 alternatives
-rw-r--r--     1 root       root          1269079 2007-05-10 18:59 available
-rw-r--r--     1 root       root          1269079 2007-05-10 18:59 available-old
?---------     ? ?          ?                   ?                ? cmethopt
-rw-r--r--     1 root       root             2552 2007-05-09 03:48 diversions
-rw-r--r--     1 root       root             2491 2007-05-09 03:48 diversions-old
br-sr----t   101    3240704 1752460901     57, 53 1970-02-07 20:26 info
?r--r-srwx 25903 1278177907 1598253923 1634235183 2021-10-17 10:04 lock
?r-sr-s--T 18734      18516      21076 1397314606 2025-07-13 04:08 methods
?---------     ? ?          ?                   ?                ? parts
?---------     ? ?          ?                   ?                ? statoverride
?---------     ? ?          ?                   ?                ? statoverride-old
-rw-r--r--     1 root       root          1166121 2007-05-10 18:59 status
-rw-r--r--     1 root       root          1166115 2007-05-10 18:59 status-old
?---------     ? ?          ?                   ?                ? updates
"
and lock is displayed in orange

I hope someone can help

If you need anymore info please feel free to ask... Thanks Dave

---

### Post by mthakur2006 on 2007-05-12
have you tried rebooting?

---

### Post by Davez69gto on 2007-05-12
Yes, rebooting does nothing for me, i've also tried using the sudo apt-get update and sudo apt-get clear.  I beleive that is what they were but the cammands were also meant to clean it like it was restarting.

---

### Post by mthakur2006 on 2007-05-13
i don't know then, sorry.
i had a problem once like this as well, but i could afford a reinstall and i did that....if you can do that, i suggest you do that.
thanks.

---

