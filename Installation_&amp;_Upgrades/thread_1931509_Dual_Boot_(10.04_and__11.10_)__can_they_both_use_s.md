---
title: "Dual Boot (10.04 and  11.10 )  can they both use same /Home partition ?"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by BikeRich on 2012-02-25
Right now I have only lucid on my netbook- no other OS.  Would like to dual boot

with 11.10 ; my question is , can both OS's use the same /Home partition, or will 

there be problems, such as UUID  issues ?  Thanks for any help.

---

### Post by coldraven on 2012-02-25
I don't know about UUID but in your home folder are all the config files for your applications. All these directories are hidden files They all have a period as the first character in their name. You can see them in Nautilus by pressing CTRL+H.
So for example the .mozilla folder will save your settings and passwords for Firefox.
Having two different versions of Firefox trying to use the same settings may cause a problem. I'm sure that someone else will have more knowledge than me so wait a while before deciding.

---

### Post by BikeRich on 2012-02-25
ColdRaven

     Thanks for that info!  Sounds like 2 separate  /Home partitions might be the way

to go, but as you suggest , I'll wait awhile .  :D

---

### Post by oldfred on 2012-02-25
Actually Firefox & Thunderbird seem to work across versions pretty well. I have both profiles in a shared NTFS partition from when I used XP a lot and still use the same profiles for several versions of Ubuntu.

But I do not recommend sharing /home. Programs are designed to upgrade settings from an old to a new version but a old version program may not like settings from a new version.

All the hidden settings in /home are small. My /home is about 1GB and 3/4s of that is my .wine. I have moved everything else all standard data folders like Music, Documents, etc and some hidden folders like Firefox & Thunderbird profiles, kmymoney, and others that have data to other partitions. Then since /home is small you can just copy it to your new install. Then if you want you can easily back up /home and copy settings back and forth but beware they may not all work.

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by BikeRich on 2012-02-25
OldFred

     I prefer to have a /Home of about 50GB , so that when its time to do a fresh 

install, that partition simply stays put , with all my stuff on it.  No doubt you are

familiar with that strategy, yet you do not use it.  Seeing that you have so much

experience makes me hope that you will tell me why.

     Those links look interesting, I'll click on each one. Thanks for your comments .

                                                                 :D

---

### Post by oldfred on 2012-02-25
I am not sure there is a lot of difference. I often suggest a separate /home to new users. But do not suggest sharing any system partition including /home at the same time.

But I want to run several versions of Ubuntu and easily have all my same data in each. Data does not depend on any system or settings so it is easily shared with some caveats on UIDs & GIDs. I started with a simple shared NTFS and just expanded into also sharing an ext3 partition when I mostly stopped using XP.

I started using links to mount folders and to make system look like a standard install. Most others now suggest bind (bindfs seems to not work now).

Another way to share:
Morbius1 uses bind, now:
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)
kansasnoob's sharing and Morbius1 use of bindfs older
[http://ubuntuforums.org/showthread.php?t=1495798](http://ubuntuforums.org/showthread.php?t=1495798)

---

### Post by BikeRich on 2012-02-25
OldFred  

     Your most recent reply is well beyond my level of understanding, but if I do some

digging and studying, then I'll learn some useful things. I am truly grateful.

---

