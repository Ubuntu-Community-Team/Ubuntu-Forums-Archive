---
title: "Uninstall / Reinstall 10.4"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by n4lbl on 2010-05-10
I am under the impression that I have a video problem due to installing restricted and non-free codecs in the wrong order.  My maintenance was done in an orderly fashion for a while but at this point I don't really know what I have.  What I believe I want to do is uninstall & reinstall 10.4  I upgraded from 9.10 and have two users.  (Yes, I have backups from "home" but) I hope that there is a way to just start over without restores.  My search didn't yield anything.  Where should I look?

---

### Post by narendraD on 2010-05-10
After you backup all your data from both users, i suggest simply do a fresh install.

But as always Backup, Backup.

---

### Post by n4lbl on 2010-05-11
Part of my question was "how do you do a fresh install"?  This install was done with the Update Manager.  Is there a way to use that again?  The Update Manager understood that the starting point wasn't a blank slate.  I don't see how this would work but I've missed things before.

I have a USB flash drive with a working 10.4 on it.  If I reinstall from that does it understand that I have two users and files out there?  I'm afraid to just try it without knowing what it does in advance.

I keep backups of everything downstream from home.  Is that adequate?  

My biggest frustration isn't that things go wrong.  It is that I can't find the information that I am looking for by myself.  I have _The Official Ubuntu Book_ (from 8.04) and that hasn't been and isn't any help.  I've tried searching but perhaps my search strings are inadequate.

thanx,,,

---

### Post by darkod on 2010-05-11
Depending how experienced you are with ubuntu, do you know if you have separate /home partition or not?

---

### Post by n4lbl on 2010-05-11
No, I only have a swap and an ext3 partition.  I think I see where you are going.  If I re-partition separating /home from the rest what do I have to do so the OS finds the new /home?  This sounds like I need to read about mount points.  Is that the right topic and are there any other topics I should cover?  

If my home is in a separate partition then a new install into the partition where the current OS resides should leave my user data alone.  I like it!  If I do nothing (not repartition) and reinstall from the flash drive is that supposed to leave my user data alone?

thanx,,,,

---

### Post by dino99 on 2010-05-11
look at this mini howto:

[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by oldfred on 2010-05-11
I used this to move /home:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

All your user settings are in /home, but if you have system settings they will be in /etc and if you have made a lot of system changes you may lose those settings.
You can also export all the install programs and reinstall them:
from lovinglinux
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)


You also have to use manual install where you choose the partitions and the formats of the partitions. When choosing /home you DO NOT format that. It finds swap automatically.

Different verisons but all will be similar:
Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

ASUS EeePC netbook PC 10.04 install
[http://members.iinet.net/~herman546/p28.html](http://members.iinet.net/~herman546/p28.html)

---

### Post by n4lbl on 2010-05-11
Well, I guess that I know what I am doing tonight!!  Many thanks and I'm hoping that this thread will say solved by tomorrow morning.

thanx,,,,,

---

### Post by darkod on 2010-05-11
Yes, that's where I was going. I see you got plenty resources from oldfred, so you've got plenty to read now. :)

---

### Post by n4lbl on 2010-05-11
I'm not one to try it and see what happens.  Ideally I'll do my homework and make everything OK on the second try!!

again, thanx,,,,

---

