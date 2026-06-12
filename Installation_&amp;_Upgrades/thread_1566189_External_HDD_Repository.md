---
title: "External HDD Repository?"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by Linuxson25 on 2010-09-02
Hi

I use AptonCD to make regular backups of all apt installed packages, and store them on my external USB HDD. Is there a way that I can add that specific folder with all the packages on the external to my software sources list? I know you can add CDROM's. It's just really a shlep having to individually double click and install each and every one, as I am still a noob at this thing...lol. It would just make life easier, as Synaptic would then sort out all dependencies, cause it seems that you need to install them in a certain order. Just double clicking the package files and installing them that way, normally leaves me with a "dependencies unsatisfied" error

Thanx

---

### Post by lechien73 on 2010-09-02
You can add a line to the /etc/apt/sources.list file, which should do this for you.

For the following example, I'm assuming the following: you're using Lucid, your USB hard disk is mounted on /media/disk, and the APTonCD repository is in the folder "repo/ubuntu".

To edit the /etc/apt/sources.list file, type:

```
gksu gedit /etc/apt/sources.list
```

Add the following line:

```
deb file:/media/disk/repo/ubuntu/ lucid main restricted universe multiverse

```

Save the file and quit from gedit. Then, with your USB disk connected and mounted, type:

```
sudo apt-get update
```

Your USB disk will now be added as a local repository.

---

### Post by Linuxson25 on 2010-09-02
Thanx lechien73

Not sure if there is a big difference between physically editing the source.list file, or adding the source with Synaptic? I tried the latter, and it won't accept. Error pops up all the time: [http://pastebin.com/GWXk878s](http://pastebin.com/GWXk878s)

PS: I am using karmic

---

### Post by lechien73 on 2010-09-02
Could you post the output of:

```
ls /media/AnthonyHDD/ubuntuBackup/20100828/dists/karmic
```

It would be interesting to see what is in that directory.

Thanks

---

