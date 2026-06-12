---
title: "Partitioning Scheme"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by carbonbased on 2010-01-16
I'm thinking of trying two distros. My first is Ubuntu 9.10 taking 1/2 of my hda1 (160gb drive), so looking at putting OpenSUSE on hda2.  When I installed Ubuntu I gave /Home to hdb1 (500gb).

Anyone know whether it would it work for /Home to be shared by the two distros? All partitions are Ext4.

---

### Post by viralmeme on 2010-01-16
> **carbonbased said:**
> .. Anyone know whether it would it work for /Home to be shared by the two distros? All partitions are Ext4.
I doubt it as the user config files are stored in home and risk getting overwritten by each distro. You best bet is to have to share a partition between each distro ..

---

### Post by carbonbased on 2010-01-16
> **ymitchell said:**
> I doubt it as the user config files are stored in home and risk getting overwritten by each distro. You best bet is to have to share a partition between each distro ..

E.g., ...?

---

### Post by oldfred on 2010-01-16
Often the user settings are different.

What you can do it create a data partition with all your data so /home only has the user settings. You then can mount all the data in both systems.

I followed one of the comments here.
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)

# Entry for /dev/sda7 :
UUID=defec4d7-3e36-4938-b5de-b2016b2dee27  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2  

ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Documents
ln -s /usr/local/fred/data/Pictures
ln -s /usr/local/fred/data/Videos
etc for every folder in /home
I cannot remember if I had to chown the data directory or if the mount gave me enough privileges.

---

