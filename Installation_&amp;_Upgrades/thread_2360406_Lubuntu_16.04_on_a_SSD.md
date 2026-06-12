---
title: "Lubuntu 16.04 on a SSD"
date: 2017-05-04
forum: Installation &amp; Upgrades
---

### Post by lubish on 2017-05-04
Currently I am on a Windows 7 on a Dell Inspiron 3520 which has a 250 GB Sandisk SSD drive that I added later. I would like to switch to Lubuntu 16.04 64-bit LTS. I have used Lubuntu before, but just not on a SSD. I would like to know what special thing (optimization for SSD) apart from the normal installation procedure will i have to do to install Lubuntu on my machine. Will it work out of the box on my system? What will happen if I don't do the optimization since I am afraid I might brick my Hard Drive. Also I am upgrading my RAM to 4 GB more later so do I need to do special settings for that. Your help will be greatly appreciated. Thanks.

---

### Post by artemkyz89 on 2017-05-05
Hello. I'm user ubuntu on ssd disk without special settings 3 years. Without swap.

---

### Post by oldfred on 2017-05-05
I do some of this:
 [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd) 

I now only really do noatime on mounting partitions and my own trim script so I have log file.

I just changed to using a tmpfs as I have a lot of RAM.
One other thing that saves writing small files to the SSD as long as you are not doing something that needs a lot of tmp space, since tmp is cleared on boot, is an fstab entry:But writing a DVD may need 4GB?
 tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0 

or, not sure of difference in parameters, I have seen both
tmpfs        /tmp        tmpfs    nodev,nosuid    0    0

---

### Post by efflandt on 2017-05-06
Each time you "access" a file (not just when you change it), the file system writes that time to a drive. But how often do you need to, or did you even know you could, get the time a file was accessed. So in /etc/fstab you just insert "noatime," in the part of the mount line, so that part of the line reads: noatime,errors=remount-ro

Normally the system will run /etc/cron.weekly/fstrim to TRIM (clear blocks of deleted files) any SSD for fastest writing. If you use a computer a lot, some people move fstrim script to /etc/cron.daily. There is no need to manually run fstrim.

My desktop is currently running 64-bit 16.10 from 512 GB mSATA SSD (from laptop that will not turn on) in a 2.5" SATA adapter. I also was using an old 80 GB Intel SSD for a back up boot system, but that currently has 16.04 in a 10 yr old laptop.

---

