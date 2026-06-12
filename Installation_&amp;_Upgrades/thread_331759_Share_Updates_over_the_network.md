---
title: "Share Updates over the network"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by CameronCalver on 2007-01-05
Hello i have  some computers and a file server.
I feel it is pointless and a waste of downloading installing all the updates on all of my computers so i was wondering if i could point apt-get and synaptic to a folder on the file server ( threw ssh)  so i can make the file server automatic download updates and put them on the shared folder so on the computers on the network it doesnt need to re download the files all it needs to do is install then ? is this possible

---

### Post by xiaoxin on 2007-01-05
I think this is what you are looking for
[http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher]("http://www.debuntu.org/how-to-set-up-a-repository-cache-with-apt-cacher")

---

### Post by CameronCalver on 2007-01-05
yeh that looks like the thing but my server is running dapper so ill update it and get back to you if it works or not

---

### Post by CameronCalver on 2007-01-07
when i try to restart apt-cacher i get 
```
server@ubuntu:~$ sudo /etc/init.d/apt-cacher restart
Restarting Apt-Cacher: apt-cacher--- /usr/sbin/apt-cacher: Fatal: Unable to open /var/log/apt-cacher/error.log
.

```

---

### Post by xiaoxin on 2007-01-08
does the /var/log/apt-cacher/error.log file exist?

---

### Post by CameronCalver on 2007-01-08
yes it does and il do a reistall but you give me a complete config file

---

### Post by CameronCalver on 2007-01-08
is this even possible to share updates

---

