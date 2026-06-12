---
title: "out of space upgrade from 11.10 to 12.04??"
date: 2012-11-23
forum: Installation &amp; Upgrades
---

### Post by Bobrm2 on 2012-11-23
I've ran completly out of space, upgrading to 12.04 from 11.10. Box is locked up. Can still get to "files". Most important files on on the "Cloud" (which I dislike). Have not opened GParted, recently moved to this home and seeking the .ISO.
  If: I re-boot the compter, is all lost? Wouldn't be the best case, but>>>>  
  2. I had no intent to remain at 12.04 but continue to the lastest version. If all is lost what's the best way to get to the latest version, i.e. just simply download the ISO and start. Always have fun when trying to upgrade to the "Latest" version. Thanks, Your Advice always appreciated.

Bob

---

### Post by snowpine on 2012-11-23
A good first start is the command:

```
df -h
```

which will show your current disk usage of all mounted partitions/volumes.

You can sometimes free up a few mb's (if the problem is a full / or "root" folder; we won't know that until you run the above command) with these "housekeeping" commands:

```
sudo apt-get clean
sudo apt-get autoremove
```

The foolproof method is to back up all data to an external drive and a fresh reinstall of 12.10. :)

---

### Post by darkod on 2012-11-23
If you reboot, it would be very rare that all data is lost. The data will still be there but you probably won't be able to boot because of the half-way upgrade.
So, if the question was: If I reboot will it boot, probably NOT.

As for moving from 12.04 to 12.10, I wouldn't recommend it unless you have a really good reason for it (something that 12.10 can do for you and 12.04 can't). Moving to new releases, upgrading all the time, just because there is a newer release is asking for trouble.

12.04 is LTS release and will be supported for 5 years. 12.10 is normal release with 18 months of support.

Which means once you have your 12.04 the way you want it, you don't have to upgrade or do a clean install until 2014 (when the new LTS should be out) or even further (it will have support until 2017).

And clean installs are always better than upgrades, but there are few things to consider. We can discuss that once you get there.

About this upgrade problem. Do you know if it actually started the upgrade and stopped, or it didn't even start complaining that there is not enough free space? Usually the upgrade process should know there is not enough free space and shouldn't even start. That would prevent it leaving the computer unusable with a half-way upgrade.
It case it only complained and actually never started upgrading, if you reboot you should get your 11.10 as normal. And you would have to consider deleting/moving some data so that you create more free space. Upgrade or no upgrade, don't let it fall to 0%.

---

### Post by Bobrm2 on 2012-11-23
Size     Used   Avail Mtn
/dev/sda7   7.3g    7.3g   100%  /
udev        874m     12K     874m /dev
tmpfs       364m     1.2m   351m  /run
none        5.0m      0     881m /run/lock
none        881m     120k   390m /run/shm
/dev/sda1   447       33m   390m /boot
/dev/sda5/   20G      14g    5.8g /home

  I've left the percentages out, also ran as SUDO.

Running sudo apt-get clean
sudo apt-get autoremove

Ok, I'll be glad to stay at 12.04, like the idea that I won't have to "upgrade" until 2017.

 Re-reading responses, to see if I've left anything out in this response. Also, believe the partition(s) could be tweaked but that's another issue. 

Bob

---

### Post by Bobrm2 on 2012-11-23
Sudo apt-get autoremove returns:

E: Could not get lock /var/lib/dpkg/lock -open (11: Resources temperarily unavailable)

E: Unable to lock administration directory (var/lib/dpkg). Is another process using it?

  Following programs are open, that I am aware of:
  <Upgrade Notres _ (Foxfire)
  <Dirstribution upgrade
  <System Info
  <df -h (i.e. Terminal)

---

### Post by Bobrm2 on 2012-11-23
upgrade DID start, then complained about insufficent space, (my mistake here). opened System Info, attemmpting to locate space. Interuption and the error made.

---

### Post by snowpine on 2012-11-23
Looks like the incomplete distribution upgrade is locking any other package management from taking place. 

Worst case you can manually delete files, for example cached .debs in /var/archive/apt/archives (that's essentially what apt-get clean does), logs in /var/log you no longer need, etc.

You can also try searching these forums for what other users have done when their drives are full.

To be realistic with only 7.3gb it's going to be a tight squeeze to upgrade-in-place rather than fresh reinstall.

---

### Post by Bobrm2 on 2012-11-23
agreed, I'll download another ISO (12.04), upload all that I think I want to save to the "Cloud" and go for it. Thanks for your advice.

  A little off the subject, but what is your opinion of the partition table??

---

### Post by snowpine on 2012-11-23
With such a tiny hard drive, I personally would put everything in the same partition (the default for the Ubuntu installer) for efficient use of space, but that is just my own preference. (or just replace with a bigger drive as they are super-cheap these days :))

---

### Post by Bobrm2 on 2012-11-23
Thanks, the one I'm on now, is 24G, I built it last year. I bet that's small now. Thanks for the assist, to all.

Bob

---

