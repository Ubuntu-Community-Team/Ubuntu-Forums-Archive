---
title: "Short of disk space"
date: 2012-12-01
forum: Installation &amp; Upgrades
---

### Post by JohnMac on 2012-12-01
I used to have Ubuntu on a 50G partition and Mint on a 90G partition on my 160G hard drive. I am running out of disk space so I decided to delete Mint, preferring to run it as a virtual drive if I want to have a play. I still need more space in my Ubuntu partition and I haven't been able to increase the size of my ubuntu partition using gparted.

Is there a way of stretching mu Ubuntu partition or adding another home directory?

My system is a desktop as follows:

Dual AMD64 
2G RAM
Harddrive 160G

---

### Post by Bucky Ball on 2012-12-01
To resize the / partition (or any partition) it needs to be unmounted so you need to boot from a LiveCD and run Gparted, making sure partitions you want to manipulate are unmounted (right click/'Unmount'). 

It is impossible to unmount the / partition when you are booted into Ubuntu as Ubuntu is running from it. 

A solution for the /home partition could be to create that partition, not as /home but just as a data storage partition, copy all personal data from the existing /home (which is probably currently a directory /home inside the / partition) delete info then from the /home directory (but not the 'Desktop' directory or hidden files/folders!) and create symlinks to the directories on the /data partition.

This way, all installs of any OS/distro can use the /data partition as their 'fake' /home partition by linking to it with symlinks in the installs /home directory (basically, you are creating shortcuts to, say, a Documents folder on /data in your /home directory inside / rather that having the real thing, and its Gbs of data, in there sucking up space.

Symlinks are really easy to create when you know how. Essentially, you should really need no more than 15Gb for a Ubuntu install as all personal data is kept elsewhere. Also, this will mean if you irreparably break your install you can (theoretically) reinstall without killing all your personal data as it's safely on a different partition and the / partition only contains links to it.  

Hope all that makes sense! ;)

---

### Post by JohnMac on 2012-12-02
Ok thanks for for your help. I understand I need to use my livecd and gparted. I need to create a /data directory in my spare partition and then create symlinks pointing to it. Exactly what I need, I'll have to find a howto.

---

### Post by ibjsb4 on 2012-12-02
Data partition

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=data+partition&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by Bucky Ball on 2012-12-02
Creating symlinks:

[http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html](http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html)

Good luck! ;)

---

### Post by irv on 2012-12-02
> **JohnMac said:**
> Ok thanks for for your help. I understand I need to use my livecd and gparted. I need to create a /data directory in my spare partition and then create symlinks pointing to it. Exactly what I need, I'll have to find a howto.

Why don't you post a screen shot of your hard drive as seen by gparted and someone can give you a step by step on what to do. I have deleted partitions and resize other using the free space that I made available.

---

### Post by oldfred on 2012-12-02
In my data partition I have all the standard folders and others that I want. Then with one line I can link all of them.

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

    
```
fred@fred-Precise:~$ cd /mnt/data
fred@fred-Precise:/mnt/data$ ls
Calibre Library  gnu           ISO       lost+found  PicasaDocuments  Videos
Documents        google-earth  itrade    mozilla     Pictures         workspace
Downloads        grampsdb      jstock    Music       Projects
eclipsetrader    icarra2       kmymoney  PDF         spyderdata

```

---

