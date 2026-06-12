---
title: "upgrading to 12.04"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by vishalnshekhar on 2012-04-26
I have ubuntu 11.10 and i want to upgrade it to 12.04 which is the best way to upgrade:
1) By update manager
2) By downloading .iso and format previous one, install ubuntu 12.04
3) By downloading iso file and while installing it give the option to upgrade from 11.10 to 12.04 as in this way our files are save.
 
Is upgrading by option 1 and 3 has same effect???

---

### Post by raja.genupula on 2012-04-26
yes 1 and 3 options will give you the same one .
2 one is not come under upgrade , it will be a fresh install . 

among the 1 and 3  , i will vote for the 1st way .

---

### Post by c2tarun on 2012-04-26
> **vishalnshekhar said:**
> I have ubuntu 11.10 and i want to upgrade it to 12.04 which is the best way to upgrade:
1) By update manager
2) By downloading .iso and format previous one, install ubuntu 12.04
3) By downloading iso file and while installing it give the option to upgrade from 11.10 to 12.04 as in this way our files are save.
 
Is upgrading by option 1 and 3 has same effect???
 
 
I'll suggest you 3rd option, in case if anything goes wrong and you are not satisfied, you can always do a fresh install of latest releast :)

---

### Post by ahso4271 on 2012-04-26
I doubt update will be as clean as a fresh install. I'll download, format and install 12.04 after saving some files from my home especially .thunderbird, .mozilla etc. The hidden files usually are apps configs so 
you won't lose passwords etc.

Some years back the update option was very bad...

---

### Post by jadtech on 2012-04-26
jst do the upgrade  throught the terminal or manager how ever make sure you have a live cd  an know that upgrades can go very wrong at time an require a full install so also back up anything you cant lose ..

---

### Post by c2tarun on 2012-04-26
> **ahso4271 said:**
> after saving some files from my home especially .thunderbird, .mozilla etc.
 
 
To save myself from this situation I keep a separate home partition, doing normal install and then mounting that home partition over /username/home :)
 
This also saves my data on my home partition, as I have pretty big home partition.

---

### Post by jadtech on 2012-04-26
> **ahso4271 said:**
> I doubt update will be as clean as a fresh install. I'll download, format and install 12.04 after saving some files from my home especially .thunderbird, .mozilla etc. The hidden files usually are apps configs so 
you won't lose passwords etc.

Some years back the update option was very bad...

actually an upgrade and install are Identical  the bigest differance is that an upgrade can save any person setup that already done ..

---

### Post by c2tarun on 2012-04-26
> **jadtech said:**
> actually an upgrade and install are Identical the bigest differance is that an upgrade can save any person setup that already done ..
 
 
Saving proper files from home folder/partition also saves most of the configuration related settings, you just have to install your softwares again.
There was something like 
     dpkg --get-settings
or something like that will give you the list of packages installed, you can easily install them :)
 
I also keep backup of /var/apt/archive/*.deb and copy them in new installation, most of the time it simply installes from there without downloading any data or very few data. :)

---

### Post by jadtech on 2012-04-26
yeah that will do it not all have that home partition though

---

