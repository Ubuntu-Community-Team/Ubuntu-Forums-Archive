---
title: "Reinstalling (while keeping the home folder)"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by Granknight on 2010-05-11
Hello, i have several problems with ubuntu as i upgraded (via update manager) to lucid.
Those problems include java apps not working, compiz crashing gnome, sound applet disappearing, and many other problems.
Since i can't backup my data (don't have (by far) enough space to store it) i searched for a way to reinstall ubuntu witout losing what i got in my home folder
by googling i found out about the command
```
dpkg-reconfigure -phigh -a
```i ended gnome, went to a terminal and did the command, but when it ended reconfiguring nothing was changed.
Any clues about what I can do? i don't mind reinstalling all the apps with synaptic, what i want to keep is only what i got in my home folder (not the config files in the hidden folders in it).
My hardware is: core2duo 1,6ghz; 2gb ram; 500gb hard disk; ati radeon x1300.
I have 2 partitions, one in ext4 on / with all but 2gb, and 2gb of swap.

---

### Post by Jay Car on 2010-05-11
> **Granknight said:**
> Hello, i have several problems with ubuntu as i upgraded (via update manager) to lucid.
Those problems include java apps not working, compiz crashing gnome, sound applet disappearing, and many other problems.
Since i can't backup my data (don't have (by far) enough space to store it) i searched for a way to reinstall ubuntu witout losing what i got in my home folder
by googling i found out about the command
```
dpkg-reconfigure -phigh -a
```i ended gnome, went to a terminal and did the command, but when it ended reconfiguring nothing was changed.
Any clues about what I can do? i don't mind reinstalling all the apps with synaptic, what i want to keep is only what i got in my home folder (not the config files in the hidden folders in it).
My hardware is: core2duo 1,6ghz; 2gb ram; 500gb hard disk; ati radeon x1300.
I have 2 partitions, one in ext4 on / with all but 2gb, and 2gb of swap.

I think you can do it if your home folder was originally set up on its own partition. But, to me, the most urgent problem you have is getting your personal files backed up. 

Maybe go through those files and prioritize by importance, then start burning the most important ones onto CDs or DVDs. I know it's tedious and time consuming, but not as painful as the risk of losing all of your data. 

I'm sure others can better help you with your reinstalling problem, but I truly hope you'll take the time to save your files first.

---

### Post by dino99 on 2010-05-11
look at this mini howto:
[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by Granknight on 2010-05-11
> **Jay Car said:**
> I think you can do it if your home folder was originally set up on its own partition. But, to me, the most urgent problem you have is getting your personal files backed up. 

Maybe go through those files and prioritize by importance, then start burning the most important ones onto CDs or DVDs. I know it's tedious and time consuming, but not as painful as the risk of losing all of your data. 

I'm sure others can better help you with your reinstalling problem, but I truly hope you'll take the time to save your files first.
i would need dozens of DVDs, and still would need to move them first to another computer to burn them :-/

---

### Post by Granknight on 2010-05-11
> **dino99 said:**
> look at this mini howto:
[http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)
this doesn't help me at all... i don't want to repartition, i need to reinstall the OS leaving intact the home folder.

---

### Post by dino99 on 2010-05-11
> **Granknight said:**
> this doesn't help me at all... i don't want to repartition, i need to reinstall the OS leaving intact the home folder.

thats all about :P

---

### Post by Granknight on 2010-05-11
> **dino99 said:**
> thats all about :P
but i *can't* partition like that, because i've already got a / partition with everything on it, and i don't want to remove it, but only to reinstall ubuntu without touching /home (which already exists, and is with everything else in the / partition)

---

### Post by johndharvey on 2010-05-11
I *think* you should be able to copy your home folder to some external medium (like an external HDD or uploading it to Mediafire), and then when you reinstall Ubuntu, just overwrite your new home folder with your old one, and you should be good to go.

Somebody please correct me if I'm wrong. ;)

---

### Post by oldfred on 2010-05-11
How much space do you have:

```
 df -Th | sort
```

Should get something like this:
/dev/sda2  fuseblk     30G   20G   11G  66% /home/fred/shared
/dev/sda5     ext4     15G  6.2G  7.5G  46% /
/dev/sda7     ext3     48G   14G   31G  32% /usr/local/fred/data

---

### Post by Granknight on 2010-05-11
I get only this
/dev/sda2     ext4    458G  242G  193G  56% /

---

### Post by oldfred on 2010-05-11
Well, you do have 193GB free so you do have some room to work. Moving partitions once they have data will be very slow and not without any risk. You still still should have backups.

I would just create a new 20GB / (root) partition, create a new /home of 150GB and install (move /home hidden files if you want). Then you can move 120GB of data to /home and delete 120GB out of your current. You then can shrink your current install and create a new /data partition 120GB and move the most of the rest into that. 
I would add the data partition for some of the data and keep that in a separate partition, so you do not have everything in once place. Easier to backup or copy if need be for a little more work in creating links to mount into /home.

---

