---
title: "Package Manager Error"
date: 2019-09-11
forum: Installation &amp; Upgrades
---

### Post by perkanator on 2019-09-11
Hello I am getting the following error when running apt-get update:

```
E: Problem parsing dependency 21
E: Error occurred while processing znc-perl (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bionic-updates_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```

Any help would be appreciated.

Thank you,

Jason

---

### Post by Skaperen on 2019-09-11
exactly what commands did you do to get this?  did it include an update?   please put the commands in code tags ending with **[/code]** and beginning with **[code]**.

---

### Post by perkanator on 2019-09-11
Yeah I am not sure see below:

```
$ sudo apt-get update
Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://archive.canonical.com/ubuntu bionic InRelease                     
Get:3 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]    
Get:4 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]   
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB] 
Fetched 252 kB in 1s (274 kB/s)                                       
Reading package lists... Error!
E: Problem parsing dependency 21
E: Error occurred while processing znc-perl (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_bionic-updates_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.


```

---

### Post by Bashing-om on 2019-09-11
perkanator; Hello -

> 
E: The package lists or status file could not be parsed or opened.


MergeLists are a working tool of apt, part of the way it keeps track of which packages are in which repositories. It's the gears of a text-based database that apt relies upon. When corrupted, they can be safely deleted. Apt will recreate them during the next apt update.

Try:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt update

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by perkanator on 2019-09-11
Bashing-om,

That seemed to work, thanks!!!!

---

### Post by Bashing-om on 2019-09-11
perkanator;  Great :P

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

