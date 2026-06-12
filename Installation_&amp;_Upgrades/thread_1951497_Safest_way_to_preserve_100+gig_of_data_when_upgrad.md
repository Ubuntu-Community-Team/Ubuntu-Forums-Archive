---
title: "Safest way to preserve 100+gig of data when upgrading"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by Razmear on 2012-04-02
Here's the deal. 
I started out with Ubuntu, then swiched to Kubuntu (installed on top of Ubuntu) a few versions back. 
For Kubuntu 12.4 I'd like to do a clean install to get rid of all those old and unneeded Ubuntu files still lurking about. 
My system only has a root partition and a swap partition. On root I have a /Vault folder with about 100gig of photos, avi's and other stuff from PCs past that I do not want to risk loosing. 
There is currently about 120gig of free disk space on the system.

So the question is, what is the safest way to preserve the /Vault folder while doing a fresh install? (preferably without the use of a bunch of DVD-Roms for backing everything up.)

Thanks,
eb
Kubuntu 11.10, 500gig drive, 2 gig ram

EDIT: Correction, there is 305gig in the Vault folder, I really should delete those old Tom Baker Doctor Who episodes tho.

---

### Post by Mark Phelps on 2012-04-03
The "safest" way -- is to NOT have those files on the drive when you do the reinstall.  Since you're not up to inserting 100 or so DVDs, the way to do this is to migrate all those files to an external drive.

A second way (not so safe, more work, but cheaper -- if you don't have an external drive) involves the following:
1) Boot into Ubuntu desktop CD and use GParted to (1) shrink the Ubuntu partition, and (2) create a new partition on the drive.
2) Migrate some of those files to the new partition.

... continue to shrink the OS partition, expand the data partition, until you have all the files migrated to the new partition. NOTE: That with 300GB of files to migrate, this is going to take a LONG time -- hours if not days.

Then, when you reinstall, use the "something else" option to reuse the existing Ubuntu OS partition.  Be VERY CAREFUL to not format or overwrite the other (data) partition.

---

### Post by robin22 on 2012-04-03
This is surely a very common problem and one I have struggled with - though not with so much data. I personally believe that large quantities of data should be on a separate disk as a matter of course.

I have nothing to add to the advice already given - it is essentially what I did.

Incidentally I was pleasantly surprised that when I moved Ubuntu into unused space (which I had freed up be downsizing an adjacent partition) Grub continued to boot properly.

I am writing this in the hope that somebody responsible for the development of the Ubuntu install process will read it. Let me know if I should be making this recommendation somewhere else.

In theory the problem of preserving data can be provided for if Ubuntu is installed with customized partition settings. However I don't have enough confidence in my understanding of what the install process will do to manually choose partitions when I install Ubuntu - and newcomers will certainly not know ho do do it.

It seems to me it would be very simple for the standard Ubuntu install process to create separate root and home partitions and, at a later stage if the user decided to re-install Ubuntu (perhaps a newer version) it would recognize the existence of the home partition and link to it.

On my netbook (in addition to Windows 7 which I rarely use) I have two partitions with Ubuntu 10.10 and Xubuntu 12.04 and a third home partition. This way, if I want to upgrade at some time in the future I can wipe the 10.10 partition and install a new Ubuntu there while still having version 12.04 working and all the data in my home partition untouched.

Of course it is essential to backup data in case of a catastrophe.

---

### Post by mastablasta on 2012-04-03
> **robin22 said:**
> 
I am writing this in the hope that somebody responsible for the development of the Ubuntu install process will read it. Let me know if I should be making this recommendation somewhere else.
Then you are writing in the wrong place. try launchpad instead.

> 
It seems to me it would be very simple for the standard Ubuntu install process to create separate root and home partitions and, at a later stage if the user decided to re-install Ubuntu (perhaps a newer version) it would recognize the existence of the home partition and link to it.


i agree. an option for separate home should be made in installer and it should be very simple. again a launchpad feature request is needed to get this roling. forums are only for help by the users community. developers are very rarely visiting them.

---

### Post by sudodus on 2012-04-03
> **Mark Phelps said:**
> The "safest" way -- is to NOT have those files on the drive when you do the reinstall.  Since you're not up to inserting 100 or so DVDs, the way to do this is to migrate all those files to an external drive.
... 
+1
I strongly recommend that you buy at least one big external drive.

If you intend to use only linux, I recommend that you re-format it to ext3 (it is probably formatted as FAT32 or exFAT). The standard is USB 2.0 connection, but you should also consider eSATA and USB 3.0 if you want faster data transfer.

1. Copy your private files to the external drive before doing a fresh install! Let this be your (first?) backup

2. If you buy two external drives one can be connected 'all the time' as a ***data partition***, and the other one can contain ***backup*** data from the system as well as from the data partition. The backup drive need not / should not be connected 'all the time'. You might even keep it in another house to reduce the risk of losing your pictures, videos etc.

---

### Post by Razmear on 2012-04-03
Thanks for the replies. 
After realizing just how big my /Vault directory is I've decided the best method would be to buy a new internal drive, remove the current drive, intstall Kubuntu 12.04 on the new drive, then reconnect the old drive and manually remove all but the /Vault folder (and possibly some config files in /home. 
I will definately be setting up a seperate /home partition this time, and agree that it should be presented as an recomended option on install as it saves a lot of grief down the road. 

Thanks again,
eb

---

### Post by robin22 on 2012-04-04
> **mastablasta said:**
> Then you are writing in the wrong place. try launchpad instead.



i agree. an option for separate home should be made in installer and it should be very simple. again a launchpad feature request is needed to get this roling. forums are only for help by the users community. developers are very rarely visiting them.

Thanks for this.

I did a little more browsing and discovered Ubuntu Brainstorm ...

Then what is REALLY FRUSTRATING I discovered that the ordinary install of Ubuntu since 8.04 [(see here)]("http://brainstorm.ubuntu.com/idea/5390/") saves the contents of /home but I have never noticed any reference to that when I was about to install Ubuntu.

---

### Post by EdwardR on 2012-04-04
Razmear, consider making a separate data partition (separate from home) in which to keep all your pics, vids, documents etc.  You can share the data partition with different operating systems on a multi-boot machine (even with Windows if the data partition is formatted ntfs), but give each OS its own home folder so there are no conflicts with configuration files.

---

