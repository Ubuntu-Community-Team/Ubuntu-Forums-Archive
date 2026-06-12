---
title: "Gusty upgrade"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by abhilash82 on 2007-10-18
How long does it take to upgrade from feisty? Any precautions to be taken?

---

### Post by dimeotane on 2007-10-18
To get this 'gutsy party' started  I just enter in my terminal: 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

and then my system will become gutsy instead of feisty?

---

### Post by frenchcr on 2007-10-18
Depends on your net conection speed..takes about 20 mins with 8mbit (800k transfer)

Get rid of automatix and all automatix related/installed stuff, thats the only precaution i can think of.

---

### Post by frenchcr on 2007-10-18
> **dimeotane said:**
> To get this 'gutsy party' started  I just enter in my terminal: 

```
sudo apt-get update
sudo apt-get dist-upgrade
```

and then my system will become gutsy instead of feisty?


no need....should see it in update manager now!!

---

### Post by ericartman on 2007-10-18
Been running Gutsy for a while now, updated 2 days ago and today  update manager says I'm current. So I 'm happy

Cart

---

### Post by abhilash82 on 2007-10-18
What abt taking backup of the /home partition?

---

### Post by Lord Landis on 2007-10-18
You should maintain regular backups of your /home partition (folder) anyway, but, yes, in this case you definitely want to have a backup on-hand.  Make sure that backup contains all of your hidden folders as well - after all, you don't want to lose your bookmarks or e-mail in the process of using an incomplete backup, do you?

I recommend using an external drive or a network drive (if you have either) and running rsynch to get the job done quickly and efficiently.  I use the following switches:

```
rsync -rptgo /home/$USER $destination/home/$USER
```

In my case, $destination is SDA1 (my external USB hard-drive).  That should just about move everything you'd need to have saved.

---

### Post by DonQuichote on 2007-10-18
Better make a backup of /etc as well. I started the upgrade about 14 hours ago (and it still runs; the "installing the upgrades" progressbar is at 60% now) and it want to unconfigure my settings one in a while. As far as I can see, the most pain is in /etc.

Is there a better way than "upgrade-manager -d" to do the upgrade? If I have to spend 21 hours (NOT counting the afterward work in reconfiguring the system again) for a non-unattended upgrade for my other machines, I'll stick to 7.04

Good luck.

---

### Post by Sef on 2007-10-18
> Is there a better way than "upgrade-manager -d" to do the upgrade?

The only other way is to do a clean install.

---

