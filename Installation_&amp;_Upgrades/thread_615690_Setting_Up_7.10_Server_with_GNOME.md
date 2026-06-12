---
title: "Setting Up 7.10 Server with GNOME"
date: 2007-11-17
forum: Installation &amp; Upgrades
---

### Post by prodonjs on 2007-11-17
I am working on a project for a Linux course and have decided to build an FTP server using Ubuntu Gutsy Gibbon.

My goal for this project is to build a server inside a virtual machine that I can host on my family's home PC. What I want to do is be able to remotely control this server from here at college to download and distribute torrents. Then, I want to be able to move the torrents into a private FTP share that I can access from here, upload to and download from.

Here the main two features I would like:
1) The ability to have GNOME since I'm not an expert on knowing where all the important configuration scripts are and having the GUI can make certain tasks much more simple. Also, I'm not sure if I'd be able to do anything with torrents without the GUI.
2) A remote administration feature. I would love to be able to access this server from a secure HTTP connection to do some basic management tasks (while I'm at college away from where the server will be hosted).

Basically, I wanted to get a guideline to follow when setting up something like this. Is there anywhere I could go look to find out how to do some of these things?

Thanks in advance for any assistance.

---

### Post by zvacet on 2007-11-17
To get GNOME you have to add repositories

```
sudo gedit /etc/apt/sources.list
```

and add 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty universe multiverse

Save and close.

```
sudo aptitude install ubuntu-desktop
```

---

