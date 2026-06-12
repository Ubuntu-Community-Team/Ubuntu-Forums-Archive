---
title: "Possible to dist-upgrade from a DVD or CD?"
date: 2005-11-04
forum: Installation &amp; Upgrades
---

### Post by aveline on 2005-11-04
Title says it all & I know that may be a dumbass question.  I know one can install linux over top of an old system install preserving your /home ofc.  However I wondered can one also just do dist -upgrade w/out having to have ubu connect to the mirrors & upgrade instead from DVD or CD?

Second question:  I have a spare comp on a workbench which I've tried a zillion times to reinstall xp onto yet after having installed ubuntu it will not boot off an xp cd.  The cd burns are good, I know b/c I tested them on other comps.  I have installed xp on that comp before so it should work.  Even low level formatting the drive did not work.  YET I can install Ubu just fine?  :confused: 

ideas pls

[Edit]  On a hunch the cdrom was faulty I replaced it twice with 2 diff drives from 2 diff manufacturers & the xp cd still will not boot, yet Ultimate Boot cd & most linuces do boot.  
aveline

---

### Post by adwait on 2005-11-04
1)Yup. Put  the Cd in, use 
```
sudo apt-cdrom
```
then
```
sudo apt-get update
sudoapt-get dist-upgrade
```

---

### Post by MakubeX on 2005-11-05
Will that method still require Internet access/connection?

Is that "sudo apt-get dist-upgrade" ?

---

### Post by tseliot on 2005-11-05
[QUOTE=MakubeX]Will that method still require Internet access/connection?

Is that "sudo apt-get dist-upgrade" ?[/QUOTE]
1) No, I guess it doesn't

2) Yes it is "sudo apt-get dist-upgrade"

---

### Post by n00bWillingToLearn on 2006-04-06
[QUOTE=adwait]1)Yup. Put  the Cd in, use 
```
sudo apt-cdrom
```
then
```
sudo apt-get update
sudoapt-get dist-upgrade
```[/QUOTE]

Sorry but I am unclear what you mean by this. I want to upgrade breezy to the newest dapper drake on another persons machine on dial up. I have DSL though and can download and burn a cd from my computer (the other machine cannot read DVD's though I can write them). Would this make me such a CD? what of these commands would I do on my computer I am burning/downloading the updates from and what would I do on the machine I am updating. FYI my machine is running the current dapper.

---

### Post by Irony on 2006-04-06
Look here;

[https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

To upgrade from Hoary to Breezy I downloaded the iso and burnt it to cd then went to synaptic hit reload > mark all upgrades

Note also change hoary to breezy in /etc/apt/sources.list - I expect the entire process is similar with Dapper.

---

### Post by aysiu on 2006-04-06
Pop the CD in.

Go to System > Administration > Synaptic Package Manager

Then go to the second menu option (I forget what it is) and select "Add CD-ROM."

It'll add the CD on to the sources.list.

Then go to Settings > Repositories and uncheck all the other sources.

Click "Reload."

I'm not sure if marking all upgrades will then do a dist-upgrade, so I would do this in terminal just to be safe. ```
sudo apt-get dist-upgrade
```

---

