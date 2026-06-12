---
title: "How do I move Boot to a New mSATA Drive?"
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by kschiff on 2014-03-16
I purchased an mSATA drive that I'm going to install into my Thinkpad X230. In my current setup, I have two partitions: a boot+OS partition sda1 and /home (sda2). I ant to move everything from sda1 to the mSATA drive and be able to boot from it. When that' done, I want to expand sda2 to take over the free disk space on the drive.


What's the best way to do this? Here's is my existing setup without the mSATA drive.

[IMG]http://i.stack.imgur.com/79xgs.png[/IMG]

---

### Post by oldfred on 2014-03-17
I would just do a new install to the new drive. If you mount current /home as part of install you will have all your settings. You should export list of installed apps, to make it easy to reinstall them. You then can still boot into old install if need be to find something that was missing.

If you try to clone sda1, you have to manually change UUIDs as you cannot have duplicates, reinstall grub so it sees new UUIDs and edit fstab for new UUIDS. If you do not change UUIDs, you have to delete old install before you can confirm new cloned install is working as the duplicate UUIDS will create all sorts of issues.

Once you get new install working,  then you can delete old install and move partition left. I generally do not like moving partitions left as it has to copy lots of data, so it will take a while. Any issue, power failure or other interruption will corrupt system so good backups are vital. 

I actually prefer to have an install on every drive.
       Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

---

