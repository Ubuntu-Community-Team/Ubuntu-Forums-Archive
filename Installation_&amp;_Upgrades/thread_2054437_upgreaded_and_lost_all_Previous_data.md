---
title: "upgreaded and lost all Previous data"
date: 2012-09-07
forum: Installation &amp; Upgrades
---

### Post by MUK3SH on 2012-09-07
I have just upgraded my OS ubuntu 10.04 to 12.04.
and lost all Music, videos and all data which was in My that user.
Lost all softwares Too. :( 
Bookmarks softwares. :(
So much importent files lost which were in documents . :( 
any body help me.

---

### Post by SlugSlug on 2012-09-07
how did you upgrade?

can you post output of

```
ls -l /home
```

---

### Post by MUK3SH on 2012-09-07
mukesh@mukesh-NC872AA-ACJ-SG3740IL:~$ ls -l /home
total 8
drwxr-xr-x 84 mukesh mukesh 4096 Sep  7 17:50 mkj
drwxr-xr-x 25 mukesh mukesh 4096 Sep  7 18:48 mukesh
mukesh@mukesh-NC872AA-ACJ-SG3740IL:~$

---

### Post by MUK3SH on 2012-09-07
I downloaded one ISO image then write that on a Blank DVD, then Restarted PC and Upgraded 10.04 to 12.04.1 .

---

### Post by MUK3SH on 2012-09-07
I am Trying qtsdk**.run**
But is Giving a error, disk is already inserted then also again and again Giving error. :( 
Please check screenshot.
[IMG]http://cdn.mspn.in/gallery/1347025224_3.png[/IMG]

---

### Post by darkod on 2012-09-07
Did you have separate /home partition in 10.04?

Also, be more specific how exactly you upgraded.
Did you install over the 10.04 or you used the option in the main menu to upgrade 10.04?

If I am not mistaken, there is no option to upgrade from the live cd. The option says something like Replace, not upgrade.

---

### Post by MUK3SH on 2012-09-07
I choosen , Please check it. [IMG]http://www.23hq.com/musante/photo/7614147/original[/IMG]

---

### Post by MUK3SH on 2012-09-07
> **darkod said:**
> Did you have separate /home partition in 10.04?

Also, be more specific how exactly you upgraded.
Did you install over the 10.04 or you used the option in the main menu to upgrade 10.04?

If I am not mistaken, there is no option to upgrade from the live cd. The option says something like Replace, not upgrade.
almost same screen was there. :( Now I cant find the files there and another error getting during installation of** .run** file.

---

### Post by darkod on 2012-09-07
Yes, they included that new option in 12.04, it wasn't there before. That's why I wasn't sure.

Unfortunately it looks like something went wrong and it's not showing you your data. Maybe it's only not showing it, maybe it was deleted.

You could try recovering the previous partitions with testdisk, but if you want to try that, stop using the computer from the hdd right away. Use it only in live mode running from the ubuntu cd.

You can download and run testdisk in live mode. Their step by step is here:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

If you have any questions after you do the Deeper Search and before you make any changes, take a screenshot and post here to ask. You should have internet access too in live mode.

---

### Post by SlugSlug on 2012-09-07
> **MUK3SH said:**
> mukesh@mukesh-NC872AA-ACJ-SG3740IL:~$ ls -l /home
total 8
drwxr-xr-x 84 mukesh mukesh 4096 Sep  7 17:50 mkj
drwxr-xr-x 25 mukesh mukesh 4096 Sep  7 18:48 mukesh
mukesh@mukesh-NC872AA-ACJ-SG3740IL:~$


so you have two users on that PC? Or have you chosen a new username..

check both folders for your data

---

