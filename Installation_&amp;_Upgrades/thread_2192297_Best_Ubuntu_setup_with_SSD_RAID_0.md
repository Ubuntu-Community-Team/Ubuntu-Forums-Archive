---
title: "Best Ubuntu setup with SSD RAID 0"
date: 2013-12-07
forum: Installation &amp; Upgrades
---

### Post by tehvulpes on 2013-12-07
Hey all

In a few days I will be getting a 240 GB RAID 0 SSD setup for my computer, and I would like to use that to speed up Ubuntu. Because a majority of the SSD space will go to windows (gaming), I'd like to give as little space as possible to Ubuntu for it to use, and keep as much as possible on a 1TB HDD while still avoiding the most noticeable performance bottlenecks. If I were to reinstall Ubuntu, what should I put on the SSD, and how much space should it have? Are there any ways for me to move parts of my current setup to the SSDs while avoiding having to reinstall? Currently all of Ubuntu is on a 100 GB partition on a 1 TB HDD.

---

### Post by oldfred on 2013-12-07
I generally do not recommend RAID 0. As if either drive fails or is corrupted then all data from both drives is gone. You need really good backup procedures.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

I have a 64GB SSD and have two complete / (root) partitions including /home. Each / is about 28GB and my working install uses about 10GB. My /home is 2GB of the 10GB and most of that is wubi for Windows Picasa.
But I link all data folders like Documents, Video etc to a data partition which has the actual folders.

Since /home is most of your configuration, I would just suggest moving /home to a new partition on your 1TB drive, and do a new install to a 20GB / partition on your SSD.
      
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

You have to do manual install and mount /home as part of install. The standard desktop does not include RAID drivers. The alternative installer has RAID but last version was 12.04. You can also use server install and then just choose desktop environment you want.
See notes on RAID.
[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)

---

