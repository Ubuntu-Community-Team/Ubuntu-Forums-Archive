---
title: "Install second 18.04 installation"
date: 2019-06-27
forum: Installation &amp; Upgrades
---

### Post by jmcgee on 2019-06-27
I have a broken 18.04 installation.  Desktops either will not load, or if they do I don't have permissions to run programs like synaptic.

So I used the guide at
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
to create a new partition on my SSD for home.

I created 18.04 startup USB disk using Startup disk creator.  I boot off that and try installing 18.04 beside existing 18.04 installation.

#1 Should I create a separate partition to hold the second Ubuntu installation?

#2 Why does installation complain no boot disc when I point it to:
/sdb2


    ```
mythuser@amethi:/$ df -h
    Filesystem      Size  Used Avail Use% Mounted on
    udev            7.8G     0  7.8G   0% /dev
    tmpfs           1.6G  3.4M  1.6G   1% /run
    /dev/sdb2       128G   30G   92G  25% /
    tmpfs           7.8G  8.8M  7.8G   1% /dev/shm
    tmpfs           5.0M  4.0K  5.0M   1% /run/lock
    tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
    /dev/loop0       89M   89M     0 100% /snap/core/7169
    /dev/loop9      152M  152M     0 100% /snap/gnome-3-28-1804/55
    /dev/loop12      36M   36M     0 100% /snap/gtk-common-themes/1269
    /dev/loop2      3.8M  3.8M     0 100% /snap/gnome-system-monitor/91
    /dev/loop4      141M  141M     0 100% /snap/gnome-3-26-1604/88
    /dev/loop1      152M  152M     0 100% /snap/gnome-3-28-1804/59
    /dev/loop3       15M   15M     0 100% /snap/gnome-characters/288
```

---

### Post by rbmorse on 2019-06-27
Just to confirm, this is not dual boot setup and you're using the machine in legacy BIOS mode?

---

### Post by jmcgee on 2019-06-27
It is not dual boot yet, and yes, using machine in legacy bios mode.

---

### Post by yancek on 2019-06-28
Is /dev/sdb2 where your current non-functioning Ubuntu is?  Is it your intention to overwrite and/or delete all data currently on that partition?  If so, select that partition during the install and select the option to format.  If you do not want to overwrite everything on that partition, then create unallocated space somewhere on the drive on which to install your new Ubuntu.  Have you created a new partition for your /home on the old Ubuntu?? and where is it?

---

### Post by jmcgee on 2019-06-28
The existing Ubuntu install is on dev/sdb2.  I want to keep that running.  And install another copy of Ubuntu. Once I get that configured like the non-functioning one, I will delete the non-functioning version.  

I created a new partition on /sdb5 but deleted it. I could not get Ubuntu to install there.

/home is on dev/sdb4

---

