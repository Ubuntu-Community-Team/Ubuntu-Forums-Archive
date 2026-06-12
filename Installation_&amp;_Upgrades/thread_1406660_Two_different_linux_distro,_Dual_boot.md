---
title: "Two different linux distro, Dual boot?"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by behzadsh on 2010-02-14
Hi, I will upgrade my ubuntu jaunty to karmic tonight. Maybe someday later I'd decide to test another linux distribution.
Question is, could two linux distro install in a same system and could stitch between them?

---

### Post by ajgreeny on 2010-02-14
No problem with two, or three, or even more linux distros on one machine.  With grub2 it is even easier to get all of them onto one grub menu instead of having to manually update every time a new kernel arrived for any of them.

Just don't try to use the same /home folder for all of them or you'll be in big trouble, as different versions even of the same application may need different config folders, many of which are kept in /home as hidden folders and files.

The easiest way is to have a separate /data partition and mount that in all distros, and to leave your home for each either on /root for the distro, or as a smaller /home partition for each, max of about 5GB each, as all your data will be elsewhere.

---

### Post by oldfred on 2010-02-14
+1 for ajgreeny

I share my data partitions one NTFS  for windows and one with all data with folders in the same fashion as root and link them all into root. My home is separate but it is only about 1GB with 3 years of some folders history and now I think I will keep home inside the distributions as it is small enough to easily backup.

Share data partition
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

You can also share swap if you never hibernate. I have also allowed a partition for next install and will real soon now download 10.04 to test it. I alternate install partitions so if I need to go back to the previous and find a setting I can.

---

### Post by behzadsh on 2010-02-14
thanks **ajgreeny** and **oldfred** for support

one more question, should separate /home now for different distros or I can modify it later when I want to Install new linux distro?

---

### Post by oldfred on 2010-02-14
If you have a separate data partition you really do not have to have separate /home partitions. You can mount the data easily in every install.
By data we mean all the standard folders in /home such as music, documents, videos, etc that do not have settings that may be unique to a program.

---

