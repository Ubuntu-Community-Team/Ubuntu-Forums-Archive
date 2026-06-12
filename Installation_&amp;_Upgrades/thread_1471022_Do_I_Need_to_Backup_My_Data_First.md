---
title: "Do I Need to Backup My Data First?"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by redwoodguy on 2010-05-03
I have the 10.04 disk and it sun checks - fine. When I went to install, I was faced with a question that threw me: 1) Make a side by side partition with 9.04 and 10.04, OR, "Erase and install 10.04 on one partition" 

Does that mean it will erase my data? If so, that seems absurd, but I didn't want to take a chance. And, I have desire to keep the old os version on another partition. 

I'd like to simply have the new OS replace the old like we would do on a Mac, without removing and then putting back all my data first. 

How does it work?

---

### Post by rg_stephens on 2010-05-03
You should always back up your data, because things can happen. 

You're right, if you choose to use the entire disk, it will wipe out everything, so you have to back up your home folder first. I wish there were an easier way to do things. I tried to "upgrade" from 9.10, and it didn't work. 

You might be able to make a separate partition for your /home folder, or simply share it between 10.4 and 9.4, but I'm not very familiar with how to do this.

---

### Post by redwoodguy on 2010-05-03
Well, if that's true - that I have to remove and reinstall all my data and programs JUST to upgrade the OS, that would make Ubuntu totally useless for me. My enthusiasm for Linux is now zero, if that's how they do upgrades. 

Is there no way to simply over-write the old OS? Seems ridiculous frankly, but oh well.

---

### Post by sunk8 on 2010-05-03
> **redwoodguy said:**
> Well, if that's true - that I have to remove and reinstall all my data and programs JUST to upgrade the OS, that would make Ubuntu totally useless for me. My enthusiasm for Linux is now zero, if that's how they do upgrades. 

Is there no way to simply over-write the old OS? Seems ridiculous frankly, but oh well.

No fear... The Joker is here...

Listen. First log into the 9.04. Go to Synaptic.
File >> Save Markings.
You might also want to backup your home folders, mails, browser bookmarks, etc...

Then boot using the 10.04 Live CD. Open GParted.
Delete the 9.04 partition.
I find ext4 better than ext3, so i won't recommend just installing on it.
Then install 10.04. Let it use that largest free space.

Restore your data.
Install latest Updates... ;-)

---

### Post by TBABill on 2010-05-03
> **redwoodguy said:**
> Well, if that's true - that I have to remove and reinstall all my data and programs JUST to upgrade the OS, that would make Ubuntu totally useless for me. My enthusiasm for Linux is now zero, if that's how they do upgrades. 
 
Is there no way to simply over-write the old OS? Seems ridiculous frankly, but oh well.
 
redwoodguy, since you are on Ubuntu have you tried to upgrade your distro instead of installing the distro again?
 
sudo aptitude update
sudo aptitude dist-upgrade
 
I'm not certain you can dist upgrade from 9.04 directly to 10.04, but do a search of the forums if you have time to be certain. If it will work this will keep your data without formatting (but backup regardless, just in case there are errors in the upgrade process!!)

---

### Post by oldos2er on 2010-05-03
The choices the OP listed, make a side-by-side partition, or erase and install are what you see if you're booted from the LiveCD. 

If you want to upgrade 9.10 to 10.04 from CD, you'll need the alternate CD (but don't boot from it). Or upgrade online from Update Manager. More info here: [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

No matter which method you choose, it's always wise to backup any sensitive data first.

---

### Post by redwoodguy on 2010-05-03
Ann-
I hope I am reading it right, but it sounds like I can update without ERASING my data. I understand backing up for "safety" - I get that. But I don't have any easy wasy to back up 100GB of my data. I also do NOT want to re load 50 applications.

I would like to be clear: Is there an upgrade which doesn't ERASE all the data on purpose?

---

### Post by redwoodguy on 2010-05-03
Ok, I upgraded over the network and it looks like it went ok. I am not sure why I didn't know this path of upgrading existed, but all is well, apparently. Thanks to everyone for their help and suggestions.

---

