---
title: "Update to 12.04 LTS. Will I lose anything?"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by dreamquartz on 2012-04-27
I would like to update to 12.04 LTS from 11.10.
I have installed all kinds of software and have all kinds of settings.
I would like not to re-install all the extra software or even do have to check or re-do my specific settings.

Does anyone know what will happen with the update?

I could not find a clear answer.

Dream

---

### Post by Irihapeti on 2012-04-27
Probably, the reason you couldn't find a clear answer is because there isn't one. Upgrading can be rather hit and miss. It works well enough for some people, but for others it's a total disaster.

If you want to try, I suggest that you back everything up first. That includes the system. See [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR) for one way of going about this. Then at least if everything falls to pieces, you can put things back the way they were.

Then go ahead and upgrade. You may get lucky and find that it works well.

---

### Post by Senior_Buckethead on 2012-04-27
Yes, upgrading can be a hit and miss affair. It would be prudent to back up the contents of your home directory to another device, like a flash drive. Just in-case something untoward happens. Make sure you back up your mail application, such as Thunderbird or Evolution.
Evolution lets you backup to a .tar.gz archive, that you can easily restore after your upgrade. I haven't investigated it, but I assume that Thunderbird does the same.

Might be an idea to record what applications you have installed, just incase you have to install them again.

Glenn.

---

### Post by kohoutek1 on 2012-04-27
> Probably, the reason you couldn't find a clear answer is because there isn't one. Upgrading can be rather hit and miss.

I think it's a reasonable question. This is a user who maybe hasn't done full upgrades before and may be used to an OS that clearly provides an "Archive and Install" option. 

On Ubuntu, the default is to leave everything intact if a pre-existing installation is found. But before you commit to the upgrade, you are given a list of changes that will be made, including some deprecated/obsolete files that will be removed but not replaced. Configuration files are not "supposed to be" touched. You should look over that list carefully. If there are things you don't want removed, and they aren't going to be replaced with updated versions, you can stop the process and decide later.

As a fallback, there is a way to easily save installed programs in their current state, too, using Synaptic. See this thread:
[http://ubuntuforums.org/showthread.php?t=1966333](http://ubuntuforums.org/showthread.php?t=1966333)

---

### Post by kohoutek1 on 2012-04-27
Another thing you'll see happening if you go on with the upgrade: A dialog will pop up for any config files that have been customized. You can choose "Keep" or "Replace." The installation stops until you choose.

---

### Post by dreamquartz on 2012-04-27
](*,)Am I missing something?
Nautilus is Preparing to Copy and it is determining that Home is WAY bigger than it actually can be.
At this point Nautilus states that Home is more than 387.3 GB, while GParted tells me that sda1 (Home is on there) has a size of 134.24 GB of which 55.04 GB has been used.
Even my laptop has a physical drive of 250 GB (stated by the manufacturer).

I initially thought I made a mistake, so I restarted to copy Home again.
But now it looks like there is something serious wrong.

Dream

---

### Post by fantab on 2012-04-28
UPGRADES are more often than not are messy. I always do a clean install and I recommend the same. I understand that backing up all that data from /home can be PITA. What I have done is create a plain Linux Partition ext4 and save all my Data on to it. I have to mount it everytime I login to Ubuntu... and I don't mind it. It can also be configured to be automounted. 

This way I don't have to worry about losing my DATA and instead of upgrading I do a clean install by formatting / partiton.  I only use / mountpoint partiton to install Ubuntu about 20GB.

Think about it.

---

### Post by dreamquartz on 2012-05-02
> **fantab said:**
> UPGRADES are more often than not are messy. I always do a clean install and I recommend the same. I understand that backing up all that data from /home can be PITA. What I have done is create a plain Linux Partition ext4 and save all my Data on to it. I have to mount it everytime I login to Ubuntu... and I don't mind it. It can also be configured to be automounted. 

This way I don't have to worry about losing my DATA and instead of upgrading I do a clean install by formatting / partiton.  I only use / mountpoint partiton to install Ubuntu about 20GB.

Think about it.
Great idea.
Will try it.

---

### Post by dreamquartz on 2012-05-02
Was able to update. Worked well.
Was not able to figure out why the backup did not work, so I went for it.
No problems so far.

---

### Post by dreamquartz on 2012-06-09
I have to change it back to NOT SOLVED!!!!!!!!!!!
I lost my BT DUN Teather to my BB 9800.

Can not get it back

---

