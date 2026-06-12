---
title: "one step from giving up on ubuntu"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by aboufady on 2006-09-11
i have no tolerance for such things and its getting on my nerves ive installed ubuntu for the second time and after a while give me the same mess up for which ive installed the ubuntu for the second time and unless i get a reason or solution for it i will not bother installing ubuntu for the 3rd time i boot up ubuntu and i get this damn message and it wont continue after it "waiting for root file system" answer me or dont i dont care

---

### Post by raldz on 2006-09-11
This could be a case of bad partition table.. this happened to me when I use GPARTED LiveCD to increase the space for my installed Ubuntu.. the partition table was damaged (or i messed up) so the system could not mount the swap partition properly which made my system soo slow.. in your case it seems that it could not mount the root properly.. just my thought..

---

### Post by wieman01 on 2006-09-11
If you don't mind wipe out your entire HD (format it) and do a fresh install. That should do.

---

### Post by jsimmons on 2006-09-11
> **wieman01 said:**
> If you don't mind wipe out your entire HD (format it) and do a fresh install. That should do.

It seems that Linux acts more like Windows every day...

---

### Post by tsiMental on 2006-09-11
It seems to me that you need to reconsider your reasons for installing ubuntu. This kind of anger will get you nowhere.

Though, I think this is a problem with your partitioning. Use an entirely separate diskdrive for ubuntu. Don't install ubuntu on the same drive as you installed Windows on, and use the default partitioning during the installation of ubuntu. And - don't repartition or resize your partitions (on that drive) using partition magic or gparted or whatever after you've got a successful installation.

AND install grub in the MBR (Master Boot Record) of your primary master IDE drive. (This should be done by default by the ubuntu installer).

Hope you'll find your way...

---

### Post by wieman01 on 2006-09-11
> **jsimmons said:**
> It seems that Linux acts more like Windows every day...

Well, it does from time to time. It's not perfect. :-)

---

### Post by bigken on 2006-09-11
If you are resizing your hdd and it has windows xp you must defrag that drive before you downsize it to allow room for ubuntu then when you install the os let it use the unused free space I have win xp edgy eft dapper suse 10.2 and freespire all on 1 80gig hdd :wink:

---

