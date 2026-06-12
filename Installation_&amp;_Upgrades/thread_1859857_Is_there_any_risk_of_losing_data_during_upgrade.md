---
title: "Is there any risk of losing data during upgrade?"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by Tutoo on 2011-10-14
i am using 11.04 now, and i would like to upgrade it to 11.10.
Is there any risk of losing data on upgrade??
What precautions should be made before upgrade..?
If so how to backup those files.. Pls help..#-o :? :? :? :?

---

### Post by oneferna on 2011-10-14
There is always a risk. So you should backup your /home directory and your /etc/X11/xorg.conf 

To back it up you can use an a million different methods. I like the command line so I tar -cxvf the /home/ onto an external drive. And I cp /etc/X11/xorg.conf over also. But you can use the file browser to drag and drop. Just make sure you show the hidden files, which are your configuration files, and copy those over also. Or you could use a backup program like Simple Backup. 

I'm upgrading now :)

---

### Post by Quackers on 2011-10-14
Welcome to UF :-)

Normally an upgrade will not cause any loss of data.
However, an upgrade gone bad can cause the loss of everything! People who've been using Ubuntu for many years tend to do a new fresh installation rather than upgrading an existing one.
You can backup everything with a number of utilities. I use clonezilla, which effectively makes a byte by byte copy of everything on your partition/drive.

I'm sure other ideas and advice will be along shortly :-)

Often the more experienced Ubuntuers will wait 2 or 3 weeks before upgrading to a new version, so that any niggly problems can be sorted out first ;)

---

### Post by sikander3786 on 2011-10-14
> **Quackers said:**
> {...}wait 2 or 3 weeks before upgrading to a new version, so that any niggly problems can be sorted out first ;)

That's it. If you are not an enthusiast and it is a production machine, don't jump into the adventure straight away.

On the contrary, Oneiric has been a far stable release than Natty but there are still a few who upgraded and had problems.

As mentioned above, theoretically, Ubuntu shouldn't cause any data loss at all. But you shouldn't risk your important data either. Most keep a backup of the things they care about. For everything else, there is always an alternative. And before doing any sort of upgrades, having backups is strongly recommended.

---

