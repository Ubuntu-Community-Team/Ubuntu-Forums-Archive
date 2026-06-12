---
title: "Partitioning for clean install"
date: 2018-01-27
forum: Installation &amp; Upgrades
---

### Post by ThanasisKant on 2018-01-27
Hello. i want to install ubuntu as the only OS in my laptop. I tried to copy guides talking about partitioning during installation and this is what i have. You think is it valid or do i have anything wrong? Also i know most of the partitions i make arent needed but i want to make them just for educational reason ( example the boot partition)[IMG]https://imgur.com/uqOebBJ[/IMG][IMG]https://imgur.com/vQ0NTgr[/IMG]
[https://imgur.com/uqOebBJ](https://imgur.com/uqOebBJ)
[https://imgur.com/vQ0NTgr](https://imgur.com/vQ0NTgr)

---

### Post by oldfred on 2018-01-27
I do not recommend all the separate partitions.
Depending on your use you may fill one or the other partitions and have to rearrange them.
Much better to just have / and then perhaps /home.
But I have /home inside / and a very large /mnt/data partition on my HDD.

This is my 16.04, originally a clean install and regularly housecleaned system.

```
fred@Z170N:~$ sudo du -hx --max-depth=1 / 2> /dev/null
[sudo] password for fred: 
16M    /etc
16K    /lost+found
12K    /media
897M    /lib
4.0K    /snap
6.5G    /usr
2.7G    /home
13M    /bin
4.0K    /lib64
4.0K    /srv
116K    /mnt
1.4G    /var
196M    /boot
4.4M    /root
4.0K    /opt
4.0K    /cdrom
14M    /sbin
12G    /
```

---

### Post by VMC on 2018-01-27
You don't have '/lib32' folder? Interesting. I do stock install and always seem to have'/lib32'. Mine takes up 5.7M

---

### Post by oldfred on 2018-01-27
32 bit vs 64 bit? Otherwise do not know.
I do not typically install anything that is 32 bit anymore.

---

### Post by ThanasisKant on 2018-01-27
i dont even know what this partition is for. i am new user you see.

---

### Post by ThanasisKant on 2018-01-27
> **oldfred said:**
> 32 bit vs 64 bit? Otherwise do not know.
I do not typically install anything that is 32 bit anymore.

64 bit. i saw an article that the 32 and 64 bit make small to none diference in the cpu soource etc etc so i went with the 64 bit

---

### Post by VMC on 2018-01-27
> **oldfred said:**
> 32 bit vs 64 bit? Otherwise do not know.
I do not typically install anything that is 32 bit anymore.
I always install 64bit, but '/lib32' is always there. Only thing in there are [COLOR=#242729][FONT=Arial, Helvetica Neue, Helvetica, sans-serif]"Shared Object" files.[/FONT]
[FONT=Arial, Helvetica Neue, Helvetica, sans-serif] I'll have to check on next development install.[/FONT]

[FONT=Arial, Helvetica Neue, Helvetica, sans-serif]As far as the OP is concerned, I only install on "/" root partition. I know others have also recommend "/home" as well.[/FONT][/COLOR]

---

### Post by Impavidus on 2018-01-28
The directories /bin, /etc, /lib, /lib32 (if existing), /lib64 (if existing), /root and /sbin should be on the root partition. These directories are required for booting into recovery mode, when other filesystems don't get mounted. Other than that, you're free to create as many partitions as you like, but apart from /home they usually cause only trouble.

---

