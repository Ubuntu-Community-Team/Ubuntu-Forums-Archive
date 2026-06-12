---
title: "Partition Size is it correct???"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by pandurang_m on 2009-12-03
Hi I have installed Ubunto on 1TB HDD while installing I made 100GB for '/' and remaining for '/Home'...

I am not sure whether 100GB is enough or excess?? I read one article which says while installing if we make partition for '/Home' all our files are safe if we want to re-install Ubuntu. How much do I need to make for Ubuntu? 

I am confused about the applications and games installation...like if I install applications and games where they are installed? In Windows they are installed in "C" "Programs" folder.

---

### Post by wilee-nilee on 2009-12-03
zzz

---

### Post by Elfy on 2009-12-03
I would say that 100Gb is excess for /

[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by hal10000 on 2009-12-03
100GB for your root-partition ( / ) is far too much. Choose about 20-30GB.
For your homepartition you must name the mountpoint /home, not /Home. Linux (and other unixes) make a difference between upper case and lower case characters.

In Linux the most user applications are installed in under the /usr directory.
But if you install an application, the files that come with the application are installed in different directories (most of them usually under /usr).
For example, executable files can be found in /usr/bin, libraries in /usr/lib, documentation in /usr/doc variable parts of an application often can be found in /var, configuration files usually go to /etc

If you are new to ubuntu, then you should read the basic help from here: [https://help.ubuntu.com/9.10/index.html](https://help.ubuntu.com/9.10/index.html)

---

### Post by Ginsu543 on 2009-12-03
I also have Ubuntu (9.04) installed on a 1 TB drive in my rig and this is how I have it partitioned:

1) 25 GB ext4 / partition
2) 75 GB ext4 /home partition
3) 1 GB swap
4) 899 GB ntfs partition

Basically, I have the first 100 GB devoted to Ubuntu and the 900 GB left over set aside as a data drive formatted in ntfs so that I can access it in Windows as well as Ubuntu (this way I can share files between the two systems as well as easily make folders available as samba shares accessible by other computers on my home network).

Hope that helps.

---

### Post by cascade9 on 2009-12-03
My setup on my 1TB drive is (on debian lenny, not that makes a much difference)-
18.8GB - /
28.2GB - /home
3.8GB - Swap.
73.3GB - /mnt/archive
753.9GB - /mnt/media

If I was doing it all over again, I would probably make / a fair bit smaller, I'm only using 3.2GB. 100GB is way, way more than what you need. 

BTW, I use /mnt/media and /mnt/archive for the files I want to keep forever. You wont lose data on /home when you reinstall (unless you format the drive) but I prefer to have separate partitions for my archived data (drivers, programs, stuff like that) and my media, so I can format /home if I want.

---

