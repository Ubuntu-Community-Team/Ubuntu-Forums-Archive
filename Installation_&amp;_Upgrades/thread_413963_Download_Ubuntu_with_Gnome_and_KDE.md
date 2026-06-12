---
title: "Download Ubuntu with Gnome and KDE"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by xlinuks on 2007-04-19
Hi,
Is there any hope that we'll have any time soon a possibility to download a Ubuntu with both KDE and Gnome desktops (kind of DVD version)?
We all know that that if one chooses Gnome you don't get such apps like Amarok and if one chooses KDE you don't get GIMP and alike, not to mention the importance of all the other _important_ apps in both desktops without which is pretty hard to live.
One could use the DVD to install all additional packages (and development tools, g++ and alike). I would propose this option were available as an "alternate install". I'm sure there were much demand on it.

---

### Post by aysiu on 2007-04-19
There already is a DVD version:

You can download it here:
[http://nginyang.uvt.nl/](http://nginyang.uvt.nl/)

---

### Post by ShadowOps on 2007-04-19
Whats the point when you can just install those packages via apt or from the package manager?

---

### Post by xlinuks on 2007-04-19
The point is that the people I want to share the new Ubuntu 7.04 don't have an internet connection and some of them have a slow internet connection. Actually there are still many people who have to deal with it.
So I just download the whole "DVD", make a lot of copies, and give'em to my friends saying "here is anything you need, all the apps, the compiling tools and so on, you don't have to spend twelve hours downloading the KDE desktop (or anything), it's already bundled".
Its a great relief for _all_ people with less than 512 kbps connection, and there's still a lot of them. At least in my country.
Thanks aysiu, but it looks like Feisty ain't there yet.

---

### Post by aysiu on 2007-04-19
> **xlinuks said:**
> 
Thanks aysiu, but it looks like Feisty ain't there yet. Try this one:
[http://cdimage.ubuntulinux.org/dvd/current/](http://cdimage.ubuntulinux.org/dvd/current/)

---

### Post by xlinuks on 2007-04-19
I'll buy you a beer! :)

---

### Post by jetpeach on 2007-04-19
Thanks, this is exactly what I need as well - it helps a lot to have both when you have 4 different computers, some with gnome, some with kde, some with both.  apt-get method can take a very long time when doing it on each if they each have to download...

One thing I don't understand - why doesn't Ubuntu just release a torrent list first so their servers don't get so hammered? Also, how much money do they spend on bandwidth that could be saved if they encouraged people to download the CDs using bittorrent and use them to upgrade, instead of using apt-get upgrading? I want as much money as possible to be spent on developers, and with all the gigs and gigs of downloads Ubuntu spends on bandwidth, it much cost a pretty penny.

I can't even find instruction on how to use the CD to upgrade. Or how about how to set up a local repository so all machines could be updated over a LAN instead of using slow web?

---

### Post by aysiu on 2007-04-19
Maybe [this](http://ubuntuforums.org/showpost.php?p=1558849&postcount=2) might help.

If you want to upgrade by CD: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.edgy
sudo apt-cdrom add
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by jetpeach on 2007-04-20
> **aysiu said:**
> Try this one:
[http://cdimage.ubuntulinux.org/dvd/current/](http://cdimage.ubuntulinux.org/dvd/current/)

Well, my DVD download finally finished, but it now appears this dvd only has the deb packages on it for regular ubuntu, and does not include those for Kubuntu (packages such as Kopete,  and even Amarok are not on the DVD). So perhaps a combination DVD does not exist [yet]?

jet

---

