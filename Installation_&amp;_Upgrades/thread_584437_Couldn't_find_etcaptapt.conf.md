---
title: "Couldn't find /etc/apt/apt.conf"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by sxjast on 2007-10-21
Hello everyone,

I'm new to Ubuntu and I installed Feisty Fawn few days back. Everything is going well until I find my first problem. I'm trying to do apt-get update and is failing on "Dynamic MMap ran out of memory". I did some googling and found out I may need to increase the cache memory size. I tried to open /etc/apt/apt.conf file and I couldn't find the file. I wonder what happened to the file, how come it got deleted? I thought of creating a new file and did gedit apt.conf at that directory level and I tried to save the file but it is saying I don't have permissions to do so? Can someone guide me?

Thanks,
sxjast

---

### Post by oomar on 2007-10-21
if creating the new file will fix it... then you must have root privaledges to save a file there... type gedit in the terminal while in sudo mode

---

### Post by ruibernardo on 2007-10-21
You can try to create an empty /etc/apt/apt.conf file like oomar said, but this file does not exist by default in Ubuntu, although you can create it to add some custom settings to APT. You should search for another reason for why this is happening

---

### Post by sxjast on 2007-10-21
Thanks for your responses. 

Even in sudo mode, I see I don't have privileges to create apt.conf file in /etc/apt. I tried both gedit and vi. It's really strange.:confused:

---

### Post by ruibernardo on 2007-10-21
Check if you have a /etc/apt/ directory:
```

ls -la /etc/apt
```This will list all the files in the /etc/apt/ directory. Then create an empty apt.conf file in it with:
```

sudo touch /etc/apt/apt.conf
```

---

### Post by sxjast on 2007-11-13
Sorry for the late response. This touch cmd helped me.

---

