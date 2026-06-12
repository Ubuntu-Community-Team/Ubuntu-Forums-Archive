---
title: "Accidentally Erased Partition Containing Ubuntu 14.04.5 LTS"
date: 2019-06-17
forum: Installation &amp; Upgrades
---

### Post by Pinkie_B on 2019-06-17
Hi All,

I had a Dell desktop dual booted with Windows and Ubuntu 14.04.5 LTS. I was told with extremely short notice that I would have to relinquish the machine to my university and in a desperate effort to wipe my data from the hard drive I deleted the partitions from with Ubuntu. I restarted the machine and boom, blank screen of only someone with skills could find my "erased" files (which is better than the blue screen of death, by far).

Now they have returned the machine to me in the state I relinquished it in and I'd like to restore its partitions and my files and settings, if possible. I've downloaded 18.04.2 LTS and I have booted the machine from the USB drive. It recognizes the previous installation and is offering me the option to "Install Ubuntu 18.04.2 LTS alongside Ubuntu 14.04.5 LTS."

I'm tempted to just go for it, but what will happened to the data in the partitions that I deleted? I imagine there must be a way to restore the partitions without wiping all the data since I deleted them simply enough (and the system didn't get weird until I restarted it), but I'm not sure how to proceed or how to go about retracing my steps.

---

### Post by tea for one on 2019-06-17
> **Pinkie_B said:**
> Hi All,

I deleted the partitions from with Ubuntu................................ since I deleted them simply enough 

How many partitions did you delete?

How did you delete them - within a live session or from Windows or something else?

Do you have a back up of your personal data originally contained in the deleted partition(s)?

---

### Post by yancek on 2019-06-17
You indicate that the machine had some unknown version of windows on it.  Are you able to boot that?  What partitions do you have now?  Can you boot the Ubuntu usb and from a terminal run this command and post the output as it will list this info:

```
sudo fdisk -l
``` 

If you want to 'restore' something, you need something to restore which would be the backups mentioned above.

---

### Post by CatKiller on 2019-06-17
If you just deleted the partition table, then the data is still on the disc until something overwrites it. There is software that will examine the layout of the data on the disc, and use that to estimate where the partition boundaries were, and so recreate the partition table.

So it is, in principle, possible to do what you want, as long as nothing has happened to the data in the meantime. I've never tried anything like that, but I understand that testdisk is a tool that people use for it. I have no idea if the tools that are included on the install image can do it, or if you'd need to use a more specialised live image.

The UUIDs of the new partition table will likely be different to the old ones, so you'll probably still need to fiddle with Grub and fstab to get it setup to work as it did.

---

### Post by oldfred on 2019-06-17
Testdisk Instructions, new versions use sectors, old ones were CHS
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

But if you or the University wrote any data to system, it would have used the unallocated space your partition(s) were in and then they may not be recoverable or fully usable.
If you do not have good backups (which you always must have) you may be able to use photorec which is part of testdisk. I have used photorec. It took overnight to run and copy data to another drive. Then I had an old backup, but it recovered every deleted copy of the files. And I had multiple copies of the files I wanted, so lots of file compares. It also only recovers by extension, not full filename. Took weeks to get most of my data, and I learned regular backups save lots of time.


 [http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

