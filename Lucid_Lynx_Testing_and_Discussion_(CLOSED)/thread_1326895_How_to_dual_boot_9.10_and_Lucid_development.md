---
title: "How to dual boot 9.10 and Lucid development"
date: 2009-11-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by williejones on 2009-11-14
Do I need to wait for a CD to download?  Can I start the upgrade form 9.10 and load 9.10 to dual boot?  Confused , but not unwilling to experiment.

---

### Post by ranch hand on 2009-11-14
You can upgrade 9.10 by changing the /etc/apt/sources.list so that all instances of "karmic" are replaced by "lucid".

You should be sure that your 9.10 is up to date and stable.

Edit the sources.list.

Run
```

sudo apt-get update

```
and
```

sudo apt-get dist-upgrade

```
You could wait until the daily builds start (?) or Alpha1 on 12-10.

We are on kernel 2.6.32-4 so it really is different from 9.10 even if it doesn't really look or feel much different.

Of coarse the sound has broken for some folks already.

---

### Post by williejones on 2009-11-14
I already did that a couple of week or so ago. **"I can't wait"**  That only led to Lucid development.  I reloaded 9.10, when it saw my file system, it saw 98% 9.10 and 2% Lucid development as one installation.  I want both.

---

### Post by williejones on 2009-11-14
Just to let you know I can reformat and reload with no problems as I have done it enough in the last 3 months to have it down to a science.

---

### Post by ranch hand on 2009-11-14
Well this is "Lucid Development".

If you want to have both 9.10 and 10.04 on the same drive you will have to install 9.10 twice.

You could do this in a couple of ways but I like 2 partitions apiece (/ and /home).  Another way is a total of 3 partitions where you have a / for each OS and a common /home.

If you go with the common /home make sure you use different user names for each so that the config files do not get tangled.

Then just pick one and do the upgrade.

At this point, do not expect to much difference in the two.  The developers conference is next week.  This is where they will nail down what they want the finished product to be.  Then we can expect things to pick up in pace a bit.

This gives us some time to set up our drives the way we want them.  I have 8.04, two 10.04s, Mandriva2009-1, Zenix9.10, and Masonux9.10.  I probably will stick a 9.04 on there so that I have a grub-legacy using ext4 compatible OS.

I am running Stoned Lizard as my daytime OS (upgraded Stoner Edition1.0 9.04>9.10>10.04) and I run all updates on Lounge Lizard (9.10>10.04) first to see if things break.

---

### Post by VMC on 2009-11-14
> **williejones said:**
> I already did that a couple of week or so ago. **"I can't wait"**  That only led to Lucid development.  I reloaded 9.10, when it saw my file system, it saw 98% 9.10 and 2% Lucid development as one installation.  I want both.

You want both karmic and lucid? If so, then you need to create a second partition for the other. Install karmic on one partition and then karmic on the other and do what ranch hand detailed to make that karmic dance to the tune of lucid. :)

---

### Post by williejones on 2009-11-14
Thanks for the solution.  How do you mark this as solved? Never mind, figured it out.

---

### Post by williejones on 2009-11-14
> I am running Stoned Lizard as my daytime OS (upgraded Stoner Edition1.0 9.04>9.10>10.04) and I run all updates on Lounge Lizard (9.10>10.04) first to see if things break.


Is it not better to load a new version than to upgrage?

---

### Post by williejones on 2009-11-14
The reason I made my last post is that I have always thought upgrades left things thas a complete install would not.  Maybe I am wrong with Ubuntu?

Later

---

### Post by ranch hand on 2009-11-15
There are differing opinions on this but we are not talking about upgrading to a finished product here.  We are following the same path that the devs are in building the new LTS.

The very base of that will be, now, 9.10.  That is why we change the repos and as time goes on the likeness between the two will become greater.

There is a LOT  of difference between 9.04 and 9.10.  There will not be that great a difference this time.

---

### Post by stevetxt on 2009-11-15
What does it mean to have a common /home but give it different names?  I often use a common /home with different releases, and it would be nice to keep the configuration files separate.  I also wonder, is there a way to delete all the hidden files and not the other files, in order to start over on configurations?

---

### Post by ranch hand on 2009-11-15
I don't like the sound of deleting config files.

When you set up one /home partition all kinds of little config files are created in that /home.  If each OS, with its own / has a different user name, then there will be an account, for each name, in the common /home partition.  This will keep the config flles separate, one OS from the others.

---

### Post by jppr on 2009-11-15
> **williejones said:**
> Is it not better to load a new version than to upgrage?

You have only one way use lucid, you must change sources.list karmic -> lucid, you can do it this way 
sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list
sudo aptitude update
sudo aptitude dist-upgrade

[https://wiki.ubuntu.com/LucidReleaseSchedule](https://wiki.ubuntu.com/LucidReleaseSchedule)  You can load alpha 1 2009-12-10

---

