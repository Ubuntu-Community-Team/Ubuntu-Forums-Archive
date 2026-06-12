---
title: "how to create a backup"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by c2tarun on 2010-11-07
i have three partitions on my laptop.
one contains ubuntu and other two my personal data.

i m using ubuntu since past three months. i installed many packages, softwares and libraries. 
i was wondering if something wrong happens and i have to format my whole drive containing ubuntu, is there a way that i can backup all my packages and softwares.

i tried to look at the /var/cache/apt/archives as it contains setup of all the packages that i installed using apt-get package manager. i tried to copy and save them, but now i was thinking that during a single package installation it installs many libraries used to support that applications. so i think this copying method will not work.
any suggestions please.

---

### Post by dino99 on 2010-11-07
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

### Post by Barriehie on 2010-11-07
I use rsync daily to backup / , on it's own drive, and $HOME, also on it's own drive to a third drive.  You can use this as part of your backup strategy to generate a list of installed packages.
```

dpkg --get-selections | grep -v deinstall > ***some_path/MyPackages-$(date +%m%d%y)***
```

---

### Post by Megaptera on 2010-11-07
... and possibly consider Remastersys CD/DVD

guide here: [http://ubuntuforums.org/showthread.php?t=1514043](http://ubuntuforums.org/showthread.php?t=1514043)

---

### Post by HermanAB on 2010-11-07
Hmm, yesh...

As you get to know Linux better, re-installing it becomes easier.  I can install a machine from scratch in about 30 minutes, with everything I normally need.  Therefore, for me to make a complete system backup is a total waste of time - eventually you will be in the same position.

I always advise people to backup their data only and forget about backup of the rest of the system, since making the backups take a lot of time and restoring it takes even longer.

---

### Post by c2tarun on 2010-11-07
> **HermanAB said:**
> Hmm, yesh...

As you get to know Linux better, re-installing it becomes easier.  I can install a machine from scratch in about 30 minutes, with everything I normally need.  Therefore, for me to make a complete system backup is a total waste of time - eventually you will be in the same position.

I always advise people to backup their data only and forget about backup of the rest of the system, since making the backups take a lot of time and restoring it takes even longer.

i agree ubuntu installation is very easy. but the problem is all my applications are installed from the internet. it takes lot of time in downloading and updating. so i just wanted to make backups to avoid any downloading.

---

### Post by geoffmcc on 2010-11-07
I have never used it - was mentioned in a post a little while ago

APTonCD

> APTonCD is a tool with a graphical interface which allows you to create one or more CDs or DVDs (you choose the type of media) with all of the packages you’ve downloaded via APT-GET or APTITUDE,

---

### Post by NertSkull on 2010-11-07
> **c2tarun said:**
> i agree ubuntu installation is very easy. but the problem is all my applications are installed from the internet. it takes lot of time in downloading and updating. so i just wanted to make backups to avoid any downloading.

I haven't done this yet.  Been meaning to look into it.  But there's a way to kind of make your own install CD/DVD that includes all the programs your normally use.  So download them all once, and then each time you re-install it almost takes it exactly back to the way you had it.  

Then you just backup your data and keep that DVD handy.  And your good to go.

Just something to think about.

Also, for data backup I recommend duplicity.  Its a great program.


**Edit: This may start you looking in the right direction.

[https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization)

---

