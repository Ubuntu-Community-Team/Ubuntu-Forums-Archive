---
title: "Raid Or Mirror"
date: 2007-02-07
forum: Installation &amp; Upgrades
---

### Post by DWCH on 2007-02-07
Hello Everyone

I have a problem that after browsing the posts cant seem to find an answer its as follows-


Poweredge Server
2 SATA 320G drives

One has Ubuntu Server (6.06) installed with VMware installed running my VM's

I would like to mirror this drive to the other one so if it fails then I will be able to move to the mirrored one and carry on without any loss. There is no data or partitions on this second drive at present.

I have installed Webmin and looking at that it looks like I should be able to do it but cant seem to work out the steps involved.

If anyone can point me in the right direction it would be appreceiated


DWCH

---

### Post by RandomJoe on 2007-02-07
There are a couple of options depending on just what you are after.

Most likely, and what I would do (have done), is to use RAID1.  As far as I know, you will have to reinstall everything (or back up to another drive then reload) since you have to change the partition types to RAID (fd), create the RAID volume, and _then_ put data on.  (This is for Linux Software RAID.)  When I installed my desktop system I used the "Alternate Install" CD which lets you set up RAID volumes before starting the installer.

The other option if all you are really after is a sort of disaster-recovery backup is to dd the entire drive to the other one (since they are the same size) in which case if the first dies, you can swap the other in (theoretically - I've never done this by physically swapping drives!) and after reloading GRUB be back in business.  From the point where you made the snapshot.

A different way of making the backups would be rsync, which is what I use.

The advantage of the snapshot method is that you have a backup even if you trash things by deleting/overwriting as well as a hardware failure.  On the other hand, the RAID1 will keep you running uninterrupted (although with degraded performance) in the event of hardware failure.

Granted, if all you are going to do is a snapshot, I would take the second drive out and put it in a USB/Firewire enclosure.

---

