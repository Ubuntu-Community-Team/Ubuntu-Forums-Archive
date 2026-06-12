---
title: "Questions about RAID0, SSD and Ubuntu"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by darkod on 2009-12-11
I am dual booting Karmic with Win7 on single hdd. It's working fine (knock on wood :) ).
I started to look into ways to speed things up, SSD, raid0, etc. I'm running an ordinary home desktop so this is more from enthusiast point of view, I don't really need it.
Because of that fact, splashing loads of money for SSD seems unjustified. The best offer I could find is still 100GBP for 64GB Kingston V-series. Plus there are some articles that the cheapest SSDs are not really that great in performance.
Next step would be onboard raid0. While not a replacement for SSD, it should offer better transfer rate. My current hdd is Seagate 250GB, 7200rpm, 16MB cache. If I was to buy 320GB or even 500GB (the price difference is small), could I use the rest of the drive outside the raid0? This is the main question. Especially if I purchase a 500GB drive I don't want the second half to be unusable.
If that can't work, I guess software raid0 comes under consideration. If I understood right, you create partitions on the drives and then a software raid out of those partitions, so I could use the rest of the disk too. Any performance degradation compared with onboard raid0? What are the pro/cons?

Sorry for the long post. I would appreciate any opinions, suggestions, etc. Thanks.

---

### Post by Ginsu543 on 2009-12-11
In a word, no. In order to set up RAID, you need two identical drives. You can't get a larger hard drive, set the amount equal to the other drive as RAID, and then use the rest as a separate drive.

IMHO, the cheapest way to get better hard drive performance is to spend ~$100 (sorry, don't know the price in Euros or GBP) and get a 1 TB drive (or larger if you can afford it). If you install the OS on the outer part of the platters (i.e., in the "front" of the drive), you'll see improved performance because larger drives are designed to have faster access speeds (they have to in order to read/write that much data) and the outer part of the platters spin faster than the inner part.

For example, on one of my 1 TB drives, I have Jaunty installed on the first 100 GB and I use the remaining 900 GB as a data drive in NTFS so that it can be accessed by both Ubuntu and Windows. Granted, it is not quite as fast as my 2 x 74 GB WD Raptor 10K rpm RAID0 array, but it is still noticeably faster than if I were to run the Raptors as independent drives. So a modern 1 TB 7200 rpm drive trumps a previous generation 10K rpm Raptor.

---

### Post by darkod on 2009-12-11
Thanks.
Actually if I go as high as 1TB the price for the drive is coming close to the SSD. Of course, 1TB has way more storage than the SSD, but I would never use that storage anyway. I would never fill up 1TB.
And I'm not doubting the statement about the speed in the outer sectors but it just made me wonder. If the drive is also 7200rpm where would the speed increase come from? The 32MB cache will play a role, but otherwise I can't see it. It still spins with 7200rpm.

---

### Post by Ginsu543 on 2009-12-12
It's simply a matter of geometry: the outer part of a circular platter moves a longer distance for the same degree of rotation than does the inner part. The entire platter spins at 7200 rpm, but the outer portion covers more distance (larger circumference) than the inner portion. Since read/write speed is dependent upon how fast the read/write heads fly over the platters, more data can be read/written when the heads are over the outer portion than the inner. Another factor is that a larger capacity drive has more platters and each platter is denser, i.e., data is packed closer together. This means that the heads don't have to travel as long a distance on the platters to read the same amount of data. And, as you mentioned, the 32 MB buffer helps speed things up.

I did not know a TB drive was as expensive as an SSD where you are. Here in the United States, a TB drive costs ~$100. SSD drives cost 2 to 5 times that amount. If price is an issue, I agree that your best bet seems to be software RAID. You can create two partitions of the same size on your hard drive and use LVM or mdadm to set up the array.

---

### Post by darkod on 2009-12-12
> **Ginsu543 said:**
> It's simply a matter of geometry: the outer part of a circular platter moves a longer distance for the same degree of rotation than does the inner part. The entire platter spins at 7200 rpm, but the outer portion covers more distance (larger circumference) than the inner portion. Since read/write speed is dependent upon how fast the read/write heads fly over the platters, more data can be read/written when the heads are over the outer portion than the inner. Another factor is that a larger capacity drive has more platters and each platter is denser, i.e., data is packed closer together. This means that the heads don't have to travel as long a distance on the platters to read the same amount of data. And, as you mentioned, the 32 MB buffer helps speed things up.

I did not know a TB drive was as expensive as an SSD where you are. Here in the United States, a TB drive costs ~$100. SSD drives cost 2 to 5 times that amount. If price is an issue, I agree that your best bet seems to be software RAID. You can create two partitions of the same size on your hard drive and use LVM or mdadm to set up the array.

Thanks again. I figured the geometry after posting. :) Too tired to think straight.
Well the price isn't the same but it comes close enough to tempt me going for an SSD. With 500GB it's a different story because that's less than 50% of the SSD.

