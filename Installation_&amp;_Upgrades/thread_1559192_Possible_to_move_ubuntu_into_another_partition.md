---
title: "Possible to move ubuntu into another partition?"
date: 2010-08-23
forum: Installation &amp; Upgrades
---

### Post by michael.the.bone on 2010-08-23
I first installed Ubuntu onto my windows hard drive, but then realised there wasnt enough space when i started to use it.

I partitioned my hard drive, but now i have to keep mounting it etc, also i think my o.s is running slower than it should because it has to run off the windows side (which i have decreased to lowest possible as i have fully switched to ubuntu).

Is it now possible to move the original root over to my new partition? Or would i need a full new installation? 

Is there a way to access my ubuntu files from windows? I cant find the partitioned side of the hard drive when i log in windows...

Cheers

---

### Post by kansasnoob on 2010-08-23
In order to get an idea of your layout please post the output from terminal of:

```
sudo fdisk -l
```

and:

```
df -H
```

---

### Post by michael.the.bone on 2010-08-23
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x998d027b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23878   191799011    7  HPFS/NTFS
/dev/sda2           23879       29485    45031709    7  HPFS/NTFS
/dev/sda3           29485       30402     7366656   17  Hidden HPFS/NTFS


michael@ubuntu:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/loop0              18G    11G   6.2G  63% /
none                   940M   291k   940M   1% /dev
none                   945M   2.4M   943M   1% /dev/shm
none                   945M   209k   945M   1% /var/run
none                   945M      0   945M   0% /var/lock
none                   945M      0   945M   0% /lib/init/rw
/dev/sda2               47G    45G   2.1G  96% /host
/dev/sda1              197G    15G   183G   8% /media/System
michael@ubuntu:~$

---

### Post by kansasnoob on 2010-08-24
Sorry to take so long, things have been crazy.

That aside, it appears this may be a Wubi install. Is that correct?

---

### Post by kansasnoob on 2010-08-24
Actually, since that shows three NTFS partitions it would be best to just see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Note: There are different instructions here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

If this is a Wubi install there is a method to move the Wubi install to a partition:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

Personally I don't recommend that procedure. I particularly worry about your windows boot files being spread over 2 or more partitions!

---

### Post by bcbc on 2010-08-25
> **kansasnoob said:**
> Actually, since that shows three NTFS partitions it would be best to just see the output of the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Note: There are different instructions here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

If this is a Wubi install there is a method to move the Wubi install to a partition:

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

Personally I don't recommend that procedure. I particularly worry about your windows boot files being spread over 2 or more partitions!

+1 on not using the migration from the wubi guide. It is out of date and does not work. You can follow this howto to migrate: [url]http://ubuntuforums.org/showthread.php?t=1519354[/url

It's possible to move a wubi install to a new partition, but you'll still have to resize the root.disk. I think it's simpler to just migrate.

---

### Post by michael.the.bone on 2010-08-26
No worries...

Cool, im going to try the Ubuntu forum guide one - not sure if i am wubi? But i presume i am if you think its says it...

Cheers.

---

### Post by spookiedoom on 2011-03-08
okay i have a really tough question:

i have a dual partitioned hard drive- it used to have windows and ubuntu 10.04 lucid lynx. windows all out failed so i wanted to repartition the hard drive to allow a 75/25 split between ubuntu and ubuntu for netbook - (since i use this computer for my NGO & personal use i want to keep the two separate) instead of the 50/50 split it had.

:asked the boyfriend for assistance in converting the hard drive:

he installed gparted - and deleted the windows boot. then discovered that he couldnt accually relocate space with out it creating a new 3rd partition.  he restarted the computer and now we obviously cant access the space that was once windows.. so theres 30gib thats in a black hole of "wtf do i do now"?

any ideas? becuase all i can think of is burning everything to a cd and completely starting over.

sincerely, newbuntu user

---

### Post by bcbc on 2011-03-08
spookiedom, I recommend starting a new thread... this one's old.

You can probably recover the windows partition if your bf just deleted it using [testdisk]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"). But you can also probably boot a live CD and repair things too without reinstalling everything.

However, I would suggest starting a new thread and post the results of the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") there so we have a clearer picture of what's going on.

---

