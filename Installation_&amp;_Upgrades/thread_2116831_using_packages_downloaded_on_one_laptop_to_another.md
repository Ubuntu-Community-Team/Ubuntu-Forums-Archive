---
title: "using packages downloaded on one laptop to another laptop"
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by jamesbon on 2013-02-16
I have upgraded Ubuntu 11.10 (amd64) to 12.04 (amd64) on one of the laptops I have, I some  **machines  which are not connected on any network** and they are  running Ubuntu  11.10 (amd64),

 I want to use the packages downloaded on the first laptop on the other machines  so that both have Ubuntu 12.04 I checked on first laptop (now running 12.04 ) downloaded upgrades are residing in /var/cache/apt/archives
I have copied them  those packages from laptop to a USB 


On the other machines  I have tried putting those package files into /var/apt/cache/archives
and then just firing the upgrade process do-release-upgrade, and unfortunately this does not work and rather than picking the packages from
/var/cache/apt/archives

it goes to some thing like

[http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main qemu-utils amd64 1.0+noroms-0ubuntu13 [353 kB]   

and so on and is downloading things (where as there is not network connection)

Now what I want to know is how do I make sure do-release-upgrade uses these copied packages from USB  and does not attempt to download  700 mb of updates** because there is no network connectivity on those machines.**
 If there is a way in this situation let me know.

---

### Post by zvacet on 2013-02-20
You can put all packages from /var/cache/apt/archives to one folder.Put folder on stick and transfer it to other comp.you can put folder with packages in your home directory and from then go inside of it and run 

```
sudo dpkg -i *deb
```

You can also use [Aptoncd.]("http://aptoncd.sourceforge.net/")

---

