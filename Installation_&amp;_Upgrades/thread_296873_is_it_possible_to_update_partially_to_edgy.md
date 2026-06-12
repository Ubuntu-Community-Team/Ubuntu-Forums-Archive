---
title: "is it possible to update partially to edgy?"
date: 2006-11-10
forum: Installation &amp; Upgrades
---

### Post by eeried on 2006-11-10
Hello,

I'm not sure I really like Xubuntu edgy but I'd like to know if it's possible to update some packages, such as Xfce and particular apps such as Firefox? I don't want to update to the new kernel which seems to make things more complicated for me as i explained elsewhere (resolution problems).

Could I use a sources.list including the edgy repositories?

cheers

---

### Post by BLTicklemonster on 2006-11-10
You'd think that they would find a way to let you incorporate "the best of" from edgy to dapper. Good luck.

---

### Post by twsnnva on 2006-11-10
You would use apt pinning.

1) Add both dapper and edgy repos to /etc/apt/sources.list
2) Create /etc/apt/preferences.
```

Package: *
Pin: release a=dapper
Pin-Priority: 900

Package: *
Pin: release a=edgy
Pin-Priority: 800

```
3) Run apt-get update
4)apt-get install firefox/edgy

---

### Post by eeried on 2006-11-10
Oh great, thanks twsnnva, I'll try this straight away.

This pinning thing reminds of the good time of Libranet (a debian-based distro that vanished early this year)!

Let's find out if it works in Xubuntu!

Do you actually type
```
apt-get install firefox/edgy
```
?

---

### Post by twsnnva on 2006-11-10
Yes, you would run that command.

There are 2 ways to install packages from the edgy repos.

Running "apt-get install firefox/edgy"
This will try to install firefox from edgy, but will not try to download any dependencies from edgy, so it may fail.

Running "apt-get -t edgy install firefox"
This will download firefox and all necessary dependencies from edgy.

---

### Post by eeried on 2006-11-10
This is the output of my apt-get update
```
E: Dynamic MMap ran out of room
E: Error occurred while processing mpg123-oss-i486 (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/fr.archive.ubuntu.com_ubuntu_dists_edgy_multiverse_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.

```

I did an ```
apt-get clean
``` and again ```
apt-get update
```. This is what df -h says: 
```
/dev/hda8             2.0G  1.8G  170M  92% /
```

Do you think all the above errors are due to lack of room ?
I'm going to install Xubuntu on a bigger partition with a separate /home partition.

cheers

---

### Post by twsnnva on 2006-11-10
You are running low on disk space, so it is possible. Before you reinstall though, try running "apt-get -o APT::Cache-Limit=16500000 update".

---

