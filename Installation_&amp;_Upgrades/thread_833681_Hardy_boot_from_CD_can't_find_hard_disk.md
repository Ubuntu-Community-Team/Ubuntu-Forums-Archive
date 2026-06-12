---
title: "Hardy boot from CD can't find hard disk"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by Xodarap on 2008-06-18
I am attempting to upgrade from Gutsy to Hardy, but the installer can't find my hard disk. If I boot not from CD it works, so I can't figure out what's going on. I don't even know how to begin to troubleshoot something like this.

From the terminal you can get to from booting off CD:

ubuntu@ubuntu:~$ ls /dev/hd*
ls: cannot access /dev/hd*: No such file or directory

ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
tmpfs                   517548     16004    501544   4% /lib/modules/2.6.24-16-generic/volatile
tmpfs                   517548     16004    501544   4% /lib/modules/2.6.24-16-generic/volatile
varrun                  517548       104    517444   1% /var/run
varlock                 517548         0    517548   0% /var/lock
udev                    517548        28    517520   1% /dev
devshm                  517548        12    517536   1% /dev/shm
tmpfs                   517548        20    517528   1% /tmp
df: `/home/ubuntu/.gvfs': Transport endpoint is not connected


See [http://paste.ubuntu.com/21287/](http://paste.ubuntu.com/21287/) for the output of ubiquity --debug --desktop %k gtk_ui

Thanks in advance for your help!

---

### Post by Pumalite on 2008-06-18
Remove all third parties from your sources.list, use Alternate CD if you are using CD. Use official method of upgrading:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
(have Gutsy fully update before you attempt upgrade)

---

### Post by Xodarap on 2008-06-19
I used the recommended way of upgrading (through the update manager) which trashed my install. It now boots to the command line (ash).

I wanted to wipe everything and just install from scratch, so I booted from CD, but when I do so it can't seem to find my HDD. Do I need to run some command from the old (destroyed) install to let it know that I want to overwrite the old install?

---

### Post by Pumalite on 2008-06-19
First make sure your drive is recognized and well configured in your BIOS.

---

### Post by avtolle on 2008-06-19
Are you able to get to a console and do```
sudo fdisk -l
```(that is the lowercase letter, not the number)? I've a feeling that the unsuccessful upgrade did just enough to change the name of the hdd as seen by the system. Post the results of the above, too, if you would.

---

### Post by avtolle on 2008-06-19
Looking at the link, it appears no partitions were found on the HDD; most interesting.

---

### Post by SchitzoJoe on 2008-06-19
I had this problem, what fixed it for me was changing the jumper options on your HDD to "Cable Select." They might be on "Master" or "Slave".

Check this out: [http://www.ehow.com/how_6031_change-master-slave-designation.html]("http://www.ehow.com/how_6031_change-master-slave-designation.html")

---

### Post by Xodarap on 2008-06-20
Thanks schitzo, that worked for me!

Weird bug though...

With regards to avtolle's question, fdisk -l produced nothing.

---

