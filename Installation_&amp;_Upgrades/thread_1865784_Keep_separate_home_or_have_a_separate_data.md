---
title: "Keep separate /home or have a separate /data?"
date: 2011-10-20
forum: Installation &amp; Upgrades
---

### Post by akand074 on 2011-10-20
I'm going to do a clean install of Oneiric within a few days on my desktop currently still running Natty. Currently I have the filesystem (/) installed on my 60GB SSD and my home folder (/home) installed on my 1TB HDD. I was just wondering if it would be better to have everything installed on my SSD and then make a separate mount point "/data" on my HDD to hold my data. Basically I was just thinking it'd be a cleaner this way and have everything related to the OS on my SSD. /home does start to get messy as old folders stay between new installs.

Would one recommend one or the other for my situation? Or does it really make no difference? Also, wouldn't /data then be owned by root by default and I'd have to change that? I only have one Ubuntu install and one user on my desktop at all times.

---

### Post by nothingspecial on 2011-10-20
Well I use a seperate data partition but I dual boot.

Then I have a Music, Videos etc on the data partition and use fstab to put them in my /home like so

```
LABEL=Data  /media/data  ext4  defaults  0  0
/media/data/bin  /home/ns/bin  none  bind  0  0
/media/data/Documents  /home/ns/Documents  none  bind  0  0
/media/data/Downloads  /home/ns/Downloads  none  bind  0  0
/media/data/images  /home/ns/images  none  bind  0  0
/media/data/mail  /home/ns/mail  none  bind  0  0
/media/data/Music  /home/ns/Music  none  bind  0  0
/media/data/Pictures  /home/ns/Pictures  none  bind  0  0
/media/data/source  /home/ns/source  none  bind  0  0
/media/data/Videos  /home/ns/Videos  none  bind  0  0
```

But it is personal preference really.

---

### Post by irv on 2011-10-20
Here of late I have been getting tired of moving files/backing up so I just keep everything in the clouds. This way I can get to all my stuff from anywhere and that includes a new fresh install. Of course you still need a home to have all your setting but I just keep the default home and let the new install put my setting there.
I do have a dual boot with Win7, and I can get to windows data from Linux because I never touch that partition when installing a new OS.
Just my thoughts.

---

### Post by malspa on 2011-10-20
Does seem like it'd be cleaner, in your situation.

I personally use a separate /home partition as well as a couple of separate partitions for my data. But different people have differing opinions about the need/usefulness of a separate /home partition.

---

### Post by oldfred on 2011-10-21
I prefer the separate /data, but there can be issues when dual booting with UIDs & GIDS. But if only one system or all Ubuntu then that is not an issue.

I just installed a SSD and I keep /home in the / (root ) partition. But my /home is just settings. All data including some of the hidden files & folders that have data have been moved. My /home is now about 1GB with 3/4 of that .wine as that is not so easy to move.
I primarily mount it (somewhat hidden) in /mnt/data and link folders back into /home. I use the profile.ini to relocate my Filefox & Thunderbird locations so I can share with XP & other Ubuntus.

---

### Post by akand074 on 2011-10-21
> **nothingspecial said:**
> Well I use a seperate data partition but I dual boot.

Then I have a Music, Videos etc on the data partition and use fstab to put them in my /home like so

```
LABEL=Data  /media/data  ext4  defaults  0  0
/media/data/bin  /home/ns/bin  none  bind  0  0
/media/data/Documents  /home/ns/Documents  none  bind  0  0
/media/data/Downloads  /home/ns/Downloads  none  bind  0  0
/media/data/images  /home/ns/images  none  bind  0  0
/media/data/mail  /home/ns/mail  none  bind  0  0
/media/data/Music  /home/ns/Music  none  bind  0  0
/media/data/Pictures  /home/ns/Pictures  none  bind  0  0
/media/data/source  /home/ns/source  none  bind  0  0
/media/data/Videos  /home/ns/Videos  none  bind  0  0
```But it is personal preference really.

I actually love this idea. Does this make it so that the folders are seem like they are seamlessly within my home folder even though they are on a separate drive? 

Did you make a new partition (or separate drive) mounted at /media/data? and then edited fstab? Also in a new fresh install, say when 12.04 is released. If I do a clean install again, I'd just do the same thing, put the same drives/partitions to / and /media/data and then redo the fstab?

---

