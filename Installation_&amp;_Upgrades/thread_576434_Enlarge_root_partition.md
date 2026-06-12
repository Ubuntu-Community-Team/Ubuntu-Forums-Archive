---
title: "Enlarge root partition"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by oasiscity on 2007-10-15
Hello,

I have "/" as seperate partition, and according to installation guidelien I alloate to it around 250M disk space.  

Now I have problem with normal upgrading a kernel image. it says the device is full and the operation stops.

So the question, is there some way that I can enlarge my root partition without a re-installation of the system?

thanks.

---

### Post by scrooge_74 on 2007-10-15
It seems you got yourself into a little mess, next time use at least 2 GB for everything under / partition and /home in a seperate.

If you have your Live CD at hand boot from it and start Gparted so you can rezise the partitions, remember to backup any important data first.

---

### Post by krang on 2007-10-15
I have somehow the same problem: It says, that my /boot partition is too small for 7.10. Never thought of having a big /boot partition for any OS...
Can I resize the /boot partition with some space of /home with gparted without getting my data lost? I do I have to format anything after resizing? I dont' like to get my data on /home lost...... And I don't like to backup 60GB...

---

### Post by scrooge_74 on 2007-10-15
There should not be any problem, but I rather backup before touching my /home partition

Remember that your / partition holds a lot of item.  If you need to make some space you can always delete downloaded packages

sudo apt-get autoclean

also in /var/log you can always delete does old logs in there

---

### Post by krang on 2007-10-15
There's still some space on /home left so I want to transfer space from /home to /boot... Just some MB... ;)
Hum, maybe I can backup it on my small portable HDD... :x

---

### Post by scrooge_74 on 2007-10-15
Better safe than sorry.  Still remember to leave space on your /home partition, if you run out of space there you won't be able to log in as your user, so keep that in mind too

---

### Post by oasiscity on 2007-10-15
> **scrooge_74 said:**
> It seems you got yourself into a little mess, next time use at least 2 GB for everything under / partition and /home in a seperate.

If you have your Live CD at hand boot from it and start Gparted so you can rezise the partitions, remember to backup any important data first.

you are right. I misinterpreted the following text:

" The root partition / must always physically contain /etc, /bin, /sbin, /lib and /dev, otherwise you won't be able to boot. Typically 150–250 MB is needed for the root partition. "
from  [https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/directory-tree.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/directory-tree.html)

Stupid mistake :-) A re-installaiton may solve it the best...

---

### Post by scrooge_74 on 2007-10-15
Most likely to better reinstall if you have not make to many changes to your system

---

### Post by krang on 2007-10-15
> **scrooge_74 said:**
> Better safe than sorry.  Still remember to leave space on your /home partition, if you run out of space there you won't be able to log in as your user, so keep that in mind too
that's for sure, there are still 10GB left  and I don't want to transfer them to /boot ;)
gonna give it a try soon

---

### Post by scrooge_74 on 2007-10-15
Sure 2 GB should be more than enough, I currently have 2.5 GB set aside for root, but I am really using less than 1 GB. But true I have a minimal Debian install with Xfce4 so I am not rellay using to much space

---

