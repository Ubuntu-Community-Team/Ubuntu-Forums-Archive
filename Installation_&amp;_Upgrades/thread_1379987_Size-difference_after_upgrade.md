---
title: "Size-difference after upgrade"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by erlend_sh on 2010-01-13
I'm the kind of guy who actually enjoys watching an upgrade-meter move on its honorable path to improve my computer. Meanwhile however, today I realized I'm also reluctant to fattening up my hard drive, and I don't know whether or not most updates do that!

I suppose there's no such thing as a [Ubuntu] module of sorts that would show the size difference after an upgrade? The thing is, it says 'the total of this upgrade is 37mb', but I reckon a lot of these megs will overwrite other megs, so I'm curious to know if I've been sized up or down after an upgrade.

I hope I didn't noob out bigtime in my first post here :). Thrilled to be an Ubuntu citizen!

---

### Post by tommcd on 2010-01-13
> **erlend_sh said:**
> 
I suppose there's no such thing as a [Ubuntu] module of sorts that would show the size difference after an upgrade? The thing is, it says 'the total of this upgrade is 37mb', but I reckon a lot of these megs will overwrite other megs, so I'm curious to know if I've been sized up or down after an upgrade.

If you want to see how much space is being used on each of your partitions, simply open a terminal (applications > accessories > terminal) and run:
```
df -h
```
The **df** command reports file system disk space usage. The **-h** option is for "human readable". 
As an example, here is df -h on my Slackware system:
```

bash-3.1$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6              13G  5.9G  6.4G  48% /
/dev/sdb5             200G   96G   94G  51% /data
tmpfs                1006M     0 1006M   0% /dev/shm
bash-3.1$ 

```
The /dev/sda6 is my Slackware root partition. The /dev/sdb5 is my /data partition for all my music, videos, files, etc.

If you want to see an in depth breakdown of how much space each directory on your system is using, run:
```
sudo du -csh /*
```
This may take a minute or so to run.The **du** command is for disk usage. To see what the **-csh **options do, read the du manual by running **man du** in the terminal.
You will see an output something like this:
```

bash-3.1# du -csh /*
12M	/bin
15M	/boot
96G	/data
172K	/dev
12M	/etc
874M	/home
93M	/lib
13M	/lib64
16K	/lost+found
64K	/media
44K	/mnt
50M	/opt
du: cannot access `/proc/11190/task/11190/fd/3': No such file or directory
du: cannot access `/proc/11190/task/11190/fdinfo/3': No such file or directory
du: cannot access `/proc/11190/fd/3': No such file or directory
du: cannot access `/proc/11190/fdinfo/3': No such file or directory
0	/proc
124K	/root
15M	/sbin
4.0K	/srv
0	/sys
50M	/tmp
4.5G	/usr
167M	/var
102G	total
bash-3.1# 

```
Don't worry if you get errors like I got in this example. The /proc directory is a virtual directory that does not actually contain anything.
The reason for running the du command with sudo is so you don't get any "permission denied" messages for directories that need super user (or root) access to see them. Using the **du** command will not make any changes to your system.

Once in a while, it is a good idea to run in the terminal:
```

sudo apt-get autoclean

```
This will remove all stored .deb packages that are old and can no longer be downloaded. This will free up a bit of space.
Write back if you need more help.

And welcome to the Ubuntu forums!

---

