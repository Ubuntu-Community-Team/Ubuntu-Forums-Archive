---
title: "Upgrade messed up"
date: 2012-12-23
forum: Installation &amp; Upgrades
---

### Post by QuimNuss on 2012-12-23
Hello everyone!

Yesterday finally I upgraded to 12.04 from 10.04.

The system is now pretty messed up. Half of the indicators weren't there, so I had to install them one by one. I believe the whole unity thing requires a lot of stuff that the upgrade did not install.

As usual, it tried installing the fglrx, which does not work on my system and leads to a black screen. I solved that.

However, today it's happening again, after some unity crashes (which unity --replace usually solved). I managed to get some output with nomodeset. The startup got blocked at Timidity, sometimes just blocked, sometimes saying '/etc/timidity is not ours'. (I tried the solution here: [https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/1035592](https://bugs.launchpad.net/ubuntu/+source/timidity/+bug/1035592) it didn't work at first, I'm not sure it's working now).

Now I've managed to get to a graphical session, not sure I can reproduce that... So any quick help would be appreciated, since I'm scared of rebooting, so to speak. 

Also, the update manager told me that only a partial update was possible, it's now updating 977 packages.

I'm a bit lost on this onw since it might be happening that several things are going wrong, aggravated by the fact the graphical card does not handle linux very well.

Let me know what information would be useful...

---

### Post by fantab on 2012-12-23
From 10.04 to 12.04 Ubuntu has undergone major changes. If you had done your research before upgrading it would have been easier for you. Anyways.

I would recommend that you do a "Clean" install of Ubuntu 12.04. It will be far easier and cleaner if you do so and less messier and less time consuming than trying to fix your failed upgrade. Just remember to BACK-UP all your important data first.

Good Luck..

---

### Post by QuimNuss on 2012-12-23
I knew there were major changes and I have my data backed up.

I hoped the upgrade would work, I guess I could surrender like you propose. I'll give another try, recheck that I have all the valuable data and configuration and surrender if it does not work.

---

### Post by fantab on 2012-12-23
> **QuimNuss said:**
> I knew there were major changes and I have my data backed up.

I hoped the upgrade would work, I guess I could surrender like you propose. I'll give another try, recheck that I have all the valuable data and configuration and surrender if it does not work.

I wouldn't call it surrender. Personally I never upgrade, I always do a clean install every time. And to make it easier for me I have a separate ext4 Data Partition, I don't use a separate '/home'. No worries about losing Data or messed up configuration files, I just reformat '/' partiton and install fresh. But I do back up my dot.thunderbird.

Downloading and Installing upgrades actually takes longer than downloading a new .iso and doing a fresh install.

My two cents...

---

### Post by QuimNuss on 2012-12-23
Great, even when starting from a USB to reinstall the whole thing I get the same result. Any hints?

---

### Post by fdrake on 2012-12-23
> **QuimNuss said:**
> Great, even when starting from a USB to reinstall the whole thing I get the same result. Any hints?

maybe your video card does not handle unity very well. if you don't mind using gnome2(which i prefer) instead of 3 follow this how to. At the lgin you have the choise to select which desktop manager to use. Also remember that some program (from 10.04) will not run (correctly) on gnome3, unless there is a specific upgradeot fix for them.

[http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-gnome-desktop](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-gnome-desktop)

---

### Post by QuimNuss on 2012-12-24
I followed your advice and I reinstalled the system when the USB stick granted me to.

Everything seams to be working! Except, maybe, the wireless dropping after a while... anyeay, I'll get this to another thread.

Thanks!
pol

---