With software raid0, am I seeing some performance degradation compared to onboard raid0? Is it recommended to use software raid0 like that anyway? I guess that's the only option if I don't want to lose the rest of disk2 by using onboard raid0.

And in that case, what would be the procedure:
On disk1, 250GB, I create with Gparted partition size X for win, size Y for ubuntu
On disk2, 500GB, in the first half I also create size X for win, size Y for ubuntu, the rest of the disk is available as none raid disk.
During install of the OS I set up software raid? I read somewhere that for win software raid you need the disks to be dynamic, not basic. If that's true can ubuntu work like that too? And for ubuntu I would need the alternate cd right, not desktop?

---

### Post by Ginsu543 on 2009-12-12
Yes, I believe you are right that you need to use the alternate CD to install software RAID. Again, I have no experience with software RAID since I've always used onboard fakeraid. Once you get your software RAID set up, let us know how much it improves performance over a single drive. I'd be interested to know. However, as you may already know, RAID0 arrays are inherently more susceptible to failure than single drives. So make sure you have all important files backed up before you make the plunge. That is why I only put the OS on my RAID0 array. All my data are on my enterprise-class TB drives.

---

### Post by darkod on 2009-12-12
Well, this is only regular home desktop, I'm doing this mostly from enthusiast point of view. Of course I know not to expect failure protection from raid0 because there is no redundancy. In fact, I read on plenty websites that raid0 is more susceptible to failure and I really don't get the point. Yes, you have two drives and if only one goes, everything is gone. But that doesn't mean the chances are really that much bigger for failure. This is only a home desktop, of course I would never use raid0 for a server, and not software raid. :)
I did more reading meanwhile and it seems you need to create same size partitions on both drives for any separate partition you want, for example /, /home and swap. Then you just create raid0 device for all of them. I thought you are creating identical partitions on both drives, combining them in raid0, and after it shows as single device you create partitions on it for /, /home and swap just as on single drive. I'll play with both setups.
And how can I measure performance in ubuntu? I was googling for it but didn't find anything except some "hdparm" command. Is that it?
In win7 with HD Tune my single Seagate 250GB, 7200rpm, 16MB showed 75MB/s average with 64kb test.
I still don't know if I could use win7 with software raid0 on the same drives because they would need to be dynamic for that, and I have never tried to set up linux on dynamic drives before.
A lot to test... :)

---

### Post by Ginsu543 on 2009-12-12
Yes, for a quick test I use "sudo hdparm -Tt /dev/sdX" command. For another, I have HardInfo installed (you can find it in Synaptic). Besides giving a lot of hardware information, it also has several tests for cpu performance. Good luck! :)

---

### Post by gilson585 on 2009-12-20
If you need help getting fakeraid to work look at my post [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445) as for the drives needing to be dynamic instead of basic, idk if that will work, u may need to invest in a cheap raid controller

---

