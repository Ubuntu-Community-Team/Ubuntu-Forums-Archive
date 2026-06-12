---
title: "Installer / Partioining Bug ??"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by Sq322 on 2006-05-31
Ok i am midway thru install and partitioning and this is what i get.
I set my partitions as follows.
hda4 is an extended partition
i created 3 subs under it.
768mb as swap
5 gb as ext3 for /
6 gb as ext3 for /home

when i pass thru the installer and it asks to confirm it is showing TWO swap and one ext3 ?? ( the second swap is the one i set to be /home )
What Gives ?? !

---

### Post by jon_z on 2006-05-31
Are you using a live cd?

---

### Post by Sq322 on 2006-05-31
[QUOTE=jon_z]Are you using a live cd?[/QUOTE]
Yes sir

---

### Post by jon_z on 2006-05-31
I have had many problems partitioning with the live cd, I have YET to install linux on a machine with the live cd manually editing the partition tables... I suggest re-burning the cd at a slower speed, if burning fast may have damaged it, try burning at 8x or something..  I gave up on the live cd and use the regular cd.. manually partitioning from there works fine..

---

### Post by Sq322 on 2006-05-31
[QUOTE=jon_z]I have had many problems partitioning with the live cd, I have YET to install linux on a machine with the live cd manually editing the partition tables... I suggest re-burning the cd at a slower speed, if burning fast may have damaged it, try burning at 8x or something..  I gave up on the live cd and use the regular cd.. manually partitioning from there works fine..[/QUOTE]
At this point does it pay to wait until the release tomorrow and just download,burn and install from there ?

---

### Post by jon_z on 2006-05-31
haha oh crap, im sorry totally forgot the release is tomorrow.... or tonight at midnight whatever it may be...  Yeah, just wait the extra day.. They may have fixed that problem with manually editing the partition tables because i know it was a bug on on bugzilla before...  A lesson I learned is to make sure that you burn OS cd's slow.   They dont like being burn't at full speed..  The extra 10 minutes is worth sanity, I've been there its frustrating...

---

### Post by ssam on 2006-05-31
if this is in the daily cd [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) then you should file a bug, and maybe mention it in #ubuntu-devel on freenode.

if its in the RC or Beta cd, then it has probably been fixed already

---

### Post by Sq322 on 2006-05-31
[QUOTE=ssam]if this is in the daily cd [http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) then you should file a bug, and maybe mention it in #ubuntu-devel on freenode.

if its in the RC or Beta cd, then it has probably been fixed already[/QUOTE]

thx for the help fellas.
It was on the RC Live CD
I will wait the day to get the final release

---

### Post by jon_z on 2006-05-31
I'm still using flight 4 cd's :-O

---

### Post by denjin on 2006-05-31
I hope they fix the live CD.  None of the versions of it have ever worked properly for partitioning for me.  Even past the Beta release.

---

### Post by Sq322 on 2006-05-31
If i cant manually partition, i cannot install !

---

### Post by dglock on 2006-05-31
[QUOTE=Sq322]If i cant manually partition, i cannot install ![/QUOTE]

  Use the mepis live cd to partition and then go back to the ubuntu cd to install.

  The mepis live cd partitioning works great!

 don

---

### Post by Sq322 on 2006-06-05
thx for the tip dglock

---

